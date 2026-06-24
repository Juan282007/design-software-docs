# Testing Strategy

## Objetivo

Definir la estrategia de pruebas utilizada en el Sistema de Gestión de Horarios SENA para garantizar el correcto funcionamiento de los componentes funcionales y no funcionales.

---

# Alcance

La estrategia cubre:

- Frontend
- Backend
- APIs
- Base de datos
- Integraciones
- Seguridad

---

# Pirámide de Pruebas

La estrategia seguirá el modelo de pirámide de testing.

## Unit Tests

Validan componentes individuales.

Cobertura esperada:

70%

---

## Integration Tests

Validan interacción entre componentes.

Cobertura esperada:

20%

---

## End-to-End Tests

Validan flujos completos.

Cobertura esperada:

10%

---

# Tipos de Prueba

## Pruebas Unitarias

Objetivo:

Validar métodos y funciones individuales.

Herramientas:

Frontend:

- Vitest
- Jest

Backend:

- JUnit

---

## Pruebas de Integración

Objetivo:

Validar interacción entre módulos.

Ejemplos:

- Usuario ↔ Roles
- Horario ↔ Instructor
- Horario ↔ Ambiente

---

## Pruebas Funcionales

Objetivo:

Validar requisitos funcionales.

Ejemplos:

- Registrar usuario.
- Crear horario.
- Consultar ficha.

---

## Pruebas de Regresión

Objetivo:

Garantizar que nuevas funcionalidades no afecten funcionalidades existentes.

---

## Pruebas de Seguridad

Objetivo:

Validar mecanismos de autenticación y autorización.

Pruebas:

- JWT
- Roles
- Permisos

---

## Pruebas de Rendimiento

Objetivo:

Validar tiempos de respuesta.

Meta:

Menor a 3 segundos.

---

# Evidencias

Toda prueba deberá generar:

- Capturas
- Resultados
- Reportes
- Logs

---

# Criterios de Aprobación

Una funcionalidad será aprobada cuando:

- Cumpla criterios de aceptación.
- No presente errores críticos.
- Pase pruebas funcionales.
- Pase pruebas de integración.