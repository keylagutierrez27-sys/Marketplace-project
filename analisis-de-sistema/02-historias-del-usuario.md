# 02. Historias de Usuario - UniMarket

A continuación se detallan las historias de usuario clave agrupadas por módulos funcionales del sistema UniMarket.

---

## Módulo: Gestión de Usuarios y Accesos

### HU-01: Autenticación Institucional
* **Como** estudiante de la comunidad universitaria,
* **quiero** iniciar sesión utilizando mi correo institucional y contraseña de red,
* **para** garantizar que solo miembros verificados accedan a la plataforma de UniMarket.
* **Criterios de Aceptación:**
  1. El sistema valida obligatoriamente dominios institucionales (`@universidad.edu.pe`).
  2. Se asignan roles diferenciados de forma automática (Estudiante Comprador / Estudiante Proveedor).

---

## Módulo: Publicación y Catálogo

### HU-02: Publicación de Productos Usados
* **Como** estudiante proveedor,
* **quiero** publicar libros o artículos usados especificando categoría, estado, precio e imágenes,
* **para** ofrecerlos de forma visible a los compradores interesados del campus.
* **Criterios de Aceptación:**
  1. El formulario solicita obligatoriamente: título, categoría, estado físico, precio en Soles e imágenes.
  2. El producto se indexa inmediatamente en el catálogo general.

### HU-03: Publicación de Servicios Profesionales
* **Como** estudiante proveedor de servicios (tutorías, programación, diseño, impresión),
* **quiero** registrar mi portafolio y tarifas por hora o proyecto,
* **para** que los compradores puedan conocer mis habilidades y contratarlos.
* **Criterios de Aceptación:**
  1. Permite adjuntar evidencias de portafolio o descripción detallada del servicio.
  2. Muestra claramente la tarifa establecida.

### HU-04: Búsqueda Avanzada y Filtros
* **Como** estudiante comprador,
* **quiero** buscar y filtrar productos o servicios por categoría, precio y valoración,
* **para** encontrar rápidamente lo que necesito al mejor precio.
* **Criterios de Aceptación:**
  1. Barra de búsqueda rápida conectada al motor de búsqueda.
  2. Filtros dinámicos por rango de precios y categorías académicas.

---

## Módulo: Transacciones y Pagos

### HU-05: Pago Directo Peer-to-Peer y Comprobante
* **Como** estudiante comprador,
* **quiero** visualizar los datos o código QR de Yape/Plin del proveedor y subir mi comprobante digital,
* **para** completar la transacción de forma directa y sin intermediarios.
* **Criterios de Aceptación:**
  1. Visualización del QR o número del proveedor en la pantalla de pago de la orden.
  2. Campo para adjuntar captura del voucher o comprobante digital.
  3. Confirmación en tiempo real por parte del proveedor.

---

## Módulo: Reservas y Horarios

### HU-06: Reserva de Salas y Tutorías en Tiempo Real
* **Como** estudiante comprador,
* **quiero** visualizar la disponibilidad de horarios en tiempo real para tutorías o salas,
* **para** evitar cruces o duplicidad de citas.
* **Criterios de Aceptación:**
  1. Calendario interactivo con franjas horarias ocupadas y libres.
  2. Envío automático de confirmación de reserva al completarse el proceso.