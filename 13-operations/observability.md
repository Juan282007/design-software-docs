# Observability

## Objetivo

Definir la estrategia de monitoreo y observabilidad para garantizar la estabilidad operativa del Sistema de Gestión de Horarios SENA.

---

# Concepto

La observabilidad permite comprender el comportamiento interno del sistema mediante:

- Logs.
- Métricas.
- Trazas.

---

# Componentes

## Logging

Todos los servicios deberán generar registros estructurados.

Información mínima:

- Fecha.
- Servicio.
- Usuario.
- Operación.
- Resultado.

---

# Niveles de Log

## INFO

Eventos normales.

Ejemplo:

Inicio de sesión exitoso.

---

## WARN

Situaciones inesperadas.

Ejemplo:

Intento de acceso inválido.

---

## ERROR

Fallos que afectan el funcionamiento.

Ejemplo:

Error de conexión.

---

## DEBUG

Información detallada para desarrollo.

---

# Métricas

Se monitorearán:

- Uso de CPU.
- Uso de memoria.
- Tiempo de respuesta.
- Número de solicitudes.
- Errores por minuto.

---

# Indicadores

## Disponibilidad

Meta:

99%

---

## Tiempo de Respuesta

Meta:

Menor a 3 segundos.

---

## Tasa de Error

Meta:

Menor al 2%.

---

# Alertas

Se generarán alertas automáticas cuando:

- Un servicio deje de responder.
- Se excedan tiempos de respuesta.
- Se detecten errores masivos.

---

# Herramientas

Herramientas recomendadas:

- Prometheus
- Grafana
- ELK Stack

---

# Trazabilidad

Toda solicitud deberá poder rastrearse entre:

- Frontend.
- API Gateway.
- Microservicios.
- Base de datos.

---

# Beneficios

- Identificación temprana de fallos.
- Mejor rendimiento.
- Mayor disponibilidad.
- Mejor experiencia de usuario.
