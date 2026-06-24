# Eventos - Academic Management Service

## Eventos publicados

| Evento | Disparador | Payload minimo |
| --- | --- | --- |
| TrainingProgramCreated | Cambio confirmado en gestion academica. | eventId, occurredAt, actorId, aggregateId, aggregateType, version, data. |
| TrainingRecordCreated | Cambio confirmado en gestion academica. | eventId, occurredAt, actorId, aggregateId, aggregateType, version, data. |
| TrainingRecordUpdated | Cambio confirmado en gestion academica. | eventId, occurredAt, actorId, aggregateId, aggregateType, version, data. |
| ApprenticeEnrolled | Cambio confirmado en gestion academica. | eventId, occurredAt, actorId, aggregateId, aggregateType, version, data. |
| ApprenticeWithdrawn | Cambio confirmado en gestion academica. | eventId, occurredAt, actorId, aggregateId, aggregateType, version, data. |

## Eventos consumidos

| Evento | Origen esperado | Efecto local |
| --- | --- | --- |
| CatalogItemUpdated | Servicio propietario del agregado | Actualiza proyeccion local, invalida cache o dispara validacion. |
| CenterChanged | Servicio propietario del agregado | Actualiza proyeccion local, invalida cache o dispara validacion. |
| UserDeactivated | Servicio propietario del agregado | Actualiza proyeccion local, invalida cache o dispara validacion. |

## Esquema comun

~~~json
{
  "eventId": "uuid",
  "eventType": "ScheduleApproved",
  "eventVersion": 1,
  "occurredAt": "2026-06-24T10:15:30Z",
  "source": "academic-management-service",
  "correlationId": "uuid",
  "causationId": "uuid",
  "actorId": "uuid",
  "aggregateId": "uuid",
  "aggregateType": "Gestion academica",
  "data": {}
}
~~~

## Flujo de mensajeria

~~~mermaid
flowchart TD
    A[Transaccion de negocio] --> B[Guardar outbox_event]
    B --> C[Commit PostgreSQL]
    C --> D[Publicador lee outbox]
    D --> E[Broker de eventos]
    E --> F[Consumidor idempotente]
    F --> G[Registrar inbox_event]
    G --> H[Actualizar proyeccion local]
~~~

## Reglas de consumo

- Rechazar eventos sin eventId, eventType, occurredAt o aggregateId.
- Procesar una sola vez por eventId.
- Reintentar errores transitorios con backoff exponencial.
- Enviar a cola de errores cuando se agote el numero de reintentos.
- Mantener compatibilidad hacia atras por version de evento.


