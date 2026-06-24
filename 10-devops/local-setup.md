# Local Setup

## Objetivo

Este documento describe el proceso necesario para preparar el entorno de desarrollo local del Sistema de Gestión de Horarios SENA.

---

# Requisitos Previos

Antes de ejecutar el proyecto se debe contar con las siguientes herramientas instaladas.

## Software Requerido

### Git

Versión recomendada:

2.40 o superior

Verificar instalación:

git --version

---

### Node.js

Versión recomendada:

20.x LTS

Verificar instalación:

node --version

---

### NPM

Versión recomendada:

10.x o superior

Verificar instalación:

npm --version

---

### Java

Versión recomendada:

JDK 21

Verificar instalación:

java --version

---

### Maven

Versión recomendada:

3.9+

Verificar instalación:

mvn --version

---

### PostgreSQL

Versión recomendada:

16+

Verificar instalación:

psql --version

---

# Clonación del Proyecto

Clonar repositorio:

git clone https://github.com/organization/horarios-sena.git

Ingresar al proyecto:

cd horarios-sena

---

# Configuración Frontend

Ingresar al proyecto frontend:

cd frontend

Instalar dependencias:

npm install

Ejecutar:

npm run dev

Servidor:

http://localhost:5173

---

# Configuración Backend

Ingresar al microservicio:

cd security-service

Instalar dependencias:

mvn clean install

Ejecutar:

mvn spring-boot:run

---

# Configuración Base de Datos

Crear base de datos:

horarios_sena

Configurar credenciales en:

application.yml

---

# Variables de Entorno

Ejemplo:

DB_HOST=localhost

DB_PORT=5432

DB_NAME=horarios_sena

DB_USER=postgres

DB_PASSWORD=password

JWT_SECRET=secret_key

---

# Verificación

Validar:

- Frontend ejecutando.
- Backend ejecutando.
- Base de datos conectada.
- APIs respondiendo.

---

# Solución de Problemas

## Error de Dependencias

Eliminar:

node_modules

Ejecutar:

npm install

---

## Error de Maven

Ejecutar:

mvn clean install

---

## Error de Conexión

Verificar:

- PostgreSQL activo.
- Credenciales correctas.
- Puerto disponible.