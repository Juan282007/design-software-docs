# Scheduling Service

## Objetivo

Orquestar la creacion, validacion, aprobacion y publicacion de horarios academicos, evitando cruces de instructor, ficha y ambiente.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de programacion de horarios con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No administra identidad, inventario ni matriculas; coordina datos externos para producir programacion academica trazable.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Crear horario | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| validar conflictos | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| asignar instructor | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| reservar ambiente | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| aprobar horario | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| publicar calendario | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| cancelar bloque | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| Schedule | Gestionado por el servicio segun el limite de negocio definido. |
| ScheduleDetail | Gestionado por el servicio segun el limite de negocio definido. |
| Assignment | Gestionado por el servicio segun el limite de negocio definido. |
| Conflict | Gestionado por el servicio segun el limite de negocio definido. |
| Reservation | Gestionado por el servicio segun el limite de negocio definido. |
| ScheduleVersion | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| ScheduleRequest | Gestionado por el servicio segun el limite de negocio definido. |
| ScheduleResponse | Gestionado por el servicio segun el limite de negocio definido. |
| AssignmentRequest | Gestionado por el servicio segun el limite de negocio definido. |
| ConflictResponse | Gestionado por el servicio segun el limite de negocio definido. |
| CalendarViewResponse | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| SCHEDULE_READ | Gestionado por el servicio segun el limite de negocio definido. |
| SCHEDULE_WRITE | Gestionado por el servicio segun el limite de negocio definido. |
| SCHEDULE_APPROVE | Gestionado por el servicio segun el limite de negocio definido. |
| SCHEDULE_PUBLISH | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Programacion de horarios]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| academic-management-service | REST y eventos | Integracion necesaria para completar reglas de programacion de horarios. |
| actors-service | REST y eventos | Integracion necesaria para completar reglas de programacion de horarios. |
| training-environment-service | REST y eventos | Integracion necesaria para completar reglas de programacion de horarios. |
| reference-data-service | REST y eventos | Integracion necesaria para completar reglas de programacion de horarios. |
| document-service | REST y eventos | Integracion necesaria para completar reglas de programacion de horarios. |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de programacion de horarios. |

## Riesgos tecnicos

| Riesgo | Mitigacion |
| --- | --- |
| Inconsistencia entre servicios | Eventos idempotentes, outbox transaccional y conciliacion por correlacion. |
| Latencia en consultas distribuidas | Cache de lectura con expiracion corta y endpoints especificos por caso de uso. |
| Crecimiento de datos historicos | Particionamiento por fecha y politicas de retencion documentadas. |

## Consideraciones de escalabilidad

- Escalar horizontalmente instancias Spring Boot detras del API Gateway.
- Mantener conexiones PostgreSQL controladas con pool HikariCP.
- Separar consultas de alto volumen mediante indices compuestos y proyecciones.
- Procesar eventos con consumidores idempotentes y control de reintentos.


