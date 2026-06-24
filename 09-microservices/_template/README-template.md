# Nombre del Microservicio

## Objetivo

Describir el objetivo real del servicio dentro del Sistema de Gestion de Horarios SENA.

## Responsabilidades

| Responsabilidad | Descripcion |
| --- | --- |
| Dominio | Capacidad de negocio administrada por el servicio. |
| API | Operaciones REST expuestas. |
| Eventos | Cambios publicados y consumidos. |
| Seguridad | Permisos y validaciones JWT. |

## Diagramas

~~~mermaid
flowchart LR
    A[Entrada] --> B[Reglas de negocio]
    B --> C[Persistencia]
    C --> D[Eventos]
~~~


