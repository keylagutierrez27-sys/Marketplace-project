# ADR-002: Clean Architecture dentro de cada módulo

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA05 (Mantenibilidad)

## Contexto
Las reglas de negocio (estados de una orden, reservas sin cruces, validación de comprobantes) no deben depender de Express, PostgreSQL, Supabase ni de servicios externos.

## Decisión
Cada módulo se organiza en cuatro capas: dominio, aplicación, infraestructura y presentación. Las dependencias de código apuntan siempre hacia el dominio, y la infraestructura implementa los puertos que define el dominio.

## Alternativas consideradas
- **MVC simple:** mezcla reglas de negocio con controladores y modelos acoplados al ORM.
- **Capas tradicionales:** la lógica queda acoplada a la base de datos y al framework.

## Consecuencias
- (+) El dominio se prueba sin base de datos ni servicios externos.
- (+) Se puede cambiar un proveedor (almacenamiento, notificaciones, IA) sin tocar las reglas.
- (-) Más carpetas e interfaces al inicio del proyecto.
