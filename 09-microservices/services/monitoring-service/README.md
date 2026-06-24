# Monitoring Service

## Objetivo

Centralizar salud tecnica, metricas, trazas, alertas y senales operativas de los microservicios.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de observabilidad operativa con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No reemplaza herramientas APM externas; normaliza indicadores funcionales y tecnicos para operacion academica.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Consultar salud | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| registrar metricas | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| disparar alerta | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| analizar dependencia | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| exponer tablero operativo | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| HealthSnapshot | Gestionado por el servicio segun el limite de negocio definido. |
| MetricSample | Gestionado por el servicio segun el limite de negocio definido. |
| TraceSummary | Gestionado por el servicio segun el limite de negocio definido. |
| AlertRule | Gestionado por el servicio segun el limite de negocio definido. |
| IncidentSignal | Gestionado por el servicio segun el limite de negocio definido. |
| ServiceDependency | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| HealthResponse | Gestionado por el servicio segun el limite de negocio definido. |
| MetricResponse | Gestionado por el servicio segun el limite de negocio definido. |
| AlertRuleRequest | Gestionado por el servicio segun el limite de negocio definido. |
| TraceResponse | Gestionado por el servicio segun el limite de negocio definido. |
| DependencyResponse | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| MONITORING_READ | Gestionado por el servicio segun el limite de negocio definido. |
| MONITORING_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |
| ALERT_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Observabilidad operativa]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| iam-service | REST y eventos | Integracion necesaria para completar reglas de observabilidad operativa. |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de observabilidad operativa. |

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


