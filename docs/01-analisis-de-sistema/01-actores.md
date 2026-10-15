# 01 - Actores del Sistema (UniMarket)

En este documento se definen los actores que interactúan con el sistema **UniMarket**, especificando su rol, objetivos y nivel de participación dentro de la plataforma de marketplace universitario.

---


## 1.1 Actores del Sistema

| Actor | Tipo | Autenticación | Objetivos | Operaciones principales |
| :--- | :--- | :--- | :--- | :--- |
| **Estudiante Comprador** | Primario, humano | Correo institucional verificado (`@unsch.edu.pe` vía Supabase Auth) con token JWT. | Adquirir productos y contratar servicios o asesorías de la comunidad universitaria. | Explorar el catálogo con filtros por facultad, precio y estado; buscar en lenguaje natural (opcional); crear órdenes y reservar tutorías o salas; ver datos de pago P2P y adjuntar el voucher; confirmar la recepción; calificar al proveedor; reportar incidencias. |
| **Estudiante Proveedor** | Primario, humano | Correo institucional verificado + perfil de proveedor activado con su medio de pago P2P. | Ofertar bienes o servicios para monetizar sus habilidades dentro del campus. | Publicar productos con imágenes, precio, stock y estado (Nuevo/Usado); gestionar portafolio y tarifas; configurar su disponibilidad horaria; revisar vouchers y confirmar o rechazar el pago; consultar historial de ventas y reputación. |
| **Administrador** | Secundario, operativo | Credenciales con permisos elevados (RBAC) + doble factor (2FA). | Supervisar, moderar y mantener el marketplace. | Gestionar usuarios y roles; suspender cuentas fraudulentas o ficticias; moderar publicaciones; ver reportes estadísticos; atender incidencias; auditar logs y exportar reportes en Excel; administrar las salas de estudio reservables. |

> **Nota:** Un estudiante tiene siempre el rol **Comprador**; al completar su perfil de proveedor (medio de pago P2P y datos de contacto) obtiene además el rol **Proveedor**. El administrador puede suspender cualquiera de los dos roles.

---

## 1.2 Sistemas y Componentes Externos (`@software` / Infraestructura)

| Componente | Tipo | Función | Integración con UniMarket |
| :--- | :--- | :--- | :--- |
| **Autenticación institucional (Supabase Auth)** | Sistema externo | Validar la identidad universitaria. | Acepta solo correos del dominio institucional (`@unsch.edu.pe`), verificados por enlace o código. SSO/OAuth se añade solo si la universidad lo autoriza y documenta. |
| **Medios de pago P2P (Yape, Plin, transferencia)** | Servicio financiero externo | Transferir dinero directamente entre estudiantes. | Sin integración por API ni custodia de fondos: el comprador paga fuera de UniMarket y sube el voucher. |
| **Servicio de notificaciones (correo/SMTP y push)** | Infraestructura | Enviar alertas automáticas. | Despacha correos transaccionales y push ante cambios en órdenes o reservas. |
| **Cloudflare** | Infraestructura | DNS, HTTPS/TLS, CDN, caché de contenido público y protección perimetral. | Gestiona el dominio `.PE` y protege/entrega el tráfico; no sustituye la autenticación del backend. |
| **Supabase (PostgreSQL y Storage)** | Infraestructura | Persistencia transaccional y archivos privados. | Base de datos relacional y almacenamiento privado/público de imágenes y comprobantes. |
| **Proveedor de IA (opcional)** | Servicio externo | Procesar lenguaje natural. | Se consume tras un adaptador (`AIProviderPort`); el sistema funciona completamente sin él. |