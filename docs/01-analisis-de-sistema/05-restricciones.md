# 05. Restricciones - UniMarket

Condicionan el diseño y la implementación; cada una tiene un impacto directo en la arquitectura.

| ID | Categoría | Restricción | Impacto en la arquitectura |
| :--- | :--- | :--- | :--- |
| **RC01** | Financiera | El costo operativo mensual de infraestructura no debe superar S/ 100 como objetivo. | Obliga a usar capas gratuitas y a elegir un solo proveedor por capa de despliegue, con alertas de consumo. |
| **RC02** | Seguridad / dominio | Acceso exclusivo a miembros de la universidad mediante correo institucional verificado con Supabase Auth. | Validación obligatoria del dominio institucional y emisión de JWT. SSO/OAuth solo con proveedor, autorización y documentación técnica de la universidad. |
| **RC03** | Negocio / legal | Transacciones directas Peer-to-Peer (Yape, Plin o transferencia). | La plataforma no procesa, captura ni retiene fondos; opera con comprobantes y confirmación manual del proveedor. |
| **RC04** | Tecnológica | Web en Next.js (PWA, responsive); app móvil en React Native como cliente previsto de la misma API. | Un único ecosistema JavaScript/TypeScript; la app móvil puede diferirse si el plazo es corto. |
| **RC05** | Arquitectura | Backend como monolito modular en Node.js con Express y TypeScript (Fastify descartado para mantener un solo framework). | Prohíbe dividir en microservicios al inicio; separación por carpetas de dominio (DDD). |
| **RC06** | Tecnológica | Persistencia en PostgreSQL administrado (Supabase). | Consistencia transaccional ACID para usuarios, catálogo, órdenes, reservas y auditoría. |
| **RC07** | Tecnológica / Infraestructura | Imágenes y comprobantes en Supabase Storage (base); Cloudinary solo como alternativa justificada para optimizar imágenes públicas. | Desacopla los archivos del servidor y mantiene privados los vouchers. |
| **RC08** | Tecnológica | Dominio `.PE` con DNS, HTTPS/SSL, CDN, caché y protección perimetral en Cloudflare. | Delega a Cloudflare la resolución DNS, el enrutamiento y la caché de contenido público. Funciones de pago (Argo, Load Balancing) quedan fuera del presupuesto base. |
| **RC09** | Tecnológica | IA opcional, con servicios gratuitos o modelos de código abierto, sujeta a límites vigentes. | El sistema funciona sin IA; el proveedor se integra tras una interfaz intercambiable y con límites de consumo. |
| **RC10** | Integración | Comunicación cliente-servidor mediante API REST en JSON, versionada bajo `/api/v1`. | Contrato estándar de endpoints con autenticación Bearer en todas las peticiones privadas. |
| **RC11** | Operativa | Código, documentación y esquemas C4 versionados con Git en un repositorio compartido. | Trazabilidad del código, integración continua y mantenimiento colaborativo. |
| **RC12** | Legal | Cumplimiento de la Ley N.º 29733 de protección de datos personales. | Datos mínimos, consentimiento y política de privacidad, acceso restringido a vouchers y eliminación o anonimización a solicitud. |
| **RC13** | Despliegue | Una combinación concreta: Vercel (frontend), Render (backend; Railway como alternativa) y Supabase (base de datos y archivos). | Evita leer los proveedores alternativos como si se contrataran todos a la vez; se revalida contra límites vigentes antes de publicar. |