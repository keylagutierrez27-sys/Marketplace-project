# 05. Restricciones - UniMarket

| ID | Restricción | Descripción |
|---|---|---|
| RC01 | Presupuesto | El costo operativo mensual no debe superar S/. 100. |
| RC02 | Autenticación institucional | El login debe integrarse con el correo o directorio de la universidad mediante OAuth 2.0 / SSO (Supabase Auth). |
| RC03 | Pagos P2P | Los pagos son directos entre usuarios (Yape, Plin o transferencia). La plataforma no procesa ni retiene fondos. |
| RC04 | Frontend | La web debe ser React / Next.js (PWA) y el móvil React Native. |
| RC05 | Backend | El backend debe ser un monolito modular en Node.js + Express, no microservicios. |
| RC06 | Base de datos | Debe usarse PostgreSQL administrado (Supabase). |
| RC07 | Almacenamiento | Los archivos e imágenes deben ir en Supabase Storage o un servicio compatible con S3. |
| RC08 | Infraestructura perimetral | El dominio debe ser .PE, y DNS, CDN, caché, HTTPS/SSL-TLS y protección WAF/DDoS se gestionan con Cloudflare. |
| RC09 | Inteligencia artificial | El módulo de IA es opcional y debe apoyarse en herramientas gratuitas, de código abierto o con capa gratuita de API. |
| RC10 | API REST | La comunicación entre los clientes (web y móvil) y el backend debe realizarse mediante una API REST. |
| RC11 | Control de versiones | El código y la documentación se versionan con Git en un repositorio compartido. |
