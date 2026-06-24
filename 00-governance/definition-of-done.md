# Definition of Done (DoD)

## Propósito

La Definition of Done (DoD) establece los criterios obligatorios que debe cumplir cualquier desarrollo, mejora, corrección o entregable antes de considerarse finalizado y apto para ser integrado al proyecto Horarios SENA.

El objetivo principal es garantizar la calidad, trazabilidad, mantenibilidad y consistencia de todos los artefactos generados durante el ciclo de vida del software.

---

# Alcance

Esta definición aplica a:

* Historias de usuario.
* Corrección de errores.
* Nuevos módulos.
* APIs.
* Microservicios.
* Componentes Frontend.
* Scripts de base de datos.
* Documentación técnica.
* Diagramas UML.

---

# Criterios de Desarrollo

Todo desarrollo deberá cumplir los siguientes requisitos:

## Calidad de código

* El código debe compilar correctamente.
* No debe contener errores de sintaxis.
* Debe seguir las convenciones establecidas por el proyecto.
* Debe mantener principios de código limpio.
* Debe evitar duplicación innecesaria.

## Arquitectura

* Debe respetar la arquitectura definida.
* No debe romper dependencias existentes.
* Debe cumplir la separación de responsabilidades.

## Seguridad

* No se deben almacenar contraseñas en texto plano.
* Las credenciales deben gestionarse mediante variables de entorno.
* Deben aplicarse controles de acceso adecuados.

---

# Criterios Funcionales

* Cumplir los criterios de aceptación.
* Resolver completamente el requerimiento.
* Cubrir escenarios normales y excepcionales.
* Validar restricciones de negocio.

---

# Criterios de Pruebas

Antes de finalizar una tarea deben realizarse:

## Pruebas Funcionales

* Validación de funcionalidades.
* Validación de formularios.
* Validación de reglas de negocio.

## Pruebas de Integración

* Verificar interacción entre módulos.
* Validar respuestas de APIs.

## Pruebas Manuales

* Flujo completo del caso de uso.
* Casos positivos y negativos.

---

# Criterios de Documentación

Todo cambio debe reflejarse en la documentación correspondiente:

* Diagramas actualizados.
* Requisitos actualizados.
* Modelos de datos actualizados.
* APIs documentadas.

---

# Criterios de Integración

Antes de realizar merge:

* Pull Request creado.
* Revisión aprobada.
* Conflictos resueltos.
* Validaciones completadas.

---

# Checklist Final

* [ ] Desarrollo completado
* [ ] Requisitos cumplidos
* [ ] Pruebas realizadas
* [ ] Documentación actualizada
* [ ] Revisión aprobada
* [ ] Integración realizada
