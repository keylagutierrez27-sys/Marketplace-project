# Restricciones

| ID | Restricción | Descripción |
|---|---|---|
| RC01 | Presupuesto | El costo operativo mensual no debe superar S/. 100 soles. |
| RC02 | Autenticación institucional | El login debe integrarse con el correo/directorio de la universidad vía OAuth 2.0 / SSO (Supabase Auth). |
| RC03 | Pagos P2P | Los pagos deben ser directos entre usuarios (Yape/Plin/transferencia); la plataforma no procesa ni retiene fondos. |
| RC04 | Frontend | La web debe ser React/Next.js (PWA) y el móvil React Native. |
| RC05 | Backend | El backend debe implementarse como un monolito modular (Node.js/Express o Fastify como API Gateway), no como microservicios. |
| RC06 | Base de datos | Debe usarse PostgreSQL administrado (Supabase). |
| RC07 | Almacenamiento | Los archivos e imágenes deben ir en Supabase Storage o un servicio compatible con S3. |
| RC08 | Infraestructura perimetral | El dominio debe ser .PE y la resolución DNS, CDN, caché y HTTPS/SSL-TLS deben gestionarse mediante Cloudflare. |
| RC09 | Inteligencia artificial | El módulo de IA es opcional y debe apoyarse en herramientas gratuitas o de código abierto (o capa gratuita de API externa). |