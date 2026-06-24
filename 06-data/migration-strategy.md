# Migration Strategy

## Objetivo

Definir la estrategia para administrar cambios en la estructura de datos del proyecto.

---

# Principios

Toda modificación de base de datos deberá:

- Ser versionada.
- Ser documentada.
- Ser reproducible.
- Ser reversible cuando sea posible.

---

# Versionamiento

Las migraciones seguirán una numeración incremental.

Ejemplos:

V001__initial_schema.sql

V002__security_tables.sql

V003__academic_module.sql

V004__schedule_module.sql

---

# Tipos de Migraciones

## Creación

Creación de nuevas tablas.

Ejemplo:

CREATE TABLE instructor (...);

---

## Modificación

Agregar columnas.

Modificar restricciones.

Crear índices.

---

## Corrección

Corrección de errores estructurales.

---

# Flujo de Migración

1. Diseñar cambio.
2. Revisar impacto.
3. Crear script.
4. Validar localmente.
5. Ejecutar en QA.
6. Aprobar.
7. Ejecutar en producción.

---

# Estrategia de Respaldo

Antes de ejecutar una migración en producción se deberá:

- Crear backup completo.
- Validar restauración.
- Registrar evidencia.

---

# Compatibilidad

Las migraciones deberán ser compatibles con versiones anteriores cuando sea posible.

---

# Rollback

Toda migración crítica deberá incluir estrategia de reversión.

Ejemplo:

DROP COLUMN

DROP TABLE

Eliminación de restricciones.

---

# Ambientes

Las migraciones deberán ejecutarse en el siguiente orden:

Development

↓

QA

↓

Production

---

# Responsabilidades

## Arquitecto

Aprueba cambios estructurales.

---

## DBA

Ejecuta cambios productivos.

---

## Desarrollador

Diseña y prueba migraciones.

---

# Buenas Prácticas

- No modificar datos manualmente.
- No ejecutar scripts sin validación.
- Documentar cada cambio.
- Mantener historial de migraciones.
