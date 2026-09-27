# Drivers arquitectónicos

| ID | Driver arquitectónico | Origen | ¿Por qué influye en la arquitectura? |
|---|---|---|---|
| DA01 | Presupuesto ultra-bajo de operación. | RC01 – Presupuesto | Obliga a usar arquitectura serverless/PaaS con capas gratuitas en vez de servidores dedicados. |
| DA02 | Autenticación institucional obligatoria. | RC02, AC01 | Exige un componente de seguridad dedicado que valide contra el SSO externo. |
| DA03 | Pagos P2P sin pasarela tradicional. | RC03 | Condiciona el módulo de transacciones a generar QR/datos y gestionar comprobantes, en vez de integrar un checkout de terceros. |
| DA04 | Escalabilidad para 15,000 usuarios con recursos mínimos. | AC04 | Dirige el uso de contenedores ligeros, CDN y base de datos gestionada. |
| DA05 | Disponibilidad en tiempo real de horarios y notificaciones. | AC03 | Requiere componentes de Reservas y Notificaciones separados y bien sincronizados. |