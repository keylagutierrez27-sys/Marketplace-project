# ADR-009: API REST única y versionada

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA10 (API REST)

## Contexto
La web (React / Next.js) y la app móvil (React Native) deben consumir el mismo backend.

## Decisión
Exponer una API REST con JSON sobre HTTPS, versionada bajo `/api/v1`, usada por ambos clientes. La autenticación se valida en un middleware común.

## Alternativas consideradas
- **GraphQL:** más flexible, pero con mayor complejidad para este alcance.
- **APIs separadas para web y móvil:** duplica código y mantenimiento.

## Consecuencias
- (+) Un solo contrato y menos duplicación entre clientes.
- (-) Los cambios de contrato requieren versionado para no romper la app móvil.
