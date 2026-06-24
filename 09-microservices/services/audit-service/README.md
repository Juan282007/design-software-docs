# Audit Service

## Objetivo

Registrar eventos criticos, cambios de datos, accesos sensibles, politicas de retencion e integridad probatoria.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de auditoria y trazabilidad con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No ejecuta acciones de negocio; recibe evidencias de actividad y expone consulta controlada para trazabilidad.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Registrar auditoria | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| consultar bitacora | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| verificar integridad | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| aplicar retencion | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| detectar acceso anomalo | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| AuditLog | Gestionado por el servicio segun el limite de negocio definido. |
| AuditEvent | Gestionado por el servicio segun el limite de negocio definido. |
| ChangeRecord | Gestionado por el servicio segun el limite de negocio definido. |
| AccessRecord | Gestionado por el servicio segun el limite de negocio definido. |
| RetentionPolicy | Gestionado por el servicio segun el limite de negocio definido. |
| IntegrityHash | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| AuditLogResponse | Gestionado por el servicio segun el limite de negocio definido. |
| AuditQueryRequest | Gestionado por el servicio segun el limite de negocio definido. |
| ChangeRecordResponse | Gestionado por el servicio segun el limite de negocio definido. |
| RetentionPolicyRequest | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| AUDIT_READ | Gestionado por el servicio segun el limite de negocio definido. |
| AUDIT_EXPORT | Gestionado por el servicio segun el limite de negocio definido. |
| AUDIT_POLICY_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Auditoria y trazabilidad]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| iam-service | REST y eventos | Integracion necesaria para completar reglas de auditoria y trazabilidad. |
| monitoring-service | REST y eventos | Integracion necesaria para completar reglas de auditoria y trazabilidad. |

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


