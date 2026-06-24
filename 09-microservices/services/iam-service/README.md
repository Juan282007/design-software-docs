# IAM Service

## Objetivo

Administrar autenticacion, autorizacion, sesiones JWT, roles y permisos del Sistema de Gestion de Horarios SENA.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Gobierno del dominio | Mantener consistencia de identidad y acceso con reglas transaccionales propias. |
| API REST | Exponer operaciones versionadas bajo  con respuestas JSON y codigos HTTP semanticos. |
| Eventos | Publicar y consumir eventos de dominio con correlationId, causationId y version de esquema. |
| Seguridad | Validar JWT, permisos funcionales y trazabilidad de acciones sensibles. |
| Persistencia | Administrar su propia base PostgreSQL  sin compartir tablas con otros servicios. |

## Limites de negocio

No administra datos academicos, ambientes, documentos ni horarios; solo expone identidad, permisos y contexto autenticado.

## Casos de uso

| Caso de uso | Actor principal | Resultado |
| --- | --- | --- |
| Inicio de sesion JWT | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| renovacion de token | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| gestion de usuarios | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| asignacion de roles | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| revocacion de sesiones | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |
| consulta de permisos efectivos | Usuario autorizado del dominio | Cambio consistente, auditable y publicado cuando aplica. |

## Entidades del dominio

| Entidad | Proposito |
| --- | --- |
| User | Gestionado por el servicio segun el limite de negocio definido. |
| Role | Gestionado por el servicio segun el limite de negocio definido. |
| Permission | Gestionado por el servicio segun el limite de negocio definido. |
| Session | Gestionado por el servicio segun el limite de negocio definido. |
| RefreshToken | Gestionado por el servicio segun el limite de negocio definido. |
| LoginAttempt | Gestionado por el servicio segun el limite de negocio definido. |

## DTOs principales

| DTO | Uso |
| --- | --- |
| LoginRequest | Gestionado por el servicio segun el limite de negocio definido. |
| TokenResponse | Gestionado por el servicio segun el limite de negocio definido. |
| UserRequest | Gestionado por el servicio segun el limite de negocio definido. |
| UserResponse | Gestionado por el servicio segun el limite de negocio definido. |
| RoleRequest | Gestionado por el servicio segun el limite de negocio definido. |
| PermissionResponse | Gestionado por el servicio segun el limite de negocio definido. |

## Seguridad y permisos

| Permiso | Alcance |
| --- | --- |
| IAM_USER_READ | Gestionado por el servicio segun el limite de negocio definido. |
| IAM_USER_WRITE | Gestionado por el servicio segun el limite de negocio definido. |
| IAM_ROLE_ADMIN | Gestionado por el servicio segun el limite de negocio definido. |
| IAM_SESSION_REVOKE | Gestionado por el servicio segun el limite de negocio definido. |

## Flujo de negocio

~~~mermaid
flowchart LR
    A[Solicitud autenticada] --> B[Validar JWT y permisos]
    B --> C[Validar reglas de Identidad y acceso]
    C --> D[Persistir en PostgreSQL]
    D --> E[Publicar eventos]
    E --> F[Registrar auditoria]
    F --> G[Responder API]
~~~

## Dependencias

| Servicio | Tipo | Uso |
| --- | --- | --- |
| audit-service | REST y eventos | Integracion necesaria para completar reglas de identidad y acceso. |
| monitoring-service | REST y eventos | Integracion necesaria para completar reglas de identidad y acceso. |

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


