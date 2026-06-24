# Document Service

## Objetivo

Generar, almacenar, versionar y servir documentos, reportes PDF, evidencias y soportes asociados a horarios.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de documentos y reportes con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No define reglas academicas; conserva artefactos documentales generados por procesos del sistema.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Generar PDF de horario | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| cargar evidencia | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| versionar reporte | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| emitir URL firmada | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| archivar documento | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| Document | Gestionado por el servicio segun el limite de negocio definido. |
| DocumentVersion | Gestionado por el servicio segun el limite de negocio definido. |
| PdfReport | Gestionado por el servicio segun el limite de negocio definido. |
| Evidence | Gestionado por el servicio segun el limite de negocio definido. |
| StorageObject | Gestionado por el servicio segun el limite de negocio definido. |
| SignatureRecord | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| DocumentRequest | Gestionado por el servicio segun el limite de negocio definido. |
| DocumentResponse | Gestionado por el servicio segun el limite de negocio definido. |
| ReportRequest | Gestionado por el servicio segun el limite de negocio definido. |
| EvidenceResponse | Gestionado por el servicio segun el limite de negocio definido. |
| SignedUrlResponse | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| DOCUMENT_READ | Gestionado por el servicio segun el limite de negocio definido. |
| DOCUMENT_WRITE | Gestionado por el servicio segun el limite de negocio definido. |
| REPORT_GENERATE | Gestionado por el servicio segun el limite de negocio definido. |
| EVIDENCE_ATTACH | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Documentos y reportes]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| scheduling-service | REST y eventos | Integracion necesaria para completar reglas de documentos y reportes. |
| iam-service | REST y eventos | Integracion necesaria para completar reglas de documentos y reportes. |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de documentos y reportes. |

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


