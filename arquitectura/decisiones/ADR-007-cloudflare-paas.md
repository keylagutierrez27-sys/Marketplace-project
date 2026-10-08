# ADR-007: Cloudflare y servicios PaaS de capa gratuita

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA01 (Presupuesto), DA06 (Infraestructura perimetral)

## Contexto
El presupuesto máximo es S/. 100 mensuales y se requiere dominio .PE, HTTPS, CDN, caché y protección WAF/DDoS.

## Decisión
Cloudflare como capa perimetral (DNS, SSL/TLS, CDN, caché, WAF). Frontend en Vercel, backend en Render o Railway, y Supabase para PostgreSQL y Storage, usando capas gratuitas o económicas.

## Alternativas consideradas
- **Servidores dedicados o VPS propios:** más costo y mantenimiento.
- **Nube pública con servicios gestionados completos:** exceden el presupuesto.

## Consecuencias
- (+) Costo dentro del presupuesto y menos administración de infraestructura.
- (-) Dependencia de proveedores y de los límites de las capas gratuitas.
