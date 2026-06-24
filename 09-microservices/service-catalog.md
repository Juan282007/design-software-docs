# Catalogo de Servicios

## Catalogo completo

| Servicio | Dominio | Objetivo | Ruta base | Base de datos | Responsable |
| --- | --- | --- | --- | --- | --- |
| iam-service | Identidad y acceso | Administrar autenticacion, autorizacion, sesiones JWT, roles y permisos del Sistema de Gestion de Horarios SENA. | /api/v1/iam | sena_iam | Seguridad |
| reference-data-service | Datos maestros | Centralizar catalogos institucionales, estados, regionales, centros, jornadas, modalidades y parametros transversales. | /api/v1/reference-data | sena_reference_data | Gobierno de datos |
| academic-management-service | Gestion academica | Gestionar programas de formacion, competencias, resultados de aprendizaje, fichas y matriculas de aprendices. | /api/v1/academic | sena_academic_management | Coordinacion academica |
| training-environment-service | Ambientes de formacion | Administrar ambientes, sedes, edificios, recursos, capacidad, disponibilidad y ventanas de mantenimiento. | /api/v1/training-environments | sena_training_environment | Infraestructura academica |
| scheduling-service | Programacion de horarios | Orquestar la creacion, validacion, aprobacion y publicacion de horarios academicos, evitando cruces de instructor, ficha y ambiente. | /api/v1/scheduling | sena_scheduling | Planeacion academica |
| actors-service | Actores academicos | Gestionar perfiles academicos de instructores, coordinadores, especialidades, disponibilidad y vinculacion institucional. | /api/v1/actors | sena_actors | Talento academico |
| document-service | Documentos y reportes | Generar, almacenar, versionar y servir documentos, reportes PDF, evidencias y soportes asociados a horarios. | /api/v1/documents | sena_documents | Gestion documental |
| monitoring-service | Observabilidad operativa | Centralizar salud tecnica, metricas, trazas, alertas y senales operativas de los microservicios. | /api/v1/monitoring | sena_monitoring | Operaciones TI |
| audit-service | Auditoria y trazabilidad | Registrar eventos criticos, cambios de datos, accesos sensibles, politicas de retencion e integridad probatoria. | /api/v1/audit | sena_audit | Cumplimiento |

## Clasificacion por criticidad

| Servicio | Criticidad | Justificacion |
| --- | --- | --- |
| scheduling-service | Alta | Coordina el proceso misional de programacion academica. |
| iam-service | Alta | Controla acceso, permisos y sesiones. |
| academic-management-service | Alta | Provee fichas, programas y aprendices usados por horarios. |
| training-environment-service | Alta | Evita cruces y sobreasignacion de ambientes. |
| actors-service | Alta | Valida instructores, coordinadores y disponibilidad. |
| document-service | Media | Genera reportes y evidencias requeridas para soporte operativo. |
| audit-service | Alta | Conserva trazabilidad institucional y evidencia de cambios. |
| reference-data-service | Media | Centraliza catalogos y estados transversales. |
| monitoring-service | Media | Habilita observabilidad, alertas y seguimiento tecnico. |



