# 06. Drivers arquitectónicos - UniMarket

Los drivers son los factores que dirigen el diseño. Cada uno cita su origen (restricción RC, atributo AC o requisito RF) y la decisión ADR que lo resuelve.

| ID | Driver | Origen | Por qué influye en la arquitectura | ADR que lo resuelve |
| :--- | :--- | :--- | :--- | :--- |
| **DA01** | Costo máximo de S/ 100 mensuales | RC01, AC-06 | Obliga a servicios PaaS en capa gratuita y a un solo despliegue centralizado, no a servidores dedicados. | ADR-001, ADR-007 |
| **DA02** | Acceso exclusivo de la comunidad universitaria | RC02, AC-05 | Exige un módulo de autenticación que valide el dominio institucional con Supabase Auth y aplique RBAC. | ADR-005 |
| **DA03** | Pagos directos P2P sin pasarela bancaria | RC03, AC-05 | El módulo orders muestra datos y QR del proveedor y gestiona comprobantes y constancias, sin checkout de terceros. | ADR-004 |
| **DA04** | Escalabilidad para una comunidad de 15,000 estudiantes con cómputo mínimo | AC-02, AC-04 | Lleva a un backend stateless que pueda replicarse horizontalmente donde el plan hosting lo permita. | ADR-001 |
| **DA05** | Modificabilidad: cambiar un módulo sin afectar otros | AC-01 | Separa responsabilidades con monolito modular y Clean Architecture. | ADR-001, ADR-002 |
| **DA06** | Dominio .PE, DNS, HTTPS, CDN, caché y protección perimetral | RC08, AC-03, AC-05 | Estas funciones se resuelven en Cloudflare antes de llegar al servidor de aplicación. | ADR-003, ADR-007 |
| **DA07** | Horarios en tiempo real sin reservas cruzadas ni duplicadas | RF-08, AC-02 | Las reglas de agenda viven en el dominio (booking) y se refuerzan con restricciones transaccionales en PostgreSQL. | ADR-006 |
| **DA08** | Asistente de IA opcional, desacoplado y de bajo costo | RC09, AC-06 | `ai-assistant` es una capacidad interna de Search & AI, consumida tras un puerto, sin infraestructura de ML propia. | ADR-008 |
| **DA09** | Respuestas rápidas con alta concurrencia | AC-04, AC-02 | Caché en dos niveles (CDN + aplicación) para contenido público e índices en la base de datos. | ADR-003 |
| **DA10** | Clientes web y móvil sobre el mismo backend | RC04, RC10 | Una única API REST versionada en JSON, desacoplada de la interfaz. | ADR-009 |
| **DA11** | Protección de datos personales y comprobantes | RC12, AC-07 | Los vouchers son datos sensibles: archivos privados, acceso por propiedad de la orden y logs sin datos bancarios. | ADR-010 |