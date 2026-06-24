# Arquitectura de Microservicios

## Vista general

El Sistema de Gestion de Horarios SENA se organiza en 9 microservicios Spring Boot 3 con Java 17, PostgreSQL por servicio, autenticacion JWT y comunicacion combinada mediante REST sincronico y eventos asincronos. El microservicio principal es scheduling-service, responsable de coordinar la programacion academica sin asumir la propiedad de identidad, datos maestros, actores, ambientes, documentos u auditoria.

## Principios arquitectonicos

| Principio | Aplicacion |
| --- | --- |
| Autonomia de servicios | Cada microservicio posee base de datos logica, migraciones y despliegue independiente. |
| Bajo acoplamiento | Las consultas inmediatas usan REST y la propagacion de cambios usa eventos. |
| Seguridad centralizada | API Gateway valida JWT y cada servicio valida permisos funcionales. |
| Trazabilidad | Toda operacion critica publica auditoria y conserva correlationId. |
| Consistencia eventual | Los datos entre dominios se sincronizan mediante eventos idempotentes. |

## Mapa de servicios

~~~mermaid
flowchart TB
    GW[API Gateway] --> IAM[iam-service]
    GW --> REF[reference-data-service]
    GW --> ACADEMIC[academic-management-service]
    GW --> ENV[training-environment-service]
    GW --> SCHED[scheduling-service]
    GW --> ACTORS[actors-service]
    GW --> DOC[document-service]
    GW --> MON[monitoring-service]
    GW --> AUDIT[audit-service]
    SCHED --> ACADEMIC
    SCHED --> ACTORS
    SCHED --> ENV
    SCHED --> DOC
    IAM --> AUDIT
    REF --> AUDIT
    DOC --> AUDIT
    MON --> AUDIT
~~~

## Microservicios

| Servicio | Dominio | Responsabilidad principal |
| --- | --- | --- |
| iam-service | Identidad y acceso | Administrar autenticacion, autorizacion, sesiones JWT, roles y permisos del Sistema de Gestion de Horarios SENA. |
| reference-data-service | Datos maestros | Centralizar catalogos institucionales, estados, regionales, centros, jornadas, modalidades y parametros transversales. |
| academic-management-service | Gestion academica | Gestionar programas de formacion, competencias, resultados de aprendizaje, fichas y matriculas de aprendices. |
| training-environment-service | Ambientes de formacion | Administrar ambientes, sedes, edificios, recursos, capacidad, disponibilidad y ventanas de mantenimiento. |
| scheduling-service | Programacion de horarios | Orquestar la creacion, validacion, aprobacion y publicacion de horarios academicos, evitando cruces de instructor, ficha y ambiente. |
| actors-service | Actores academicos | Gestionar perfiles academicos de instructores, coordinadores, especialidades, disponibilidad y vinculacion institucional. |
| document-service | Documentos y reportes | Generar, almacenar, versionar y servir documentos, reportes PDF, evidencias y soportes asociados a horarios. |
| monitoring-service | Observabilidad operativa | Centralizar salud tecnica, metricas, trazas, alertas y senales operativas de los microservicios. |
| audit-service | Auditoria y trazabilidad | Registrar eventos criticos, cambios de datos, accesos sensibles, politicas de retencion e integridad probatoria. |

## Flujo principal de scheduling-service

~~~mermaid
sequenceDiagram
    participant C as Coordinador
    participant S as scheduling-service
    participant A as academic-management-service
    participant I as actors-service
    participant E as training-environment-service
    participant D as document-service
    participant AU as audit-service
    C->>S: Crear horario
    S->>A: Validar ficha y programa
    S->>I: Validar instructor y disponibilidad
    S->>E: Validar ambiente y capacidad
    S->>S: Detectar conflictos
    S->>S: Persistir version del horario
    S->>D: Solicitar reporte PDF al aprobar
    S->>AU: Registrar trazabilidad
    S-->>C: Horario aprobado o conflicto detallado
~~~



