# Persistencia - Training Environment Service

## Estrategia de persistencia

El servicio usa PostgreSQL en la base logica . Cada tabla incluye id UUID, status, created_at, updated_at, created_by, updated_by y version para auditoria y control optimista. No se comparten tablas con otros microservicios.

## Modelo logico

| Tabla | Entidad | Proposito |
| --- | --- | --- |
| tabla | Environment | Persistir informacion principal de ambientes de formacion. |
| tabla | Building | Persistir informacion principal de ambientes de formacion. |
| tabla | Campus | Persistir informacion principal de ambientes de formacion. |
| tabla | Resource | Persistir informacion principal de ambientes de formacion. |
| tabla | EnvironmentAvailability | Persistir informacion principal de ambientes de formacion. |
| tabla | MaintenanceWindow | Persistir informacion principal de ambientes de formacion. |
| outbox_event | Evento de salida | Garantizar publicacion confiable posterior al commit. |
| inbox_event | Evento de entrada | Controlar idempotencia de eventos consumidos. |

## Indices recomendados PostgreSQL

| Indice | Tabla | Columnas | Uso |
| --- | --- | --- | --- |
| idx_e_nv_ir_on_me_nt_status | tabla | status | Filtros operativos por estado. |
| idx_e_nv_ir_on_me_nt_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
| idx_b_ui_ld_in_g_status | tabla | status | Filtros operativos por estado. |
| idx_b_ui_ld_in_g_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
| idx_c_am_pu_s_status | tabla | status | Filtros operativos por estado. |
| idx_c_am_pu_s_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
| idx_r_es_ou_rc_e_status | tabla | status | Filtros operativos por estado. |
| idx_r_es_ou_rc_e_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
| idx_outbox_pending | outbox_event | status, created_at | Publicacion ordenada de eventos por publicar. |
| idx_inbox_event_id | inbox_event | event_id | Idempotencia en consumidores. |

## Relaciones internas

~~~mermaid
erDiagram
    PRINCIPAL ||--o{ DETALLE : contiene
    PRINCIPAL ||--o{ OUTBOX_EVENT : publica
    INBOX_EVENT ||--o{ PRINCIPAL : actualiza_contexto
    PRINCIPAL {
        uuid id
        string code
        string status
        int version
        timestamp created_at
    }
    DETALLE {
        uuid id
        uuid principal_id
        string description
        string status
    }
    OUTBOX_EVENT {
        uuid event_id
        string event_type
        jsonb payload
        string status
    }
    INBOX_EVENT {
        uuid event_id
        string source_service
        timestamp processed_at
    }
~~~

## Politicas de datos

- Eliminacion logica para informacion academica, documental, de seguridad y auditoria.
- Migraciones con Flyway en cada servicio.
- Campos sensibles cifrados o enmascarados en logs.
- jsonb reservado para metadatos variables, sin reemplazar entidades principales.


