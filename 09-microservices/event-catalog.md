# Catalogo Centralizado de Eventos

## Eventos publicados y consumidos

| Evento | Servicio | Tipo | Dominio | Uso |
| --- | --- | --- | --- | --- |
| UserCreated | iam-service | Publicado | Identidad y acceso | Consumidores segun necesidad de consistencia eventual. |
| UserUpdated | iam-service | Publicado | Identidad y acceso | Consumidores segun necesidad de consistencia eventual. |
| UserDeactivated | iam-service | Publicado | Identidad y acceso | Consumidores segun necesidad de consistencia eventual. |
| RoleAssigned | iam-service | Publicado | Identidad y acceso | Consumidores segun necesidad de consistencia eventual. |
| PermissionChanged | iam-service | Publicado | Identidad y acceso | Consumidores segun necesidad de consistencia eventual. |
| SessionRevoked | iam-service | Publicado | Identidad y acceso | Consumidores segun necesidad de consistencia eventual. |
| AuditPolicyChanged | iam-service | Consumido | Identidad y acceso | Actualiza proyeccion, cache o validacion local. |
| CatalogItemCreated | reference-data-service | Publicado | Datos maestros | Consumidores segun necesidad de consistencia eventual. |
| CatalogItemUpdated | reference-data-service | Publicado | Datos maestros | Consumidores segun necesidad de consistencia eventual. |
| CatalogItemDisabled | reference-data-service | Publicado | Datos maestros | Consumidores segun necesidad de consistencia eventual. |
| StatusChanged | reference-data-service | Publicado | Datos maestros | Consumidores segun necesidad de consistencia eventual. |
| UserCreated | reference-data-service | Consumido | Datos maestros | Actualiza proyeccion, cache o validacion local. |
| TrainingProgramCreated | academic-management-service | Publicado | Gestion academica | Consumidores segun necesidad de consistencia eventual. |
| TrainingRecordCreated | academic-management-service | Publicado | Gestion academica | Consumidores segun necesidad de consistencia eventual. |
| TrainingRecordUpdated | academic-management-service | Publicado | Gestion academica | Consumidores segun necesidad de consistencia eventual. |
| ApprenticeEnrolled | academic-management-service | Publicado | Gestion academica | Consumidores segun necesidad de consistencia eventual. |
| ApprenticeWithdrawn | academic-management-service | Publicado | Gestion academica | Consumidores segun necesidad de consistencia eventual. |
| CatalogItemUpdated | academic-management-service | Consumido | Gestion academica | Actualiza proyeccion, cache o validacion local. |
| CenterChanged | academic-management-service | Consumido | Gestion academica | Actualiza proyeccion, cache o validacion local. |
| UserDeactivated | academic-management-service | Consumido | Gestion academica | Actualiza proyeccion, cache o validacion local. |
| EnvironmentCreated | training-environment-service | Publicado | Ambientes de formacion | Consumidores segun necesidad de consistencia eventual. |
| EnvironmentUpdated | training-environment-service | Publicado | Ambientes de formacion | Consumidores segun necesidad de consistencia eventual. |
| EnvironmentDisabled | training-environment-service | Publicado | Ambientes de formacion | Consumidores segun necesidad de consistencia eventual. |
| EnvironmentAvailabilityChanged | training-environment-service | Publicado | Ambientes de formacion | Consumidores segun necesidad de consistencia eventual. |
| MaintenanceWindowRegistered | training-environment-service | Publicado | Ambientes de formacion | Consumidores segun necesidad de consistencia eventual. |
| CatalogItemUpdated | training-environment-service | Consumido | Ambientes de formacion | Actualiza proyeccion, cache o validacion local. |
| ScheduleCancelled | training-environment-service | Consumido | Ambientes de formacion | Actualiza proyeccion, cache o validacion local. |
| ScheduleCreated | training-environment-service | Consumido | Ambientes de formacion | Actualiza proyeccion, cache o validacion local. |
| ScheduleCreated | scheduling-service | Publicado | Programacion de horarios | Consumidores segun necesidad de consistencia eventual. |
| ScheduleUpdated | scheduling-service | Publicado | Programacion de horarios | Consumidores segun necesidad de consistencia eventual. |
| ScheduleApproved | scheduling-service | Publicado | Programacion de horarios | Consumidores segun necesidad de consistencia eventual. |
| ScheduleCancelled | scheduling-service | Publicado | Programacion de horarios | Consumidores segun necesidad de consistencia eventual. |
| ScheduleConflictDetected | scheduling-service | Publicado | Programacion de horarios | Consumidores segun necesidad de consistencia eventual. |
| EnvironmentReserved | scheduling-service | Publicado | Programacion de horarios | Consumidores segun necesidad de consistencia eventual. |
| InstructorAssigned | scheduling-service | Publicado | Programacion de horarios | Consumidores segun necesidad de consistencia eventual. |
| TrainingRecordCreated | scheduling-service | Consumido | Programacion de horarios | Actualiza proyeccion, cache o validacion local. |
| InstructorAvailabilityChanged | scheduling-service | Consumido | Programacion de horarios | Actualiza proyeccion, cache o validacion local. |
| EnvironmentAvailabilityChanged | scheduling-service | Consumido | Programacion de horarios | Actualiza proyeccion, cache o validacion local. |
| CatalogItemUpdated | scheduling-service | Consumido | Programacion de horarios | Actualiza proyeccion, cache o validacion local. |
| InstructorCreated | actors-service | Publicado | Actores academicos | Consumidores segun necesidad de consistencia eventual. |
| InstructorUpdated | actors-service | Publicado | Actores academicos | Consumidores segun necesidad de consistencia eventual. |
| InstructorDeactivated | actors-service | Publicado | Actores academicos | Consumidores segun necesidad de consistencia eventual. |
| InstructorAvailabilityChanged | actors-service | Publicado | Actores academicos | Consumidores segun necesidad de consistencia eventual. |
| SpecialtyAssigned | actors-service | Publicado | Actores academicos | Consumidores segun necesidad de consistencia eventual. |
| UserCreated | actors-service | Consumido | Actores academicos | Actualiza proyeccion, cache o validacion local. |
| UserDeactivated | actors-service | Consumido | Actores academicos | Actualiza proyeccion, cache o validacion local. |
| CatalogItemUpdated | actors-service | Consumido | Actores academicos | Actualiza proyeccion, cache o validacion local. |
| DocumentStored | document-service | Publicado | Documentos y reportes | Consumidores segun necesidad de consistencia eventual. |
| DocumentVersioned | document-service | Publicado | Documentos y reportes | Consumidores segun necesidad de consistencia eventual. |
| ReportGenerated | document-service | Publicado | Documentos y reportes | Consumidores segun necesidad de consistencia eventual. |
| EvidenceAttached | document-service | Publicado | Documentos y reportes | Consumidores segun necesidad de consistencia eventual. |
| DocumentArchived | document-service | Publicado | Documentos y reportes | Consumidores segun necesidad de consistencia eventual. |
| ScheduleApproved | document-service | Consumido | Documentos y reportes | Actualiza proyeccion, cache o validacion local. |
| ScheduleUpdated | document-service | Consumido | Documentos y reportes | Actualiza proyeccion, cache o validacion local. |
| ScheduleCancelled | document-service | Consumido | Documentos y reportes | Actualiza proyeccion, cache o validacion local. |
| UserDeactivated | document-service | Consumido | Documentos y reportes | Actualiza proyeccion, cache o validacion local. |
| ServiceHealthChanged | monitoring-service | Publicado | Observabilidad operativa | Consumidores segun necesidad de consistencia eventual. |
| AlertTriggered | monitoring-service | Publicado | Observabilidad operativa | Consumidores segun necesidad de consistencia eventual. |
| IncidentSignalRaised | monitoring-service | Publicado | Observabilidad operativa | Consumidores segun necesidad de consistencia eventual. |
| MetricThresholdExceeded | monitoring-service | Publicado | Observabilidad operativa | Consumidores segun necesidad de consistencia eventual. |
| ScheduleConflictDetected | monitoring-service | Consumido | Observabilidad operativa | Actualiza proyeccion, cache o validacion local. |
| DocumentStored | monitoring-service | Consumido | Observabilidad operativa | Actualiza proyeccion, cache o validacion local. |
| UserCreated | monitoring-service | Consumido | Observabilidad operativa | Actualiza proyeccion, cache o validacion local. |
| ServiceHealthChanged | monitoring-service | Consumido | Observabilidad operativa | Actualiza proyeccion, cache o validacion local. |
| AuditLogRecorded | audit-service | Publicado | Auditoria y trazabilidad | Consumidores segun necesidad de consistencia eventual. |
| AuditPolicyChanged | audit-service | Publicado | Auditoria y trazabilidad | Consumidores segun necesidad de consistencia eventual. |
| IntegrityCheckFailed | audit-service | Publicado | Auditoria y trazabilidad | Consumidores segun necesidad de consistencia eventual. |
| AccessAnomalyDetected | audit-service | Publicado | Auditoria y trazabilidad | Consumidores segun necesidad de consistencia eventual. |
| UserCreated | audit-service | Consumido | Auditoria y trazabilidad | Actualiza proyeccion, cache o validacion local. |
| RoleAssigned | audit-service | Consumido | Auditoria y trazabilidad | Actualiza proyeccion, cache o validacion local. |
| ScheduleApproved | audit-service | Consumido | Auditoria y trazabilidad | Actualiza proyeccion, cache o validacion local. |
| DocumentStored | audit-service | Consumido | Auditoria y trazabilidad | Actualiza proyeccion, cache o validacion local. |
| EnvironmentUpdated | audit-service | Consumido | Auditoria y trazabilidad | Actualiza proyeccion, cache o validacion local. |
| InstructorUpdated | audit-service | Consumido | Auditoria y trazabilidad | Actualiza proyeccion, cache o validacion local. |
| TrainingRecordUpdated | audit-service | Consumido | Auditoria y trazabilidad | Actualiza proyeccion, cache o validacion local. |

## Convenciones

| Campo | Regla |
| --- | --- |
| eventId | UUID global unico. |
| eventVersion | Version numerica para evolucion compatible. |
| occurredAt | Fecha UTC ISO 8601. |
| source | Nombre tecnico del microservicio emisor. |
| correlationId | Identificador comun de la transaccion distribuida. |
| aggregateId | Identificador del agregado de dominio. |
| data | Objeto JSON validado por esquema del evento. |


