# API REST - IAM Service

## Convenciones

- Version base: /api/v1/iam.
- Autenticacion: Authorization Bearer JWT.
- Formato de fecha: ISO 8601.
- Identificadores: UUID.
- Paginacion: page, size, sort.
- Trazabilidad: X-Correlation-Id.

## Endpoints REST

| Verbo HTTP | Ruta | Proposito | Permiso |
| --- | --- | --- | --- |
| GET | /api/v1/iam/users | Listar registros paginados con filtros por estado, centro y texto libre. | IAM_USER_READ |
| POST | /api/v1/iam/users | Crear un registro validado por reglas de dominio. | IAM_USER_WRITE |
| GET | /api/v1/iam/users/{id} | Consultar detalle por identificador UUID. | IAM_USER_READ |
| PUT | /api/v1/iam/users/{id} | Actualizar datos editables preservando auditoria. | IAM_USER_WRITE |
| PATCH | /api/v1/iam/users/{id}/status | Cambiar estado operativo con causal. | IAM_USER_WRITE |
| GET | /api/v1/iam/roles | Consultar recurso secundario con filtros de negocio. | IAM_USER_READ |
| POST | /api/v1/iam/roles | Registrar recurso secundario asociado. | IAM_USER_WRITE |
| GET | /api/v1/iam/events | Consultar eventos emitidos por correlacion. | IAM_USER_READ |
| GET | /api/v1/iam/health/business | Exponer salud funcional del dominio. | MONITORING_READ |

## Contratos de entrada y salida

| DTO | Campos principales |
| --- | --- |
| LoginRequest | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| TokenResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| UserRequest | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| UserResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| RoleRequest | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| PermissionResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |

## Codigos de respuesta

| Codigo | Uso |
| --- | --- |
| 200 | Consulta o actualizacion exitosa. |
| 201 | Recurso creado. |
| 204 | Cambio de estado aplicado sin cuerpo de respuesta. |
| 400 | Regla de validacion incumplida. |
| 401 | JWT ausente, expirado o invalido. |
| 403 | Permiso insuficiente. |
| 404 | Recurso inexistente o no visible para el usuario. |
| 409 | Conflicto de negocio o version optimista desactualizada. |
| 422 | Datos validos en sintaxis pero no aceptables por regla academica. |

## Reglas de validacion

| Regla | Aplicacion |
| --- | --- |
| Identidad obligatoria | Toda operacion requiere usuario autenticado y permisos del servicio. |
| Estado controlado | Los cambios de estado deben usar catalogos vigentes de reference-data-service. |
| Integridad referencial externa | Los identificadores recibidos se verifican mediante REST o replica de evento. |
| Auditoria | Operaciones de escritura envian evento de auditoria con antes, despues y actor. |
| Concurrencia | Actualizaciones usan campo version para bloqueo optimista. |

## Diagrama de secuencia

~~~mermaid
sequenceDiagram
    participant UI as Frontend
    participant GW as API Gateway
    participant S as IAM Service
    participant DB as PostgreSQL
    participant MQ as Broker de eventos
    UI->>GW: Solicitud REST con JWT
    GW->>S: Enruta con contexto de seguridad
    S->>S: Valida permisos y reglas
    S->>DB: Lee o persiste datos
    DB-->>S: Resultado transaccional
    S->>MQ: Publica evento de dominio
    S-->>GW: Respuesta JSON
    GW-->>UI: Codigo HTTP y payload
~~~
