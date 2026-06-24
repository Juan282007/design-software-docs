# Environments

## Objetivo

Definir los ambientes utilizados durante el ciclo de vida del Sistema de Gestión de Horarios SENA.

---

# Ambientes Disponibles

## Development (DEV)

### Propósito

Desarrollo de funcionalidades.

### Usuarios

Equipo de desarrollo.

### Características

- Cambios frecuentes.
- Datos de prueba.
- Despliegues continuos.

### URL

https://dev.horarios-sena.com

---

# Quality Assurance (QA)

## Propósito

Validación funcional.

## Usuarios

- QA
- Product Owner
- Analistas

## Características

- Pruebas integrales.
- Validación de historias.
- Validación de defectos.

### URL

https://qa.horarios-sena.com

---

# Production (PROD)

## Propósito

Operación oficial.

## Usuarios

Usuarios finales.

## Características

- Alta disponibilidad.
- Datos reales.
- Seguridad reforzada.

### URL

https://horarios-sena.com

---

# Estrategia de Promoción

Development

↓

QA

↓

Production

---

# Reglas

## DEV

Permite pruebas experimentales.

---

## QA

Permite validaciones funcionales.

---

## PROD

Solo cambios aprobados.

---

# Control de Versiones

Cada despliegue debe registrar:

- Fecha.
- Versión.
- Responsable.
- Evidencias.

---

# Gestión de Configuración

Cada ambiente tendrá:

- Variables propias.
- Base de datos propia.
- Logs independientes.

---

# Seguridad

Las credenciales deberán administrarse mediante:

- Variables de entorno.
- Secret Managers.
- Configuración protegida.

---

# Monitoreo

Todos los ambientes deberán registrar:

- Logs.
- Errores.
- Métricas.
- Disponibilidad.