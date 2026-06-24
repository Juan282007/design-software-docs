# Data Models

## Objetivo

Describir la estructura lógica y conceptual de los datos utilizados por el Sistema de Gestión de Horarios SENA.

---

# Modelo Conceptual

El modelo conceptual identifica las entidades principales del negocio y sus relaciones.

Entidades principales:

- User
- Role
- Permission
- Instructor
- Apprentice
- TrainingProgram
- TrainingRecord
- Environment
- Schedule
- AuditLog
- Parameter
- Catalog

---

# Modelo Lógico

## Seguridad

User (1,N) UserRole

Role (1,N) UserRole

Role (1,N) RolePermission

Permission (1,N) RolePermission

---

## Académico

TrainingProgram (1,N) TrainingRecord

TrainingRecord (1,N) Apprentice

---

## Instructores

Instructor (1,N) Schedule

---

## Infraestructura

Environment (1,N) Schedule

---

## Programación

TrainingRecord (1,N) Schedule

---

# Modelo Físico

La implementación se realizará sobre PostgreSQL.

Características:

- Integridad referencial.
- Restricciones de unicidad.
- Índices.
- Claves primarias UUID.

---

# Convenciones

## Claves Primarias

Formato:

id_entity

Ejemplos:

id_user

id_schedule

id_environment

---

## Claves Foráneas

Formato:

entity_id

Ejemplos:

role_id

status_id

program_id

---

# Estrategia de Integridad

Se aplicarán:

- Primary Keys
- Foreign Keys
- Unique Constraints
- Check Constraints

---

# Estrategia de Auditoría

Todas las entidades críticas deberán registrar:

- Fecha creación
- Fecha modificación
- Usuario responsable

---

# Entidades Compartidas

Algunos datos serán consumidos por múltiples módulos:

- User
- Status
- Parameter
- Catalog

Estos deberán exponerse mediante APIs controladas.
