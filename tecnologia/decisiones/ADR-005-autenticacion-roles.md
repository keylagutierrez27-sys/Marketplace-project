# ADR-005: Autenticación institucional y control de acceso por roles

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA02 (Autenticación institucional)

## Contexto
Solo la comunidad universitaria debe usar UniMarket, con permisos distintos para compradores, proveedores y administradores.

## Decisión
Autenticar con Supabase Auth validando el correo institucional (`@universidad.edu.pe`), usar tokens de sesión y aplicar control de acceso por roles (RBAC) en middlewares de la API. Todo el tráfico va por HTTPS.

## Alternativas consideradas
- **Registro abierto con verificación manual:** riesgo de usuarios externos y carga operativa.
- **Autenticación propia con contraseñas:** más código y más riesgo de seguridad.

## Consecuencias
- (+) Comunidad cerrada y menos código de seguridad propio.
- (-) Dependencia de Supabase Auth y de la disponibilidad del correo institucional.
