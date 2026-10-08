# ADR-006: Integridad de reservas

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA07 (Reservas sin cruces)

## Contexto
Las reservas de salas y tutorías no pueden cruzarse ni duplicarse, aun con solicitudes simultáneas.

## Decisión
La regla de no cruce vive en el dominio (entidad `Reserva`) y se refuerza en PostgreSQL con transacciones y restricciones de unicidad o exclusión sobre franja horaria y recurso.

## Alternativas consideradas
- **Validar solo en el frontend:** se salta fácilmente y falla con concurrencia.
- **Bloqueos en memoria del servidor:** no funcionan con varias instancias.

## Consecuencias
- (+) Consistencia garantizada con varias instancias del backend.
- (-) Más lógica y pruebas en el módulo Booking & Schedule.
