# ADR-003: Estrategia de caché en dos niveles

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA09 (Rendimiento), DA06 (Infraestructura perimetral)

## Contexto
El catálogo y la búsqueda concentrarán la mayoría de las lecturas, con alta concurrencia, y el backend debe mantenerse stateless.

## Decisión
1. **Borde:** CDN y caché de Cloudflare para imágenes y contenido estático.
2. **Backend:** caché de consultas frecuentes del catálogo (categorías, listados populares) con TTL corto, sin guardar estado de negocio en la memoria de una instancia.
3. **Base de datos:** índices en PostgreSQL para búsqueda y filtros.

## Alternativas consideradas
- **Consultar siempre a PostgreSQL:** más latencia y carga en la capa gratuita.
- **Solo índices y paginación:** insuficiente ante picos de campañas.

## Consecuencias
- (+) Menor carga al origen y a la base de datos, y respuestas más rápidas.
- (-) Datos que pueden quedar desactualizados unos segundos o minutos.
- (-) Hay que definir cuándo se invalida la caché (al publicar o editar una publicación).
