# Persistencia - Monitoring Service

## Estrategia de persistencia

El servicio usa PostgreSQL en la base logica . Cada tabla incluye id UUID, status, created_at, updated_at, created_by, updated_by y version para auditoria y control optimista. No se comparten tablas con otros microservicios.

## Modelo logico

| Tabla | Entidad | Proposito |
| --- | --- | --- |
| tabla | HealthSnapshot | Persistir informacion principal de observabilidad operativa. |
| tabla | MetricSample | Persistir informacion principal de observabilidad operativa. |
| tabla | TraceSummary | Persistir informacion principal de observabilidad operativa. |
| tabla | AlertRule | Persistir informacion principal de observabilidad operativa. |
| tabla | IncidentSignal | Persistir informacion principal de observabilidad operativa. |
| tabla | ServiceDependency | Persistir informacion principal de observabilidad operativa. |
| outbox_event | Evento de salida | Garantizar publicacion confiable posterior al commit. |
| inbox_event | Evento de entrada | Controlar idempotencia de eventos consumidos. |

## Indices recomendados PostgreSQL

| Indice | Tabla | Columnas | Uso |
| --- | --- | --- | --- |
| idx_h_ea_lt_hs_na_ps_ho_t_status | tabla | status | Filtros operativos por estado. |
| idx_h_ea_lt_hs_na_ps_ho_t_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
| idx_m_et_ri_cs_am_pl_e_status | tabla | status | Filtros operativos por estado. |
| idx_m_et_ri_cs_am_pl_e_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
| idx_t_ra_ce_su_mm_ar_y_status | tabla | status | Filtros operativos por estado. |
| idx_t_ra_ce_su_mm_ar_y_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
| idx_a_le_rt_ru_le_status | tabla | status | Filtros operativos por estado. |
| idx_a_le_rt_ru_le_code_unique | tabla | code | Busqueda exacta y unicidad funcional. |
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


