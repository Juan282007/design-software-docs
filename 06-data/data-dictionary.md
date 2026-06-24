# Data Dictionary

## Objetivo

Este documento describe los datos administrados por el Sistema de Gestión de Horarios SENA, incluyendo entidades, atributos, tipos de datos y restricciones.

Su propósito es garantizar un entendimiento común entre analistas, desarrolladores, arquitectos y administradores de bases de datos.

---

# User

## Descripción

Representa una persona con acceso al sistema.

| Campo | Tipo | Restricción | Descripción |
|---------|---------|---------|---------|
| id_user | UUID | PK | Identificador único |
| document_number | VARCHAR(20) | UNIQUE | Documento |
| first_name | VARCHAR(100) | NOT NULL | Nombre |
| last_name | VARCHAR(100) | NOT NULL | Apellido |
| email | VARCHAR(150) | UNIQUE | Correo institucional |
| password_hash | VARCHAR(255) | NOT NULL | Contraseña cifrada |
| status_id | UUID | FK | Estado |
| created_at | TIMESTAMP | NOT NULL | Fecha creación |

---

# Role

## Descripción

Representa los roles disponibles.

| Campo | Tipo |
|---------|---------|
| id_role | UUID |
| role_name | VARCHAR(100) |
| description | TEXT |

---

# Permission

## Descripción

Permisos asociados a roles.

| Campo | Tipo |
|---------|---------|
| id_permission | UUID |
| permission_name | VARCHAR(100) |
| description | TEXT |

---

# Instructor

## Descripción

Información de instructores.

| Campo | Tipo |
|---------|---------|
| id_instructor | UUID |
| document_number | VARCHAR(20) |
| first_name | VARCHAR(100) |
| last_name | VARCHAR(100) |
| email | VARCHAR(150) |
| phone | VARCHAR(20) |
| specialty_id | UUID |
| status_id | UUID |

---

# Apprentice

## Descripción

Información de aprendices.

| Campo | Tipo |
|---------|---------|
| id_apprentice | UUID |
| document_number | VARCHAR(20) |
| first_name | VARCHAR(100) |
| last_name | VARCHAR(100) |
| email | VARCHAR(150) |
| training_record_id | UUID |

---

# Training Program

## Descripción

Programas de formación.

| Campo | Tipo |
|---------|---------|
| id_program | UUID |
| code | VARCHAR(20) |
| program_name | VARCHAR(200) |
| duration_hours | INTEGER |
| status_id | UUID |

---

# Training Record

## Descripción

Representa una ficha.

| Campo | Tipo |
|---------|---------|
| id_training_record | UUID |
| record_number | VARCHAR(50) |
| program_id | UUID |
| start_date | DATE |
| end_date | DATE |
| status_id | UUID |

---

# Environment

## Descripción

Ambientes de formación.

| Campo | Tipo |
|---------|---------|
| id_environment | UUID |
| environment_name | VARCHAR(150) |
| capacity | INTEGER |
| location | VARCHAR(200) |
| status_id | UUID |

---

# Schedule

## Descripción

Programación académica.

| Campo | Tipo |
|---------|---------|
| id_schedule | UUID |
| training_record_id | UUID |
| instructor_id | UUID |
| environment_id | UUID |
| start_datetime | TIMESTAMP |
| end_datetime | TIMESTAMP |
| status_id | UUID |

---

# Audit Log

## Descripción

Registro de auditoría.

| Campo | Tipo |
|---------|---------|
| id_audit | UUID |
| user_id | UUID |
| action | VARCHAR(100) |
| entity_name | VARCHAR(100) |
| action_date | TIMESTAMP |
| details | TEXT |