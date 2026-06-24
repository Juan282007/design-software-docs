# Domain Map

## Objetivo

Definir los dominios funcionales que conforman el Sistema de Gestión de Horarios SENA y las relaciones existentes entre ellos.

---

# Visión General

El sistema se divide en varios dominios de negocio que representan áreas funcionales independientes.

Cada dominio puede implementarse como uno o varios microservicios.

---

# Dominio de Seguridad

## Responsabilidad

Gestionar acceso al sistema.

## Funciones

* Usuarios
* Roles
* Permisos
* Sesiones
* Auditoría

## Entidades Principales

* User
* Role
* Permission
* Session

---

# Dominio de Parametrización

## Responsabilidad

Administrar configuraciones generales.

## Funciones

* Catálogos
* Parámetros
* Estados

## Entidades

* Catalog
* CatalogDetail
* Status
* Parameter

---

# Dominio Académico

## Responsabilidad

Administrar procesos formativos.

## Funciones

* Programas
* Fichas
* Aprendices

## Entidades

* TrainingProgram
* TrainingRecord
* Apprentice

---

# Dominio de Talento Humano

## Responsabilidad

Administrar instructores.

## Entidades

* Instructor
* Specialty
* AcademicLevel

---

# Dominio de Infraestructura

## Responsabilidad

Administrar ambientes y recursos físicos.

## Entidades

* Environment
* Resource
* Building

---

# Dominio de Programación

## Responsabilidad

Gestionar horarios académicos.

## Entidades

* Schedule
* ScheduleAssignment
* ScheduleDetail

---

# Relaciones Entre Dominios

## Seguridad ↔ Todos los Dominios

Control de acceso.

---

## Parametrización ↔ Todos los Dominios

Suministra estados, catálogos y parámetros.

---

## Académico ↔ Programación

Las fichas requieren horarios.

---

## Instructor ↔ Programación

Los instructores reciben asignaciones.

---

## Infraestructura ↔ Programación

Los ambientes son utilizados por los horarios.

---

# Beneficios de la Separación

* Escalabilidad.
* Mantenibilidad.
* Independencia.
* Reutilización.
