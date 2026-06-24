# Domain Events

## Objetivo

Documentar los eventos de negocio que ocurren dentro del Sistema de Gestión de Horarios SENA y que pueden ser consumidos por otros módulos o microservicios.

Los eventos representan sucesos importantes que generan cambios dentro del dominio.

---

# ¿Qué es un Evento de Dominio?

Un evento de dominio representa un hecho que ya ocurrió dentro del sistema y que tiene relevancia para otros procesos.

Ejemplo:

Un instructor fue registrado.

Un horario fue asignado.

Un ambiente fue reservado.

---

# Eventos del Módulo de Seguridad

## UserCreated

### Descripción

Se genera cuando un usuario es registrado exitosamente.

### Datos

* userId
* name
* email
* role

### Consumidores

* Auditoría
* Notificaciones

---

## UserUpdated

Se genera cuando se actualiza la información de un usuario.

---

## UserDisabled

Se genera cuando un usuario es deshabilitado.

---

# Eventos del Módulo de Instructores

## InstructorCreated

Se genera cuando un instructor es registrado.

### Datos

* instructorId
* document
* name
* specialty

---

## InstructorUpdated

Actualización de información del instructor.

---

# Eventos del Módulo de Ambientes

## EnvironmentCreated

Se genera cuando se registra un ambiente.

---

## EnvironmentReserved

Se genera cuando un ambiente es asignado a un horario.

---

## EnvironmentReleased

Se genera cuando se libera un ambiente.

---

# Eventos del Módulo de Programación

## ScheduleCreated

Se genera cuando se crea un horario.

### Datos

* scheduleId
* instructorId
* environmentId
* trainingRecordId
* startDate
* endDate

---

## ScheduleUpdated

Modificación de un horario existente.

---

## ScheduleDeleted

Eliminación lógica de un horario.

---

# Eventos del Módulo Académico

## TrainingProgramCreated

Registro de programa de formación.

---

## TrainingRecordCreated

Registro de ficha.

---

## ApprenticeAssigned

Asignación de aprendiz a ficha.

---

# Eventos del Módulo de Parametrización

## ParameterCreated

Creación de parámetro.

---

## CatalogUpdated

Actualización de catálogo.

---

## StatusChanged

Cambio de estado de una entidad.

---

# Beneficios

* Desacoplamiento entre servicios.
* Escalabilidad.
* Trazabilidad.
* Integración sencilla.
