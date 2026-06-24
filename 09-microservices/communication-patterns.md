# Patrones de Comunicacion

## REST sincronico

| Uso | Reglas |
| --- | --- |
| Validaciones inmediatas | Consultar existencia, estado y disponibilidad antes de confirmar operaciones. |
| Operaciones CRUD | Exponer endpoints versionados bajo /api/v1. |
| Consultas de usuario | Responder con paginacion, filtros y ordenamiento. |

## Eventos asincronos

| Uso | Reglas |
| --- | --- |
| Propagacion de cambios | Publicar eventos despues del commit mediante outbox. |
| Proyecciones locales | Consumir eventos con idempotencia por eventId. |
| Auditoria | Registrar operaciones criticas sin bloquear el flujo principal cuando sea viable. |

## Mensajeria y resiliencia

| Mecanismo | Decision |
| --- | --- |
| Broker | Topicos por dominio y colas de error por servicio consumidor. |
| Circuit breaker | Aplicado a llamadas REST entre microservicios. |
| Retries | Solo para fallos transitorios con backoff exponencial. |
| Timeouts | Cortos para validaciones, extendidos para generacion documental. |
| Observabilidad | Trazas distribuidas, logs estructurados y metricas Micrometer. |

~~~mermaid
flowchart LR
    Client[Frontend] --> Gateway[API Gateway]
    Gateway --> ServiceA[Microservicio A]
    ServiceA --> ServiceB[REST interno]
    ServiceA --> Outbox[(Outbox)]
    Outbox --> Broker[Broker]
    Broker --> Consumer[Microservicio consumidor]
    Consumer --> Inbox[(Inbox)]
    ServiceA --> Metrics[Monitoring]
    ServiceA --> Audit[Audit]
~~~


