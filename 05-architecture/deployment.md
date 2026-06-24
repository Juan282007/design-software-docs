# Deployment Architecture

## Introducción

Este documento describe la estrategia de despliegue utilizada por el Sistema de Gestión de Horarios SENA.

---

# Ambientes

El sistema contempla tres ambientes principales.

## Development

Propósito:

Entorno utilizado por desarrolladores.

Características:

- Desarrollo continuo.
- Pruebas locales.
- Configuración flexible.

---

## QA

Propósito:

Validación funcional.

Características:

- Pruebas integrales.
- Validación de historias.
- Pruebas de aceptación.

---

## Production

Propósito:

Operación institucional.

Características:

- Alta disponibilidad.
- Seguridad reforzada.
- Monitoreo continuo.

---

# Infraestructura

## Cliente

Acceso mediante navegador web.

Ejemplos:

- Google Chrome
- Microsoft Edge
- Mozilla Firefox

---

## Frontend Server

Hospeda la aplicación React.

Responsabilidades:

- Entregar interfaz.
- Consumir APIs.

---

## API Gateway

Canaliza todas las solicitudes.

Responsabilidades:

- Autenticación.
- Enrutamiento.
- Seguridad.

---

## Backend Services

Contiene los microservicios.

Servicios:

- Security Service
- Parameterization Service
- Academic Service
- Instructor Service
- Infrastructure Service
- Schedule Service

---

## Database Server

Motor de persistencia.

Tecnología:

PostgreSQL

Responsabilidades:

- Almacenamiento.
- Integridad.
- Respaldo.

---

# Dockerización

Todos los servicios podrán ejecutarse mediante contenedores Docker.

Ventajas:

- Portabilidad.
- Consistencia.
- Facilidad de despliegue.

---

# Variables de Entorno

Ejemplos:

DATABASE_URL

DATABASE_USER

DATABASE_PASSWORD

JWT_SECRET

API_PORT

---

# Pipeline CI/CD

Flujo:

1. Commit.
2. Push.
3. Pull Request.
4. Validación.
5. Merge.
6. Build.
7. Deploy.

---

# Estrategia de Despliegue

## Desarrollo

Despliegue automático.

---

## QA

Despliegue controlado.

---

## Producción

Despliegue aprobado por responsables.

---

# Recuperación

El sistema deberá:

- Mantener respaldos.
- Permitir restauración.
- Minimizar pérdida de datos.