# 07. Decisiones arquitectónicas - UniMarket


| ID | Decisión arquitectónica | Driver relacionado | Justificación | Resultado |
|---|---|---|---|---|
| ADR-001 | Monolito modular | DA01, DA04, DA05 | Organizar las funcionalidades en módulos independientes dentro de una sola aplicación desplegable y escalable horizontalmente. | Módulos Auth & Security, Users, Catalog, Search, Orders, Booking, Notifications, Administration y AI Assistant. |
| ADR-002 | Clean Architecture dentro de cada módulo | DA05 | Separar las reglas de negocio de los detalles tecnológicos. | Dominio, Aplicación, Infraestructura y Presentación por módulo. |
| ADR-003 | Estrategia de caché en dos niveles | DA09, DA06 | Reducir consultas repetitivas y carga al origen. | CDN y caché de Cloudflare, caché de consultas frecuentes e índices. |
| ADR-004 | Pagos P2P con puertos y adaptadores | DA03 | Dar trazabilidad sin procesar fondos y desacoplar el dominio de los proveedores. | Flujo orden, comprobante, confirmación y constancia, con puertos de almacenamiento y notificación. |
| ADR-005 | Autenticación institucional y RBAC | DA02 | Restringir el acceso a la comunidad universitaria y controlar permisos por rol. | Supabase Auth con correo institucional y autorización en la API. |
| ADR-006 | Integridad de reservas | DA07 | Evitar reservas cruzadas con solicitudes simultáneas. | Regla en el dominio y restricciones y transacciones en PostgreSQL. |
| ADR-007 | Cloudflare y servicios PaaS de capa gratuita | DA01, DA06 | Cumplir el presupuesto y centralizar la capa perimetral. | Cloudflare, Vercel, Render o Railway, y Supabase. |
| ADR-008 | IA como servicio desacoplado | DA08 | Que el asistente sea opcional y no afecte al núcleo. | Puerto AsistenteBusqueda con adaptador a una API externa o de código abierto. |
| ADR-009 | API REST única y versionada | DA10 | Que web y móvil consuman el mismo backend. | Endpoints bajo `/api/v1` con JSON sobre HTTPS. |
