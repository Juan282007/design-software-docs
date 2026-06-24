# API Authentication

## Objetivo

Definir el mecanismo de autenticación y autorización utilizado por las APIs del Sistema de Gestión de Horarios SENA.

El objetivo es garantizar que únicamente usuarios autorizados puedan acceder a los recursos del sistema.

---

# Arquitectura de Seguridad

La autenticación se realizará mediante JSON Web Token (JWT).

Flujo:

Usuario
↓
Login
↓
Security Service
↓
JWT Token
↓
API Gateway
↓
Microservices

---

# Proceso de Autenticación

## Paso 1 - Inicio de Sesión

El usuario envía:

{
    "email": "usuario@sena.edu.co",
    "password": "******"
}

---

## Paso 2 - Validación

El Security Service valida:

- Usuario existente.
- Estado activo.
- Contraseña correcta.

---

## Paso 3 - Generación de Token

Si la validación es exitosa:

{
    "accessToken": "jwt_token",
    "expiresIn": 3600,
    "role": "Coordinator"
}

---

## Paso 4 - Consumo de APIs

Las solicitudes deberán incluir:

Authorization: Bearer jwt_token

---

# Estructura del JWT

Claims recomendados:

{
    "sub": "user_id",
    "email": "usuario@sena.edu.co",
    "role": "Coordinator",
    "iat": 1710000000,
    "exp": 1710003600
}

---

# Autorización

La autorización estará basada en Roles y Permisos.

---

## Roles

Administrador

Permisos:

- Gestión total.

---

Coordinador

Permisos:

- Gestión académica.
- Gestión de horarios.

---

Instructor

Permisos:

- Consultar horarios.
- Consultar asignaciones.

---

Aprendiz

Permisos:

- Consultar programación.

---

# Expiración

Tiempo recomendado:

60 minutos.

---

# Refresh Token

Para futuras versiones se contempla:

- Refresh Token.
- Renovación automática.

---

# Respuestas de Error

401 Unauthorized

Usuario no autenticado.

---

403 Forbidden

Usuario autenticado sin permisos.

---

# Seguridad Adicional

- HTTPS obligatorio.
- Tokens cifrados.
- Auditoría de accesos.
