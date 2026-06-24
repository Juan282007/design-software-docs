# Dependencias - Audit Service

## Dependencias entrantes y salientes

| Servicio relacionado | Direccion | Mecanismo | Contrato |
| --- | --- | --- | --- |
| iam-service | Saliente | REST sincronico y eventos asincronos | Consulta validada, evento de dominio o auditoria. |
| monitoring-service | Saliente | REST sincronico y eventos asincronos | Consulta validada, evento de dominio o auditoria. |

## Resiliencia

| Mecanismo | Configuracion recomendada |
| --- | --- |
| Circuit breaker | Abrir circuito con 50% de fallos en ventana movil de 20 llamadas. |
| Timeout | 2 segundos para consultas internas y 5 segundos para operaciones documentales. |
| Retry | 3 intentos maximos solo para errores 408, 429, 502, 503 y 504. |
| Bulkhead | Pool separado para integraciones criticas y generacion documental. |
| Cache | TTL de 5 minutos para catalogos y perfiles consultados frecuentemente. |

## Observabilidad

- Propagar X-Correlation-Id desde API Gateway hasta eventos.
- Exponer metricas Micrometer para latencia, errores, volumen y consumidores.
- Registrar logs estructurados sin datos sensibles.
- Publicar salud tecnica y salud funcional.

## Diagrama de dependencias

~~~mermaid
flowchart LR
    S[Audit Service] --> DB[PostgreSQL sena_audit]
    S --> iam_service[iam-service]
    S --> monitoring_service[monitoring-service]
    S --> Broker[Broker de eventos]
    S --> Obs[Monitoring Service]
~~~


