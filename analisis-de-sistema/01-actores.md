# Actores y Perfiles del Sistema - UniMarket

Este documento define los actores del sistema de acuerdo con la arquitectura propuesta en el proyecto **UniMarket** (Marketplace de servicios y productos universitarios).

---

## 1. Actores Principales (Usuarios del Sistema)

### 1.1. Estudiante Comprador
* **Descripción:** Estudiante perteneciente a la comunidad universitaria que utiliza la plataforma web o móvil para adquirir bienes o contratar servicios académicos dentro del campus.
* **Responsabilidades y Acciones:**
  * Iniciar sesión mediante autenticación institucional de red (`nombre_estudiante@unsch.edu.pe`).
  * Buscar y filtrar productos (libros, artículos usados) y servicios (tutorías, diseño, programación, impresión) mediante búsqueda avanzada.
  * Realizar compras, reservas de salas de estudio o agendamiento de citas de tutoría.
  * Realizar pagos directos mediante transferencias o billeteras digitales (Yape/Plin) cargando su comprobante digital.
  * Evaluar y calificar a los estudiantes proveedores tras recibir el producto o servicio.

### 1.2. Estudiante Proveedor
* **Descripción:** Estudiante universitario que ofrece bienes tangibles o servicios profesionales especializados a la comunidad estudiantil a través de la plataforma.
* **Responsabilidades y Acciones:**
  * Registrar y gestionar su portafolio de servicios (tarifas por hora o proyecto) o catálogo de productos (categoría, estado, precio e imágenes).
  * Administrar la disponibilidad de horarios en tiempo real para tutorías o reserva de salas.
  * Validar comprobantes de pago digitales y confirmar transacciones en tiempo real.
  * Gestionar el ciclo de vida de sus ventas y entregas.

---

## 2. Actores de Administración

### 2.1. Administrador General
* **Descripción:** Personal designado por la institución universitaria o encargado del sistema para la supervisión global de la plataforma.
* **Responsabilidades y Acciones:**
  * Visualizar reportes estadísticos de ventas, cantidad de publicaciones activas y volumen de transacciones por facultades o categorías.
  * Consultar registros de auditoría y generar reportes exportables en formato Excel sobre incidencias o disputas entre usuarios.

---

## 3. Sistemas Externos (Actores de Integración)

### 3.1. Sistema de Autenticación Institucional (SSO / OAuth 2.0)
* **Descripción:** Servicio externo de la universidad que valida las credenciales corporativas y el correo institucional de los estudiantes.

### 3.2. Pasarela de Pagos (Yape / Plin / Transferencia Directa)
* **Descripción:** Mecanismo de pagos Peer-to-Peer que procesa y muestra los datos o códigos QR del estudiante proveedor para eliminar intermediarios.

### 3.3. Servicio de Notificaciones Externo (Firebase / Correo)
* **Descripción:** Mecanismo que despacha alertas push y correos de confirmación ante cambios de estado en compras, pedidos y reservas.