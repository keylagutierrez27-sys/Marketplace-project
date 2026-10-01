# 04. Atributos de Calidad (Requisitos No Funcionales) - UniMarket

Este documento define los atributos de calidad (también conocidos como no funcionales o requerimientos de arquitectura) del sistema **UniMarket** en su versión **v2.0**, basados en las normas de calidad de software y en las restricciones del proyecto universitario.

---

## 1. Modificabilidad y Mantenibilidad

### Descripción

Capacidad del sistema para ser modificado de forma eficiente (añadir nuevas características, corregir errores o adaptar el entorno) sin comprometer la estabilidad general.

### Estrategia Arquitectónica

- Se adopta una arquitectura de **monolito modular** basada en principios de **Domain-Driven Design (DDD)**, donde cada módulo (Marketplace, Tutorías, Autenticación, etc.) se encuentra estrictamente separado a nivel de código en directorios independientes.
- El backend utiliza **Fastify / Node.js** con una estructura limpia y desacoplada, lo que permite refactorizar o extraer componentes hacia microservicios en el futuro si la universidad lo requiere, sin necesidad de rediseñar toda la aplicación desde cero.


---


## 2. Escalabilidad

### Descripción

Capacidad del sistema para soportar el crecimiento de la demanda de la comunidad universitaria (hasta **15,000 estudiantes**) manteniendo un rendimiento óptimo.

### Estrategia Arquitectónica

- **Backend Stateless:** El servidor de aplicaciones se diseña sin estado en memoria, permitiendo escalar horizontalmente el monolito modular añadiendo múltiples instancias detrás de un balanceador de carga en la nube cuando la concurrencia aumente.
- **Base de Datos Desacoplada:** La base de datos relacional (**Supabase PostgreSQL Cluster**) opera de forma independiente al servidor de aplicaciones.
- **Capa de Borde (Cloudflare):** El uso de CDN, caché inteligente y distribución global (**Edge Delivery Network**) absorbe la mayor parte del tráfico estático, protegiendo al servidor de origen de sobrecargas innecesarias.

---

## 3. Disponibilidad y Fiabilidad 

## Descripción

Garantía de que la plataforma se encuentre operativa y accesible de manera continua para los estudiantes y administradores.

### Estrategia Arquitectónica

- Uso de servicios en la nube de alta disponibilidad con capas administradas (como **Render/Railway** para el API Cloud y **Supabase** para el cluster de PostgreSQL y Storage).
- Reducción de puntos únicos de fallo mediante la infraestructura redundante de **Cloudflare**, que asegura alta disponibilidad (Uptime) incluso ante fluctuaciones de tráfico o intentos de ataques perimetrales.

---

## 4. Rendimiento y Eficiencia (Performance)

### Descripción

Tiempos de respuesta rápidos y uso eficiente de los recursos computacionales y de red.

### Estrategia Arquitectónica

- **Optimización de Activos:** Compresión y entrega de contenido estático a través de la red de distribución de contenidos (**CDN**) de Cloudflare con políticas de caché agresivas para assets e imágenes.
- **Consultas Eficientes:** Uso de índices optimizados en **PostgreSQL** para las búsquedas y filtrados rápidos en el catálogo de productos y servicios.
- **PWA (Progressive Web App):** El frontend desarrollado en **React / Next.js** está optimizado para ofrecer una carga inicial rápida y una experiencia fluida tanto en navegadores web de escritorio como en dispositivos móviles de gama media/baja.

---

## 5. Seguridad (Security)

### Descripción

Protección de los datos confidenciales de la comunidad universitaria, control de accesos y mitigación de amenazas digitales.

### Estrategia Arquitectónica

- **Cifrado en Tránsito:** Uso obligatorio de **HTTPS** con certificados **SSL/TLS** administrados mediante Cloudflare.
- **Protección Perimetral (WAF):** Implementación de capas de defensa contra ataques DDoS, inyecciones y tráfico malicioso mediante el **Cloudflare Security Layer**.
- **Autenticación Institucional:** Validación estricta de usuarios mediante correo electrónico corporativo (`@universidad.edu.pe`) y tokens de seguridad seguros gestionados por **Supabase Auth**.
- **Control de Acceso Basado en Roles (RBAC):** Restricción de permisos a nivel de API para garantizar que solo los usuarios autorizados (**Comprador, Proveedor o Administrador**) realicen acciones sobre los recursos correspondientes.

---

## 6. Costo y Restricción Presupuestaria (Eficiencia Operativa)

### Descripción

Cumplimiento estricto del presupuesto operativo reducido establecido para el proyecto.

### Estrategia Arquitectónica

- La solución está diseñada para mantenerse estrictamente dentro de un presupuesto máximo de **S/. 100 soles mensuales**, aprovechando las capas gratuitas (**Free Tiers**) y planes económicos de servicios modernos en la nube (**Vercel, Render, Supabase y Cloudflare**), optimizando el dominio `.PE` corporativo sin incurrir en costos de infraestructura empresarial sobredimensionada.