# Backup and Recovery

## Objetivo

Definir las estrategias de respaldo y recuperación del Sistema de Gestión de Horarios SENA para garantizar la disponibilidad, integridad y continuidad de la información ante incidentes operativos o fallos tecnológicos.

---

# Alcance

Este documento aplica a:

- Bases de datos.
- Configuraciones de microservicios.
- Archivos de despliegue.
- Configuraciones de infraestructura.
- Documentación crítica.

---

# Política de Respaldo

Todo componente crítico deberá contar con mecanismos de respaldo programados.

Objetivos:

- Evitar pérdida de información.
- Reducir tiempos de recuperación.
- Garantizar continuidad operativa.

---

# Tipos de Backup

## Backup Completo

Contiene toda la información del sistema.

Frecuencia:

- Semanal.

Ventajas:

- Recuperación sencilla.
- Mayor integridad.

Desventajas:

- Mayor espacio requerido.

---

## Backup Incremental

Respalda únicamente cambios realizados desde el último respaldo.

Frecuencia:

- Diaria.

Ventajas:

- Menor espacio.
- Mayor velocidad.

---

# Bases de Datos

Motor:

PostgreSQL

Elementos respaldados:

- Esquema.
- Datos.
- Procedimientos.
- Funciones.
- Índices.

---

# Almacenamiento

Los respaldos deberán almacenarse en:

- Servidor principal.
- Almacenamiento externo.
- Repositorio seguro.

---

# Retención

Respaldos diarios:

30 días.

Respaldos semanales:

3 meses.

Respaldos mensuales:

1 año.

---

# Recuperación

## Escenario 1

Recuperación de registros específicos.

Procedimiento:

1. Identificar respaldo.
2. Restaurar entorno temporal.
3. Extraer información.
4. Validar integridad.

---

## Escenario 2

Recuperación total del sistema.

Procedimiento:

1. Detener servicios.
2. Restaurar base de datos.
3. Restaurar configuraciones.
4. Reiniciar servicios.
5. Validar funcionamiento.

---

# Responsabilidades

Administrador de Base de Datos

- Ejecutar respaldos.
- Verificar restauraciones.

Equipo DevOps

- Mantener infraestructura.

Arquitecto

- Aprobar estrategias de recuperación.

---

# Validación

Se deberán realizar pruebas de restauración al menos una vez por trimestre.
