# 03. Requisitos Funcionales - UniMarket

Listado formal de los requerimientos funcionales extraídos de la propuesta técnica del sistema.

---

## 1. Módulo de Gestión de Usuarios y Accesos
* **RF-01:** El sistema validará obligatoriamente que el usuario pertenezca a la comunidad universitaria mediante correo institucional (`Nombre_estudiante@universidad.edu.pe`) y contraseña de red.
* **RF-02:** El sistema asignará permisos y roles diferenciados de manera estricta entre **Estudiante Comprador** y **Estudiante Proveedor**.
* **RF-03:** La interfaz de usuario deberá ser intuitiva, amigable y responsiva, compatible con dispositivos móviles y navegadores web modernos.

## 2. Módulo de Publicación y Catálogo
* **RF-04:** El sistema permitirá a los proveedores publicar bienes (libros, productos usados) especificando categoría, estado de conservación, precio e imágenes mediante el almacenamiento en la nube.
* **RF-05:** El sistema permitirá a los proveedores de servicios (tutorías, diseño, programación, impresión) registrar su portafolio profesional y tarifas estipuladas por hora o por proyecto.
* **RF-06:** El sistema incluirá un mecanismo de búsqueda avanzada y filtrado multicriterio por categoría, rango de precios y valoración de usuarios.

## 3. Módulo de Transacciones y Pagos
* **RF-07:** El sistema integrará un modelo de pagos directos Peer-to-Peer (Yape / Plin / Transferencia bancaria), mostrando los datos o códigos QR del estudiante proveedor en cada transacción para eliminar comisiones de pasarelas intermediarias.
* **RF-08:** El sistema gestionará la trazabilidad del proceso mediante la carga de comprobantes digitales por parte del comprador y la validación/confirmación en tiempo real por el proveedor.
* **RF-09:** El sistema generará constancias virtuales automáticas de transacción para ambas partes involucradas.

## 4. Módulo de Reservas y Horarios
* **RF-10:** El módulo de tutorías y reserva de salas visualizará la disponibilidad de horarios en tiempo real para evitar cruces o duplicidad de citas.
* **RF-11:** El sistema enviará notificaciones y confirmaciones automáticas de reserva de salas y citas de tutoría.

## 5. Módulo de Administración e Informes
* **RF-12:** El administrador general visualizará reportes estadísticos consolidados de ventas, cantidad de publicaciones activas y volumen de transacciones segmentadas por facultades o categorías.
* **RF-13:** El sistema mantendrá registros de auditoría y generará reportes exportables en formato Excel sobre incidencias y disputas entre usuarios.

---

## Relación entre Historias de Usuario (HU) y Requisitos Funcionales (RF)

| Historia de Usuario | Descripción breve | Requisitos Funcionales Asociados |
| :--- | :--- | :--- |
| **HU-01** | Autenticación Institucional | RF-01, RF-02, RF-03 |
| **HU-02** | Publicación de Productos Usados | RF-04, RF-06 |
| **HU-03** | Publicación de Servicios Profesionales | RF-05, RF-06 |
| **HU-04** | Búsqueda Avanzada y Filtros | RF-06 |
| **HU-05** | Pago Directo Peer-to-Peer y Comprobante | RF-07, RF-08, RF-09 |
| **HU-06** | Reserva de Salas y Tutorías en Tiempo Real | RF-10, RF-11 |