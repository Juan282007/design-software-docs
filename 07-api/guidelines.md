# API Guidelines

## Objetivo

Definir estándares para el diseño, implementación y mantenimiento de las APIs del Sistema de Gestión de Horarios SENA.

---

# Principios

Las APIs deben ser:

- Simples.
- Consistentes.
- Escalables.
- Versionables.
- Seguras.

---

# Arquitectura

Las APIs seguirán el estilo REST.

---

# Versionamiento

Formato:

/api/v1/

Ejemplos:

/api/v1/users

/api/v1/instructors

/api/v1/schedules

---

# Métodos HTTP

GET

Consultar información.

POST

Crear información.

PUT

Actualizar completamente.

PATCH

Actualizar parcialmente.

DELETE

Eliminar lógicamente.

---

# Convención de Recursos

Correcto:

/users

/instructors

/training-records

/schedules

---

Incorrecto:

/getUsers

/createInstructor

/deleteSchedule

---

# Códigos HTTP

200 OK

Consulta exitosa.

---

201 Created

Registro creado.

---

204 No Content

Operación exitosa sin contenido.

---

400 Bad Request

Solicitud incorrecta.

---

401 Unauthorized

No autenticado.

---

403 Forbidden

Sin permisos.

---

404 Not Found

Recurso inexistente.

---

500 Internal Server Error

Error interno.

---

# Formato de Respuesta

Respuesta Exitosa:

{
    "success": true,
    "data": {}
}

---

Respuesta Error:

{
    "success": false,
    "message": "Resource not found"
}

---

# Paginación

Formato:

GET /users?page=1&size=10

Respuesta:

{
    "page": 1,
    "size": 10,
    "totalElements": 100,
    "totalPages": 10,
    "content": []
}

---

# Filtrado

Ejemplo:

GET /instructors?status=ACTIVE

---

# Ordenamiento

Ejemplo:

GET /users?sort=name,asc

---

# Validaciones

Todas las APIs deberán validar:

- Campos obligatorios.
- Formatos.
- Restricciones de negocio.

---

# Documentación

Todas las APIs deberán documentarse mediante OpenAPI.

---

# Seguridad

Toda API protegida deberá validar:

- JWT.
- Permisos.
- Roles.
