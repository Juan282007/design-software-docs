# Almacenamiento Documental

## Estrategia

El document-service administra documentos PDF, evidencias, reportes, versiones y objetos de almacenamiento asociados a horarios, auditoria y soporte academico. Los binarios se almacenan en un repositorio de objetos compatible con S3 o almacenamiento institucional equivalente; PostgreSQL conserva metadatos, integridad, versionado y relacion con agregados de negocio.

## Tipos documentales

| Tipo | Origen | Retencion | Trazabilidad |
| --- | --- | --- | --- |
| Horario PDF | scheduling-service | Vigencia academica mas periodo institucional | Version, aprobador, fecha y hash. |
| Evidencia | Usuario autorizado | Segun politica documental del centro | Autor, relacion de negocio y checksum. |
| Reporte operativo | monitoring-service o scheduling-service | Periodo operativo definido por auditoria | Parametros, filtros y usuario solicitante. |
| Soporte de auditoria | audit-service | Retencion extendida | Cadena de integridad y acceso controlado. |

## Flujo documental

~~~mermaid
flowchart TD
    A[Evento ScheduleApproved] --> B[Generar PDF]
    B --> C[Calcular hash SHA-256]
    C --> D[Guardar binario en storage]
    D --> E[Persistir metadatos]
    E --> F[Publicar ReportGenerated]
    F --> G[Registrar AuditLogRecorded]
~~~

## Seguridad

- URLs firmadas con expiracion corta para descarga.
- Validacion JWT y permiso documental antes de servir archivos.
- Cifrado en reposo para objetos sensibles.
- Registro de acceso a documentos criticos.
- Control de versiones sin sobrescribir binarios historicos.


