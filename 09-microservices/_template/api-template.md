# API REST

## Endpoints

| Verbo HTTP | Ruta | Proposito | Permiso |
| --- | --- | --- | --- |
| GET | /api/v1/recurso | Listar recursos. | DOMAIN_READ |
| POST | /api/v1/recurso | Crear recurso. | DOMAIN_WRITE |

## Validaciones

| Regla | Resultado ante incumplimiento |
| --- | --- |
| JWT valido | 401 |
| Permiso funcional | 403 |
| Regla de negocio | 422 |


