# Microservices Documentation Standard

## Objetivo

Definir el estándar documental que deberán seguir todos los microservicios del proyecto.

La documentación debe permitir comprender rápidamente:

* Responsabilidades.
* Dependencias.
* APIs.
* Eventos.
* Datos.

---

# Estructura Obligatoria

Cada microservicio deberá contener:

## API Contract

Descripción de:

* Endpoints.
* Métodos HTTP.
* Parámetros.
* Respuestas.

Documento:

api-contract.md

---

## Data Model

Descripción de:

* Entidades.
* Relaciones.
* Restricciones.

Documento:

data-model.md

---

## Events

Descripción de:

* Eventos publicados.
* Eventos consumidos.

Documento:

events.md

---

## Runbook

Descripción de:

* Despliegue.
* Configuración.
* Operación.

Documento:

runbook.md

---

# Información General

Cada servicio debe incluir:

## Nombre

Ejemplo:

Security Service

---

## Propósito

Descripción funcional.

---

## Responsabilidades

Lista de funciones del servicio.

Ejemplo:

* Gestión de usuarios.
* Gestión de roles.
* Gestión de permisos.

---

# Dependencias

Debe documentarse:

## Dependencias Internas

Otros microservicios.

## Dependencias Externas

APIs externas.

## Base de Datos

Motor utilizado.

---

# APIs

Cada endpoint debe documentar:

* Método.
* URL.
* Descripción.
* Request.
* Response.
* Códigos HTTP.

---

# Eventos

Ejemplo:

UserCreated

InstructorAssigned

ScheduleGenerated

Cada evento debe especificar:

* Productor.
* Consumidor.
* Payload.

---

# Observabilidad

Documentar:

* Logs.
* Métricas.
* Alertas.

---

# Seguridad

Documentar:

* JWT.
* Roles.
* Permisos.
* Auditoría.

---

# Mantenimiento

Todo cambio en un microservicio debe reflejarse inmediatamente en su documentación asociada.
