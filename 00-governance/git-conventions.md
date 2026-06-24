# Git Conventions

## Objetivo

Establecer las reglas para el control de versiones del proyecto Horarios SENA mediante Git, garantizando trazabilidad, colaboración eficiente y control sobre los cambios realizados.

---

# Estrategia de Ramas

El proyecto utiliza una estrategia basada en Git Flow simplificado.

## main

Representa la versión estable en producción.

Características:

* Código validado.
* Sin errores críticos.
* Solo recibe cambios aprobados.

---

## qa

Representa el ambiente de pruebas.

Características:

* Validación funcional.
* Validación de integración.
* Pruebas de aceptación.

---

## dev

Representa la rama principal de desarrollo.

Características:

* Integración de funcionalidades.
* Desarrollo continuo.

---

## feature

Utilizada para nuevas funcionalidades.

Formato:

feature/HU-001-login

Ejemplos:

feature/HU-002-user-management

feature/HU-010-schedule-module

---

## bugfix

Utilizada para corrección de errores.

Formato:

bugfix/BUG-001-login

---

## hotfix

Utilizada para correcciones urgentes en producción.

Formato:

hotfix/HOT-001-security

---

# Convención de Commits

Se utilizará Conventional Commits.

## feat

Nueva funcionalidad.

Ejemplo:

feat: create instructor management module

---

## fix

Corrección de errores.

Ejemplo:

fix: validate duplicate email registration

---

## docs

Cambios en documentación.

Ejemplo:

docs: update architecture overview

---

## refactor

Mejoras internas sin afectar funcionalidad.

Ejemplo:

refactor: optimize schedule validation service

---

## test

Pruebas.

Ejemplo:

test: add unit tests for user service

---

## chore

Tareas administrativas.

Ejemplo:

chore: update dependencies

---

# Pull Requests

Todo cambio deberá realizarse mediante Pull Request.

El Pull Request deberá incluir:

* Descripción del cambio.
* Historia de usuario relacionada.
* Evidencias de pruebas.
* Impacto generado.

---

# Revisión de Código

Antes de aprobar un Pull Request se verificará:

* Calidad del código.
* Cumplimiento de estándares.
* Seguridad.
* Rendimiento.
* Documentación.

---

# Versionamiento

Formato:

MAJOR.MINOR.PATCH

Ejemplo:

1.0.0

1.1.0

1.1.1

## Significado

MAJOR:
Cambios incompatibles.

MINOR:
Nuevas funcionalidades compatibles.

PATCH:
Correcciones.
