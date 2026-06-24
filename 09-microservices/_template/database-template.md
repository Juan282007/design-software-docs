# Base de Datos

## Estrategia

Cada microservicio posee base PostgreSQL independiente, migraciones Flyway, auditoria tecnica y control optimista.

## Tablas

| Tabla | Proposito |
| --- | --- |
| aggregate | Agregado principal del servicio. |
| outbox_event | Eventos por publicar. |
| inbox_event | Eventos procesados para idempotencia. |


