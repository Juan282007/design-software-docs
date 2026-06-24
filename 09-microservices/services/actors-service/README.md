# Actors Service

## Objetivo

Gestionar perfiles academicos de instructores, coordinadores, especialidades, disponibilidad y vinculacion institucional.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de actores academicos con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No autentica usuarios ni genera horarios; mantiene datos operativos de actores requeridos por la programacion.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Crear instructor | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| asignar especialidad | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| registrar disponibilidad | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| consultar carga academica | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| desactivar actor | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| Instructor | Gestionado por el servicio segun el limite de negocio definido. |
| InstructorProfile | Gestionado por el servicio segun el limite de negocio definido. |
| Specialty | Gestionado por el servicio segun el limite de negocio definido. |
| Availability | Gestionado por el servicio segun el limite de negocio definido. |
| Contract | Gestionado por el servicio segun el limite de negocio definido. |
| Coordinator | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| InstructorRequest | Gestionado por el servicio segun el limite de negocio definido. |
| InstructorResponse | Gestionado por el servicio segun el limite de negocio definido. |
| AvailabilityRequest | Gestionado por el servicio segun el limite de negocio definido. |
| SpecialtyResponse | Gestionado por el servicio segun el limite de negocio definido. |
| CoordinatorResponse | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| ACTOR_READ | Gestionado por el servicio segun el limite de negocio definido. |
| ACTOR_WRITE | Gestionado por el servicio segun el limite de negocio definido. |
| INSTRUCTOR_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |
| AVAILABILITY_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Actores academicos]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| iam-service | REST y eventos | Integracion necesaria para completar reglas de actores academicos. |
| reference-data-service | REST y eventos | Integracion necesaria para completar reglas de actores academicos. |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de actores academicos. |

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


