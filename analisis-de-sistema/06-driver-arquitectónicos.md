# Drivers arquitectónicos

| ID | Driver arquitectónico | Origen | ¿Por qué influye en la arquitectura? |
|---|---|---|---|
| DA01 | Presupuesto ultra-bajo de operación. | RC01 | Obliga a usar arquitectura basada en PaaS/capas gratuitas en vez de servidores dedicados. |
| DA02 | Autenticación institucional obligatoria. | RC02, AC01 | Exige un componente de seguridad dedicado (Auth & Security) que valide contra el SSO externo. |
| DA03 | Pagos P2P sin pasarela tradicional. | RC03 | Condiciona el módulo de Orders & Transactions a generar QR/datos y gestionar comprobantes, sin checkout de terceros. |
| DA04 | Escalabilidad para 15,000 usuarios con recursos mínimos. | AC04 | Dirige el diseño hacia un monolito stateless que pueda replicarse horizontalmente detrás de un balanceador. |
| DA05 | Elección de monolito modular sobre microservicios. | RC05, AC05 | Define que las responsabilidades se separen por módulos dentro de una sola unidad desplegable, simplificando despliegue y manteniendo opción de extraer servicios a futuro. |
| DA06 | Infraestructura perimetral centralizada en Cloudflare. | RC08, AC01 | Condiciona que DNS, CDN, caché, HTTPS/SSL-TLS y protección WAF/DDoS se resuelvan en una capa perimetral común antes de llegar a la aplicación. |
| DA07 | Disponibilidad en tiempo real de horarios y notificaciones. | AC03 | Requiere componentes de Booking & Schedule y Notifications bien sincronizados. |
| DA08 | Inteligencia artificial opcional de bajo costo. | RC09 | Condiciona que el componente AI Assistant se integre como servicio desacoplado (ej. Supabase Edge Functions + API externa) en vez de infraestructura de ML propia. |