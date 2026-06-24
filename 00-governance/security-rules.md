# Security Rules

## Objetivo

Establecer los lineamientos de seguridad que deben aplicarse durante el desarrollo, despliegue y operación del sistema Horarios SENA.

---

# Principios de Seguridad

El sistema debe garantizar:

* Confidencialidad.
* Integridad.
* Disponibilidad.
* Trazabilidad.
* Autenticidad.

---

# Gestión de Credenciales

## Prohibiciones

No se permite almacenar:

* Contraseñas.
* Tokens.
* Llaves privadas.
* Credenciales de base de datos.

Dentro del código fuente.

---

## Variables de Entorno

Las credenciales deberán almacenarse mediante:

.env

Secrets Manager

Variables del servidor.

---

# Gestión de Contraseñas

Las contraseñas deberán:

* Almacenarse cifradas.
* Utilizar algoritmos seguros.
* Nunca enviarse en texto plano.

---

# Autenticación

El sistema utilizará:

* JWT
* Refresh Tokens

Cuando aplique.

---

# Autorización

El acceso se controlará mediante:

## Roles

Ejemplos:

* Administrador
* Coordinador
* Instructor
* Aprendiz

---

## Permisos

Cada operación deberá validar permisos.

Ejemplo:

Crear horario.

Modificar usuario.

Eliminar ambiente.

---

# Protección de APIs

Todas las APIs deberán:

* Validar autenticación.
* Validar autorización.
* Registrar auditoría.
* Validar entradas.

---

# Auditoría

Se registrarán:

* Inicios de sesión.
* Cierre de sesión.
* Creación de registros.
* Actualizaciones.
* Eliminaciones.

---

# Protección de Datos

No se permitirá:

* Exposición de datos sensibles.
* Almacenamiento inseguro.
* Acceso no autorizado.

---

# Gestión de Errores

Los mensajes de error no deberán revelar:

* Consultas SQL.
* Estructura interna.
* Información sensible.

---

# OWASP Top 10

El proyecto deberá mitigar riesgos asociados a:

* Broken Access Control.
* Cryptographic Failures.
* Injection.
* Security Misconfiguration.
* Vulnerable Components.
* Authentication Failures.

---

# Registro de Incidentes

Todo incidente deberá documentarse indicando:

* Fecha.
* Descripción.
* Impacto.
* Solución.
* Responsable.

---

# Cumplimiento

Estas reglas aplican a:

* Backend.
* Frontend.
* APIs.
* Bases de datos.
* Infraestructura.
* Microservicios.
