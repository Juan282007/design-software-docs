# OpenAPI Contracts

## Objetivo

Esta carpeta contiene las especificaciones OpenAPI (Swagger) de los microservicios del Sistema de Gestión de Horarios SENA.

---

# Estructura

Cada microservicio deberá poseer su propio contrato.

Ejemplo:

security-service.yaml

academic-service.yaml

schedule-service.yaml

instructor-service.yaml

---

# Información Obligatoria

Toda especificación OpenAPI deberá incluir:

- Información general.
- Versionamiento.
- Endpoints.
- Modelos.
- Respuestas.
- Seguridad.

---

# Ejemplo de Endpoint

GET /api/v1/users

Descripción:

Consultar usuarios registrados.

---

# Beneficios

- Integración sencilla.
- Generación automática de documentación.
- Consistencia entre equipos.