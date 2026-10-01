# 03. Requisitos Funcionales - UniMarket

Listado formal de los requerimientos funcionales extraídos de la propuesta técnica del sistema.

---

## 1. Módulo de Gestión de Usuarios y Accesos (Auth & Security / Users)

### RF-01: Autenticación Institucional Obligatoria

El sistema debe validar obligatoriamente que el usuario pertenezca a la comunidad universitaria mediante un correo electrónico institucional con dominio `@universidad.edu.pe` y sus credenciales de red.

### RF-02: Asignación de Roles y Permisos

El sistema asignará permisos y roles diferenciados tras el inicio de sesión, limitando o habilitando funcionalidades específicas para:

- **Estudiante Comprador**
- **Estudiante Proveedor**
- **Administrador**

### RF-03: Interfaz de Usuario Adaptativa

La interfaz gráfica (Frontend en **React / Next.js PWA**) deberá ser intuitiva, amigable y totalmente compatible con dispositivos móviles y navegadores web modernos bajo un diseño responsivo.

---

## 2. Módulo de Publicación y Catálogo (Catalog / Search)

### RF-04: Publicación de Bienes

Los estudiantes proveedores podran publicar bienes (libros, productos usados) especificando categoría, estado de conservación, precio e imágenes mediante el almacenamiento en la nube.

### RF-05: Registro de Servicios Profesionales

Los proveedores de servicios (tutorías, diseño, programación, impresión) registrar su portafolio profesional y tarifas estipuladas por hora o por proyecto.

### RF-06: Búsqueda Avanzada y Filtros

El sistema incluirá un mecanismo de búsqueda avanzada y filtrado multicriterio por categoría, rango de precios y valoración de usuarios.

---


## 3. Módulo de Transacciones y Pagos (Orders & Transactions)

### RF-07: Modelo de Pagos Directos Peer-to-Peer (P2P)

El sistema integrará un modelo de pagos directos Peer-to-Peer (Yape / Plin / Transferencia bancaria), mostrando los datos o códigos QR del estudiante proveedor en cada transacción para eliminar comisiones de pasarelas intermediarias.

### RF-08: Trazabilidad y Comprobantes Digitales

El sistema gestionará la trazabilidad del proceso mediante la carga de comprobantes digitales por parte del comprador y la validación/confirmación en tiempo real por el proveedor.

---


## 4. Módulo de Reservas y Horarios (Booking & Schedule)


### RF-09: Gestión de Disponibilidad en Tiempo Real

 El módulo de tutorías y reserva de salas visualizará la disponibilidad de horarios en tiempo real para evitar cruces o duplicidad de citas.

### RF-10: Confirmaciones Automáticas

El sistema enviará notificaciones y confirmaciones automáticas de reserva de salas y citas de tutoría.

---


## 5. Módulo de Administración e Informes (Administration & Reports)


### RF-11: Reportes Estadísticos y Analítica

 El administrador general visualizará reportes estadísticos consolidados de ventas, cantidad de publicaciones activas y volumen de transacciones segmentadas por facultades o categorías.

### RF-12: Auditoría y Reportes Exportables

El sistema mantendrá registros de auditoría y generará reportes exportables en formato Excel sobre incidencias y disputas entre usuarios.

---

## 6. Módulo de Infraestructura y Soporte Tecnológico (Cloud / Security)

### RF-13: Optimización Perimetral y Seguridad

La plataforma utilizará dominio `.PE`, resolución DNS y protección perimetral mediante **Cloudflare** (WAF y protección DDoS), cifrado HTTPS con SSL/TLS, CDN y mecanismos de caché optimizados para una comunidad objetivo de hasta **15,000 estudiantes** bajo un presupuesto reducido.

### RF-14: Asistente Inteligente Opcional (IA)

El sistema podrá incorporar de forma opcional un asistente inteligente ligero para interpretar consultas en lenguaje natural, facilitando la búsqueda y sugiriendo productos o servicios relevantes según las interacciones del estudiante.

## Relación entre Historias de Usuario (HU) y Requisitos Funcionales (RF)

| Historia de Usuario | Descripción breve | Requisitos Funcionales Asociados |
|---|---|---|
| **HU01: Autenticación Institucional** | Iniciar sesión mediante correo y credenciales de la universidad para acceder al sistema. | RF-01, RF-02, RF-03 |
| **HU02: Publicación de Bienes** | Publicar libros o artículos usados especificando categoría, estado, precio e imágenes. | RF-04, RF-13 |
| **HU03: Registro de Servicios Profesionales** | Registrar portafolios y tarifas (por hora o proyecto) para tutorías y servicios académicos. | RF-05, RF-09 |
| **HU04: Búsqueda y Filtrado Avanzado** | Buscar y filtrar productos o servicios por categoría, rango de precio y valoración. | RF-06 |
| **HU05: Realizar Pagos Directos P2P** | Visualizar datos o códigos QR (Yape/Plin/Transferencia) del proveedor para pago directo. | RF-07 |
| **HU06: Carga de Comprobantes y Validación** | Subir el comprobante digital y permitir al proveedor confirmar la transacción en tiempo real. | RF-08, RF-13 |
| **HU07: Reserva de Salas y Tutorías** | Consultar disponibilidad de horarios en tiempo real para reservar salas o citas sin cruces. | RF-09, RF-10 |
| **HU08: Visualización de Reportes Estadísticos** | Consultar estadísticas de ventas, publicaciones y exportar registros de auditoría/disputas. | RF-11, RF-12 |
