# API REST - Actors Service

## Convenciones

- Version base: /api/v1/actors.
- Autenticacion: Authorization Bearer JWT.
- Formato de fecha: ISO 8601.
- Identificadores: UUID.
- Paginacion: page, size, sort.
- Trazabilidad: X-Correlation-Id.

## Endpoints REST

| Verbo HTTP | Ruta | Proposito | Permiso |
| --- | --- | --- | --- |
| GET | /api/v1/actors/instructors | Listar registros paginados con filtros por estado, centro y texto libre. | ACTOR_READ |
| POST | /api/v1/actors/instructors | Crear un registro validado por reglas de dominio. | ACTOR_WRITE |
| GET | /api/v1/actors/instructors/{id} | Consultar detalle por identificador UUID. | ACTOR_READ |
| PUT | /api/v1/actors/instructors/{id} | Actualizar datos editables preservando auditoria. | ACTOR_WRITE |
| PATCH | /api/v1/actors/instructors/{id}/status | Cambiar estado operativo con causal. | ACTOR_WRITE |
| GET | /api/v1/actors/availability | Consultar recurso secundario con filtros de negocio. | ACTOR_READ |
| POST | /api/v1/actors/availability | Registrar recurso secundario asociado. | ACTOR_WRITE |
| GET | /api/v1/actors/events | Consultar eventos emitidos por correlacion. | ACTOR_READ |
| GET | /api/v1/actors/health/business | Exponer salud funcional del dominio. | MONITORING_READ |

## Contratos de entrada y salida

| DTO | Campos principales |
| --- | --- |
| InstructorRequest | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| InstructorResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| AvailabilityRequest | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| SpecialtyResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| CoordinatorResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |

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
    participant S as Actors Service
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
