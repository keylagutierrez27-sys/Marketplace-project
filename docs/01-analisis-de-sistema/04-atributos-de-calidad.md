# 04. Atributos de Calidad (Requisitos No Funcionales) - UniMarket

Son siete atributos (requisitos no funcionales). Las metas numéricas se verifican con las pruebas de la sección 4.8 del documento; no se afirma que la plataforma las cumple sin resultados de prueba.

| ID | Atributo | Objetivo / Métrica clave | Estrategia arquitectónica |
| :--- | :--- | :--- | :--- |
| **AC-01** | **Modificabilidad y mantenibilidad** | Mantenimiento desacoplado y posibilidad de extraer módulos en el futuro. | Monolito modular con Domain-Driven Design (DDD) y Clean Architecture. |
| **AC-02** | **Escalabilidad** | Soportar la comunidad objetivo de hasta 15,000 estudiantes; meta de pruebas: 500 usuarios concurrentes, con pruebas de estrés superiores. | API backend *stateless*, PostgreSQL desacoplado, archivos fuera del servidor y caché perimetral para contenido público. |
| **AC-03** | **Disponibilidad y fiabilidad** | Objetivo de disponibilidad mensual del 99.5%. | Plataforma administrada (Vercel, Render, Supabase) con reinicio automático y protección perimetral de Cloudflare. Los planes gratuitos pueden suspender por inactividad, por lo que el objetivo se condiciona a un plan de backend sin suspensión, dentro del presupuesto. |
| **AC-04** | **Rendimiento y eficiencia** | Latencia de la API REST inferior a 300 ms en el 95% de las peticiones y carga de la PWA en menos de 1.5 s. | CDN de Cloudflare para contenido público, índices B-Tree en PostgreSQL, caché de aplicación para consultas públicas y PWA en Next.js. |
| **AC-05** | **Seguridad** | Cifrado de datos en tránsito y protección contra el OWASP Top 10. | TLS 1.3, protección DDoS y reglas WAF básicas de Cloudflare, JWT con correo institucional verificado, RBAC, validación en backend, archivos privados con URL firmada. |
| **AC-06** | **Eficiencia operativa (costo)** | Objetivo de hasta S/ 100 mensuales, sujeto a límites y precios vigentes de los proveedores. | PaaS en capas gratuitas (Vercel, Supabase, Cloudflare), un plan básico de backend si hace falta, dominio `.PE` prorrateado y alertas de consumo. |
| **AC-07** | **Privacidad y protección de datos** | Cumplir la Ley N.º 29733 en datos personales y comprobantes. | Datos mínimos, acceso a *vouchers* solo para las partes de la orden y el administrador autorizado, *bucket* privado, *logs* sin datos bancarios sensibles. |