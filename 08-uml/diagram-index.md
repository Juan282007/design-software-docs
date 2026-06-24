# UML Diagram Index

## Objetivo

Este documento centraliza el inventario de diagramas utilizados en el proyecto Sistema de Gestión de Horarios SENA.

Su propósito es facilitar la localización, mantenimiento y trazabilidad de los diagramas durante todo el ciclo de vida del software.

---

# Organización de Diagramas

Los diagramas se almacenan en dos ubicaciones:

## Source

Ubicación:

08-uml/source/

Contiene los archivos editables.

Ejemplos:

- Draw.io
- XML
- PlantUML

---

## Exports

Ubicación:

08-uml/exports/

Contiene versiones exportadas para consulta.

Formatos:

- PNG
- JPG
- PDF
- SVG

---

# Catálogo de Diagramas

## UML-001 Diagrama de Contexto

### Objetivo

Representar la interacción entre el sistema y los actores externos.

### Actores

- Administrador
- Coordinador
- Instructor
- Aprendiz

### Ubicación

source/context-diagram.drawio

exports/context-diagram.png

---

## UML-002 Diagrama de Casos de Uso

### Objetivo

Representar las funcionalidades del sistema desde la perspectiva de los usuarios.

### Casos Principales

- Gestionar usuarios
- Gestionar roles
- Gestionar instructores
- Gestionar aprendices
- Gestionar ambientes
- Gestionar horarios
- Generar reportes

---

## UML-003 Diagrama de Dominio

### Objetivo

Representar los conceptos principales del negocio y sus relaciones.

---

## UML-004 Diagrama de Clases

### Objetivo

Representar la estructura estática del sistema.

### Elementos

- Clases
- Atributos
- Métodos
- Relaciones

---

## UML-005 Diagrama de Componentes

### Objetivo

Mostrar la arquitectura lógica del sistema.

### Componentes

- Frontend
- API Gateway
- Security Service
- Academic Service
- Schedule Service
- Instructor Service
- Parameterization Service

---

## UML-006 Diagrama de Despliegue

### Objetivo

Representar la infraestructura física.

### Elementos

- Cliente Web
- Servidor Frontend
- API Gateway
- Microservicios
- PostgreSQL

---

## UML-007 Diagrama de Secuencia Login

### Objetivo

Representar el flujo de autenticación.

### Participantes

- Usuario
- Frontend
- API Gateway
- Security Service
- Database

---

## UML-008 Diagrama de Secuencia Gestión de Horarios

### Objetivo

Representar la creación de horarios.

---

## UML-009 Modelo Entidad Relación (MER)

### Objetivo

Representar las entidades de la base de datos.

### Elementos

- Seguridad
- Parametrización
- Académico
- Instructores
- Ambientes
- Horarios

---

## UML-010 Bounded Context Diagram

### Objetivo

Representar los dominios del sistema.

### Dominios

- Security
- Parameterization
- Academic
- Infrastructure
- Scheduling

---

# Control de Versiones

Todo cambio en un diagrama deberá:

- Mantener archivo fuente.
- Actualizar exportación.
- Registrar cambios mediante Git.

---

# Convenciones

## Nombres

Formato:

tipo-diagrama-modulo-version

Ejemplo:

class-diagram-schedule-v1.drawio

sequence-login-v1.drawio

deployment-v1.drawio

---

# Responsabilidades

Los diagramas deberán mantenerse actualizados respecto a:

- Requisitos
- Arquitectura
- Modelo de datos
- Microservicios

---

# Estado de Diagramas

| Código | Nombre | Estado |
|----------|----------|----------|
| UML-001 | Contexto | Activo |
| UML-002 | Casos de Uso | Activo |
| UML-003 | Dominio | Activo |
| UML-004 | Clases | Activo |
| UML-005 | Componentes | Activo |
| UML-006 | Despliegue | Activo |
| UML-007 | Secuencia Login | Activo |
| UML-008 | Secuencia Horarios | Activo |
| UML-009 | MER | Activo |
| UML-010 | Bounded Context | Activo |