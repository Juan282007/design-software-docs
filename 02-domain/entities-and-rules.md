# Entities and Business Rules

## Objetivo

Documentar las entidades principales del sistema y las reglas de negocio que gobiernan su comportamiento.

---

# User

## Descripción

Representa una persona con acceso al sistema.

## Reglas

RN-001

El correo electrónico debe ser único.

RN-002

Un usuario debe tener al menos un rol.

RN-003

Un usuario inactivo no puede iniciar sesión.

---

# Instructor

## Descripción

Representa un instructor del SENA.

## Reglas

RN-004

Un instructor debe encontrarse activo para recibir asignaciones.

RN-005

Un instructor no puede tener dos horarios simultáneos.

RN-006

Debe pertenecer a un centro de formación.

---

# Apprentice

## Descripción

Representa un aprendiz.

## Reglas

RN-007

Debe pertenecer a una ficha.

RN-008

Solo puede estar asociado a una ficha activa.

---

# Training Program

## Descripción

Programa académico ofrecido por el SENA.

## Reglas

RN-009

Debe encontrarse activo.

RN-010

Debe poseer una duración válida.

---

# Training Record

## Descripción

Representa una ficha de formación.

## Reglas

RN-011

Debe pertenecer a un programa.

RN-012

Puede tener múltiples horarios.

---

# Environment

## Descripción

Representa un ambiente de aprendizaje.

## Reglas

RN-013

No puede asignarse a dos horarios simultáneamente.

RN-014

Debe encontrarse activo.

RN-015

Debe tener capacidad suficiente.

---

# Schedule

## Descripción

Representa la programación académica.

## Reglas

RN-016

Debe tener instructor asignado.

RN-017

Debe tener ambiente asignado.

RN-018

Debe tener fecha válida.

RN-019

Debe estar asociado a una ficha.

RN-020

La hora de inicio debe ser menor que la hora final.

---

# Role

## Descripción

Determina permisos de acceso.

## Reglas

RN-021

Todo rol debe tener permisos asociados.

---

# Permission

## Descripción

Representa una autorización específica.

## Reglas

RN-022

No pueden existir permisos duplicados.

---

# Status

## Descripción

Representa el estado de una entidad.

## Reglas

RN-023

Toda entidad principal debe tener estado.

---

# Auditoría

## Reglas

RN-024

Toda operación crítica debe registrarse.

RN-025

Toda modificación debe conservar trazabilidad.

---

# Restricciones Globales

RN-026

No se permite eliminación física de información crítica.

RN-027

Toda información debe mantener integridad referencial.

RN-028

Las operaciones sensibles requieren autenticación válida.

RN-029

Los cambios deben quedar registrados en auditoría.

RN-030

Los conflictos de horario deben ser bloqueados automáticamente.
