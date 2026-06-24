# Functional Requirements

## Introducción

Los requisitos funcionales describen las capacidades, comportamientos y servicios que debe proporcionar el Sistema de Gestión de Horarios SENA.

Estos requisitos representan las funcionalidades esperadas por los usuarios y constituyen la base para el desarrollo de la solución.

---

# RF-001 Gestión de Usuarios

## Descripción

El sistema deberá permitir registrar usuarios dentro de la plataforma.

## Actor

Administrador.

## Entradas

* Documento.
* Nombre.
* Correo.
* Contraseña.
* Rol.

## Salidas

* Usuario registrado.

## Criterios de aceptación

* El correo debe ser único.
* El documento debe ser único.
* La contraseña debe almacenarse cifrada.

---

# RF-002 Gestión de Roles

## Descripción

Permitir la administración de roles institucionales.

## Funcionalidades

* Crear rol.
* Editar rol.
* Consultar rol.
* Inactivar rol.

---

# RF-003 Gestión de Permisos

El sistema deberá permitir asignar permisos a cada rol.

---

# RF-004 Inicio de Sesión

Permitir la autenticación de usuarios mediante credenciales válidas.

---

# RF-005 Gestión de Instructores

## Funcionalidades

* Registrar instructor.
* Actualizar instructor.
* Consultar instructor.
* Inactivar instructor.

## Validaciones

* Documento único.
* Estado activo.

---

# RF-006 Gestión de Aprendices

## Funcionalidades

* Registrar aprendiz.
* Consultar aprendiz.
* Actualizar información.

---

# RF-007 Gestión de Programas

## Funcionalidades

* Crear programa.
* Consultar programa.
* Modificar programa.
* Inactivar programa.

---

# RF-008 Gestión de Fichas

## Funcionalidades

* Registrar ficha.
* Consultar ficha.
* Modificar ficha.
* Asociar aprendices.

---

# RF-009 Gestión de Ambientes

## Funcionalidades

* Registrar ambiente.
* Consultar disponibilidad.
* Actualizar capacidad.

---

# RF-010 Gestión de Horarios

## Funcionalidades

* Crear horario.
* Modificar horario.
* Eliminar horario.
* Consultar horario.

## Reglas

* Debe existir instructor.
* Debe existir ambiente.
* Debe existir ficha.

---

# RF-011 Validación de Conflictos

El sistema deberá impedir:

* Cruce de horarios.
* Doble asignación de ambientes.
* Doble asignación de instructores.

---

# RF-012 Gestión de Parámetros

Permitir administrar parámetros configurables.

---

# RF-013 Gestión de Catálogos

Permitir administrar catálogos institucionales.

---

# RF-014 Auditoría

Registrar eventos críticos del sistema.

---

# RF-015 Reportes

Generar reportes de:

* Horarios.
* Ambientes.
* Instructores.
* Ocupación.

---

# RF-016 Notificaciones

Enviar notificaciones relacionadas con cambios importantes del sistema.
