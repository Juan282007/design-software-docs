# Training Environment Service

## Objetivo

Administrar ambientes, sedes, edificios, recursos, capacidad, disponibilidad y ventanas de mantenimiento.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de ambientes de formacion con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No decide asignaciones academicas; informa restricciones y disponibilidad fisica al servicio de horarios.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Registro de ambientes | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| validacion de capacidad | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| bloqueo por mantenimiento | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| consulta de disponibilidad | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| inventario de recursos | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| Environment | Gestionado por el servicio segun el limite de negocio definido. |
| Building | Gestionado por el servicio segun el limite de negocio definido. |
| Campus | Gestionado por el servicio segun el limite de negocio definido. |
| Resource | Gestionado por el servicio segun el limite de negocio definido. |
| EnvironmentAvailability | Gestionado por el servicio segun el limite de negocio definido. |
| MaintenanceWindow | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| EnvironmentRequest | Gestionado por el servicio segun el limite de negocio definido. |
| EnvironmentResponse | Gestionado por el servicio segun el limite de negocio definido. |
| ResourceRequest | Gestionado por el servicio segun el limite de negocio definido. |
| AvailabilityResponse | Gestionado por el servicio segun el limite de negocio definido. |
| MaintenanceRequest | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| ENVIRONMENT_READ | Gestionado por el servicio segun el limite de negocio definido. |
| ENVIRONMENT_WRITE | Gestionado por el servicio segun el limite de negocio definido. |
| ENVIRONMENT_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Ambientes de formacion]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| reference-data-service | REST y eventos | Integracion necesaria para completar reglas de ambientes de formacion. |
| scheduling-service | REST y eventos | Integracion necesaria para completar reglas de ambientes de formacion. |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de ambientes de formacion. |

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


