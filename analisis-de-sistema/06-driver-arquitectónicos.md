# 06. Drivers arquitectónicos - UniMarket


| ID | Driver arquitectónico | Origen | ¿Por qué influye en la arquitectura? |
|---|---|---|---|
| DA01 | El sistema debe operar con un presupuesto máximo de S/. 100 mensuales. | RC01, AC06 | Obliga a usar servicios PaaS con capa gratuita y un solo despliegue en vez de servidores dedicados. |
| DA02 | El sistema debe permitir el acceso solo a la comunidad universitaria mediante autenticación institucional. | RC02, AC01 | Exige un módulo de Auth & Security que valide contra Supabase Auth / SSO y aplique roles. |
| DA03 | El sistema debe soportar pagos P2P sin pasarela tradicional. | RC03 | Condiciona al módulo Orders & Transactions a mostrar datos o QR del proveedor y a gestionar comprobantes y constancias, sin checkout de terceros. |
| DA04 | El sistema debe escalar para 15,000 usuarios con recursos mínimos. | AC04 | Dirige el diseño hacia un backend stateless que pueda replicarse horizontalmente. |
| DA05 | El sistema debe permitir modificar funcionalidades sin afectar innecesariamente otros módulos. | AC05 | Influye en la separación de responsabilidades, la modularidad y las dependencias internas. |
| DA06 | El sistema debe usar dominio .PE, DNS, HTTPS/SSL-TLS, CDN, caché y protección WAF/DDoS mediante Cloudflare. | RC08, AC01, AC03 | Condiciona que estas funciones se resuelvan en una capa perimetral común antes de llegar a la aplicación. |
| DA07 | El sistema debe mostrar la disponibilidad de horarios en tiempo real sin permitir reservas cruzadas ni duplicadas. | RF-08 | Obliga a ubicar la regla de reservas en el dominio y reforzarla con transacciones y restricciones en PostgreSQL. |
| DA08 | El sistema debe permitir un asistente de IA opcional de bajo costo (prioridad baja). | RC09 | Condiciona que el AI Assistant sea un servicio desacoplado, sin infraestructura de ML propia. |
| DA09 | El sistema debe mantener tiempos de respuesta adecuados con alta concurrencia. | AC02 | Influye en la estrategia de caché, los índices y la comunicación entre componentes. |
| DA10 | Web y móvil deben consumir el mismo backend mediante una API REST. | RC04, RC10 | Obliga a separar interfaz y backend con una API única y versionada. |

## Drivers y decisiones que responden

| Driver | Problema que plantea | Decisión que responde |
|---|---|---|
| DA01 - Presupuesto | Costo máximo de S/. 100 mensuales | Servicios PaaS con capa gratuita y un solo despliegue (ADR-007, ADR-001) |
| DA02 - Autenticación institucional | Solo la comunidad universitaria debe acceder | Supabase Auth con correo institucional y RBAC (ADR-005) |
| DA03 - Pagos P2P | No hay pasarela, pero se necesita trazabilidad | Flujo con comprobante y confirmación, usando puertos y adaptadores (ADR-004) |
| DA04 - Escalabilidad | Hasta 15,000 usuarios con picos | Monolito modular stateless con escalamiento horizontal (ADR-001) |
| DA05 - Mantenibilidad | Los cambios no deben afectar otros módulos | Modularidad + Clean Architecture por módulo (ADR-001, ADR-002) |
| DA06 - Infraestructura perimetral | DNS, HTTPS, CDN, caché y WAF centralizados | Cloudflare como capa de borde (ADR-007, ADR-003) |
| DA07 - Integridad de reservas | Reservas cruzadas o duplicadas | Regla en el dominio y restricciones en PostgreSQL (ADR-006) |
| DA08 - IA opcional | IA sin costo ni infraestructura propia | Servicio de IA desacoplado detrás de un puerto (ADR-008) |
| DA09 - Rendimiento | Alta concurrencia en búsqueda y catálogo | Caché en dos niveles e índices (ADR-003) |
| DA10 - API REST | Web y móvil comparten backend | API REST única y versionada (ADR-009) |
