# API REST - Document Service

## Convenciones

- Version base: /api/v1/documents.
- Autenticacion: Authorization Bearer JWT.
- Formato de fecha: ISO 8601.
- Identificadores: UUID.
- Paginacion: page, size, sort.
- Trazabilidad: X-Correlation-Id.

## Endpoints REST

| Verbo HTTP | Ruta | Proposito | Permiso |
| --- | --- | --- | --- |
| GET | /api/v1/documents/documents | Listar registros paginados con filtros por estado, centro y texto libre. | DOCUMENT_READ |
| POST | /api/v1/documents/documents | Crear un registro validado por reglas de dominio. | DOCUMENT_WRITE |
| GET | /api/v1/documents/documents/{id} | Consultar detalle por identificador UUID. | DOCUMENT_READ |
| PUT | /api/v1/documents/documents/{id} | Actualizar datos editables preservando auditoria. | DOCUMENT_WRITE |
| PATCH | /api/v1/documents/documents/{id}/status | Cambiar estado operativo con causal. | DOCUMENT_WRITE |
| GET | /api/v1/documents/reports | Consultar recurso secundario con filtros de negocio. | DOCUMENT_READ |
| POST | /api/v1/documents/reports | Registrar recurso secundario asociado. | DOCUMENT_WRITE |
| GET | /api/v1/documents/events | Consultar eventos emitidos por correlacion. | DOCUMENT_READ |
| GET | /api/v1/documents/health/business | Exponer salud funcional del dominio. | MONITORING_READ |

## Contratos de entrada y salida

| DTO | Campos principales |
| --- | --- |
| DocumentRequest | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| DocumentResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| ReportRequest | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| EvidenceResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |
| SignedUrlResponse | id, code, name, status, createdAt, updatedAt, version y campos especificos del dominio. |

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
    participant S as Document Service
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
