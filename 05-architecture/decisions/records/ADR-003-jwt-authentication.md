# ADR-003

## Título

Autenticación mediante JWT.

## Estado

Aceptado

## Contexto

Los microservicios requieren autenticación desacoplada.

## Decisión

Implementar JWT.

## Consecuencias

### Positivas

- Stateless.
- Escalable.
- Compatible con APIs.

### Negativas

- Gestión de expiración.