# Dependencies

## Objetivo

Documentar las dependencias funcionales, técnicas y organizacionales necesarias para el correcto desarrollo del Sistema de Gestión de Horarios SENA.

---

# Introducción

Toda iniciativa tecnológica depende de componentes internos y externos para cumplir sus objetivos.

La identificación temprana de dependencias permite reducir riesgos y planificar adecuadamente las actividades del proyecto.

---

# Dependencias Tecnológicas

## Frontend

Tecnologías utilizadas:

- React
- Vite
- React Router
- Axios

Dependencia:

El frontend requiere disponibilidad de APIs para funcionar correctamente.

---

## Backend

Tecnologías utilizadas:

- Java
- Spring Boot
- Maven

Dependencia:

Necesita acceso a base de datos y servicios compartidos.

---

## Base de Datos

Tecnología:

PostgreSQL

Dependencias:

- Infraestructura disponible.
- Backups programados.
- Conectividad de red.

---

# Dependencias Funcionales

## Seguridad

Todos los módulos dependen del servicio de autenticación.

Servicios dependientes:

- Académico
- Horarios
- Infraestructura
- Parametrización

---

## Parametrización

Proporciona:

- Estados
- Catálogos
- Parámetros

Consumidores:

Todos los módulos.

---

## Académico

Proporciona:

- Programas
- Fichas
- Aprendices

Consumidores:

- Horarios
- Reportes

---

## Instructores

Proporciona:

- Información de instructores.
- Disponibilidad.

Consumidores:

- Horarios

---

## Infraestructura

Proporciona:

- Ambientes
- Recursos

Consumidores:

- Horarios

---

# Dependencias Externas

## GitHub

Gestión del código fuente.

---

## Docker

Contenerización.

---

## PostgreSQL

Persistencia.

---

# Gestión

Toda nueva dependencia deberá:

- Ser documentada.
- Ser evaluada.
- Ser aprobada por arquitectura.

---

# Control

Las dependencias deberán revisarse en cada iteración del proyecto.