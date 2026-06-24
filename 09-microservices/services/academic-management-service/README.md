# Academic Management Service

## Objetivo

Gestionar programas de formacion, competencias, resultados de aprendizaje, fichas y matriculas de aprendices.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de gestion academica con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No asigna horarios ni reserva ambientes; provee estructura academica validada para la programacion.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Registro de programas | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| apertura de fichas | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| matricula de aprendices | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| consulta de competencias | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| cierre academico de ficha | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| TrainingProgram | Gestionado por el servicio segun el limite de negocio definido. |
| Competency | Gestionado por el servicio segun el limite de negocio definido. |
| LearningOutcome | Gestionado por el servicio segun el limite de negocio definido. |
| TrainingRecord | Gestionado por el servicio segun el limite de negocio definido. |
| Apprentice | Gestionado por el servicio segun el limite de negocio definido. |
| Enrollment | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| TrainingProgramRequest | Gestionado por el servicio segun el limite de negocio definido. |
| TrainingProgramResponse | Gestionado por el servicio segun el limite de negocio definido. |
| TrainingRecordRequest | Gestionado por el servicio segun el limite de negocio definido. |
| ApprenticeResponse | Gestionado por el servicio segun el limite de negocio definido. |
| EnrollmentRequest | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| ACADEMIC_READ | Gestionado por el servicio segun el limite de negocio definido. |
| ACADEMIC_WRITE | Gestionado por el servicio segun el limite de negocio definido. |
| RECORD_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |
| APPRENTICE_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Gestion academica]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| reference-data-service | REST y eventos | Integracion necesaria para completar reglas de gestion academica. |
| actors-service | REST y eventos | Integracion necesaria para completar reglas de gestion academica. |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de gestion academica. |

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


