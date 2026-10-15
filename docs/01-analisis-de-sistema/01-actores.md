# 01 - Actores del Sistema (UniMarket)

En este documento se definen los actores que interactúan con el sistema **UniMarket**, especificando su rol, objetivos y nivel de participación dentro de la plataforma de marketplace universitario.

---

## 1. Estudiante Comprador (`@person`)

* **Descripción:** Es el actor principal que pertenece a la comunidad universitaria y utiliza la plataforma para adquirir bienes o contratar servicios académicos.
* **Tipo:** Actor primario / Humano.
* **Autenticación:** Obligatoria mediante correo institucional (`@universidad.edu.pe`) y contraseña de red.
* **Objetivos y Responsabilidades:**
  * Explorar el catálogo general de productos (libros, artículos usados) y servicios profesionales (tutorías, diseño, programación, impresión).
  * Realizar búsquedas avanzadas y aplicar filtros por categoría, precio y valoración.
  * Enviar solicitudes de compra o reservas de salas de estudio y horarios de tutoría.
  * Efectuar pagos directos Peer-to-Peer (Yape, Plin o transferencias) y cargar el comprobante digital (voucher) en el sistema.
  * Recibir notificaciones push o por correo electrónico sobre el estado de sus pedidos y reservas.

---

## 2. Estudiante Proveedor (`@person`)

* **Descripción:** Estudiante de la comunidad universitaria que oferta bienes o servicios profesionales dentro del marketplace para generar ingresos o intercambiar recursos académicos.
* **Tipo:** Actor primario / Humano.
* **Autenticación:** Obligatoria mediante correo institucional (`@universidad.edu.pe`) y asignación de rol de proveedor.
* **Objetivos y Responsabilidades:**
  * Publicar bienes especificando categoría, estado, precio e imágenes de los productos.
  * Registrar portafolios y tarifas (por hora o por proyecto) para servicios de tutorías, diseño, programación e impresión.
  * Gestionar en tiempo real la disponibilidad de horarios para evitar cruces o duplicidad de citas y reservas.
  * Validar en tiempo real los comprobantes de pago subidos por los compradores y confirmar la entrega del producto o servicio.
  * Visualizar su historial de ventas y reputación dentro de la plataforma.

---

## 3. Administrador (`@person`)

* **Descripción:** Usuario encargado de la supervisión, control y mantenimiento general de la plataforma, asegurando el correcto funcionamiento del marketplace.
* **Tipo:** Actor secundario / Operativo.
* **Autenticación:** Credenciales de acceso con privilegios elevados del sistema.
* **Objetivos y Responsabilidades:**
  * Supervisar la correcta gestión de usuarios, cuentas institucionales y roles.
  * Monitorear el catálogo de publicaciones activas y moderar el contenido.
  * Visualizar reportes estadísticos de ventas, volumen de transacciones e interacciones por facultades o categorías.
  * Gestionar registros de auditoría y generar reportes exportables en formato Excel para la resolución de incidencias o disputas entre usuarios.

---

## 4. Sistemas y Actores Externos (`@software` / Infraestructura)

Además de los usuarios humanos, el sistema interactúa con los siguientes componentes externos descritos en la arquitectura:

* **Servicio de Autenticación Institucional (SSO / OAuth 2.0):** Valida la identidad y pertenencia de los estudiantes a la comunidad universitaria mediante el correo corporativo.
* **Plataforma de Pagos P2P (Yape / Plin / Transferencias Bancarias):** Medios externos de pagos directos utilizados entre los estudiantes, operando sin retención ni procesamiento de fondos por parte de UniMarket.
* **Servicio de Notificaciones (Firebase Cloud Messaging / Correo):** Envía alertas automáticas y correos de confirmación ante cambios de estado en pedidos, ventas o reservas.
* **Capa Perimetral Cloudflare (DNS, HTTPS/SSL-TLS, CDN y WAF):** Protege, enruta y optimiza el tráfico de la plataforma asegurando el cifrado de las comunicaciones.
* **Servicio de Inteligencia Artificial (Asistente Ligero):** Componente opcional basado en APIs o modelos open-source para interpretar consultas en lenguaje natural y sugerir recomendaciones relevantes.