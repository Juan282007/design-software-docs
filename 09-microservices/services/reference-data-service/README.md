# Reference Data Service

## Objetivo

Centralizar catalogos institucionales, estados, regionales, centros, jornadas, modalidades y parametros transversales.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de datos maestros con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No ejecuta procesos academicos; entrega datos maestros versionados para validacion y seleccion.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Consulta de catalogos | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| administracion de estados | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| gestion de centros | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| activacion de parametros | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| sincronizacion de datos maestros | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| Catalog | Gestionado por el servicio segun el limite de negocio definido. |
| CatalogItem | Gestionado por el servicio segun el limite de negocio definido. |
| Status | Gestionado por el servicio segun el limite de negocio definido. |
| City | Gestionado por el servicio segun el limite de negocio definido. |
| Regional | Gestionado por el servicio segun el limite de negocio definido. |
| Center | Gestionado por el servicio segun el limite de negocio definido. |
| Modality | Gestionado por el servicio segun el limite de negocio definido. |
| Shift | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| CatalogRequest | Gestionado por el servicio segun el limite de negocio definido. |
| CatalogResponse | Gestionado por el servicio segun el limite de negocio definido. |
| CatalogItemRequest | Gestionado por el servicio segun el limite de negocio definido. |
| StatusResponse | Gestionado por el servicio segun el limite de negocio definido. |
| CenterResponse | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| REFERENCE_READ | Gestionado por el servicio segun el limite de negocio definido. |
| REFERENCE_WRITE | Gestionado por el servicio segun el limite de negocio definido. |
| REFERENCE_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Datos maestros]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| iam-service | REST y eventos | Integracion necesaria para completar reglas de datos maestros. |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de datos maestros. |

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


