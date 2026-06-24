# CI/CD Strategy

## Objetivo

Definir el proceso de integración continua y despliegue continuo del Sistema de Gestión de Horarios SENA.

---

# Conceptos

## CI

Continuous Integration.

Permite validar automáticamente cambios realizados por los desarrolladores.

---

## CD

Continuous Delivery / Deployment.

Permite desplegar versiones de forma controlada.

---

# Flujo General

Developer

↓

Git Commit

↓

Git Push

↓

Pull Request

↓

Code Review

↓

Merge

↓

Build

↓

Tests

↓

Deploy

---

# Pipeline de Integración Continua

## Etapa 1

Checkout Source Code

Objetivo:

Obtener código fuente.

---

## Etapa 2

Install Dependencies

Objetivo:

Instalar dependencias.

Frontend:

npm install

Backend:

mvn clean install

---

## Etapa 3

Static Analysis

Objetivo:

Validar calidad de código.

Herramientas:

- SonarQube
- ESLint

---

## Etapa 4

Unit Tests

Objetivo:

Validar funcionalidades.

---

## Etapa 5

Build

Objetivo:

Generar artefactos.

Frontend:

npm run build

Backend:

mvn package

---

# Pipeline de Despliegue

## Development

Despliegue automático.

---

## QA

Despliegue mediante aprobación.

---

## Production

Despliegue controlado.

Requiere:

- Aprobación.
- Evidencias.
- Validación QA.

---

# Estrategia de Rollback

Si ocurre una falla:

1. Identificar versión estable.
2. Revertir despliegue.
3. Restaurar servicio.
4. Documentar incidente.

---

# Métricas

## Build Success Rate

Porcentaje de compilaciones exitosas.

---

## Deployment Success Rate

Porcentaje de despliegues exitosos.

---

## Lead Time

Tiempo desde desarrollo hasta producción.

---

## Mean Time To Recovery (MTTR)

Tiempo promedio de recuperación.

---

# Herramientas Recomendadas

## Repositorio

GitHub

---

## CI/CD

GitHub Actions

---

## Contenedores

Docker

---

## Monitoreo

Grafana

Prometheus

---

# Buenas Prácticas

- Automatizar pruebas.
- Automatizar despliegues.
- Mantener pipelines simples.
- Evitar despliegues manuales.
- Registrar evidencias.
