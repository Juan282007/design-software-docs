# Architecture Overview

## Introducción

El Sistema de Gestión de Horarios SENA ha sido diseñado utilizando una arquitectura basada en microservicios con el objetivo de garantizar escalabilidad, mantenibilidad, disponibilidad y desacoplamiento entre los diferentes dominios de negocio.

Esta arquitectura permite que cada módulo funcional pueda evolucionar de manera independiente sin afectar el funcionamiento global del sistema.

---

# Objetivos Arquitectónicos

La arquitectura propuesta busca:

- Facilitar el mantenimiento del sistema.
- Permitir crecimiento modular.
- Mejorar la disponibilidad.
- Incrementar la escalabilidad.
- Reducir dependencias entre módulos.
- Facilitar despliegues independientes.
- Mejorar la trazabilidad de cambios.

---

# Estilo Arquitectónico

El sistema adopta una arquitectura basada en microservicios.

Cada microservicio implementa una capacidad específica del negocio y posee responsabilidades claramente definidas.

---

# Componentes Principales

## Frontend

Responsable de la interacción con los usuarios.

Tecnologías:

- React
- Vite
- React Router
- Axios

Responsabilidades:

- Visualización de información.
- Navegación.
- Validación básica.
- Consumo de APIs.

---

## API Gateway

Representa el punto único de entrada al sistema.

Responsabilidades:

- Centralizar solicitudes.
- Aplicar autenticación.
- Enrutar peticiones.
- Controlar acceso.

Beneficios:

- Mayor seguridad.
- Menor acoplamiento.
- Gestión centralizada.

---

## Microservicio de Seguridad

Responsabilidades:

- Usuarios.
- Roles.
- Permisos.
- Autenticación.
- Sesiones.
- Auditoría.

Entidades:

- User
- Role
- Permission
- Session
- AuditLog

---

## Microservicio de Parametrización

Responsabilidades:

- Parámetros.
- Catálogos.
- Estados.
- Configuraciones.

Entidades:

- Parameter
- Catalog
- CatalogDetail
- Status

---

## Microservicio Académico

Responsabilidades:

- Programas.
- Fichas.
- Aprendices.

Entidades:

- TrainingProgram
- TrainingRecord
- Apprentice

---

## Microservicio de Instructores

Responsabilidades:

- Registro de instructores.
- Especialidades.
- Disponibilidad.

Entidades:

- Instructor
- Specialty
- Availability

---

## Microservicio de Infraestructura

Responsabilidades:

- Ambientes.
- Recursos.
- Capacidad.

Entidades:

- Environment
- Resource
- Building

---

## Microservicio de Horarios

Responsabilidades:

- Programación académica.
- Asignaciones.
- Validaciones.

Entidades:

- Schedule
- ScheduleAssignment
- ScheduleDetail

---

# Persistencia

Cada microservicio administra su propia base de datos lógica.

Principios:

- Independencia.
- Bajo acoplamiento.
- Escalabilidad.

---

# Comunicación

La comunicación entre componentes se realiza mediante:

## Comunicación Sincrónica

REST API

Utilizada para:

- Consultas.
- Operaciones CRUD.

---

## Comunicación Asincrónica

Eventos de dominio.

Ejemplos:

- UserCreated
- ScheduleCreated
- EnvironmentReserved

---

# Seguridad

El acceso se controla mediante:

- JWT
- Roles
- Permisos
- Auditoría

---

# Beneficios

- Escalabilidad.
- Mantenibilidad.
- Flexibilidad.
- Seguridad.
- Independencia tecnológica.
