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

### HU05: Realizar Pagos Directos P2P

**Como** estudiante comprador,

**quiero** visualizar los datos o el código QR de pago (Yape, Plin o transferencia) del estudiante proveedor,

**para** realizar la transacción de forma directa sin intermediarios.

#### Criterios de Aceptación

  1. El sistema debe mostrar los datos de pago exactos del roveedor al confirmar la orden.
  2. No debe haber retención ni procesamiento de fondos por parte de la plataforma (modelo P2P puro).

### HU06: Carga de Comprobantes y Validación

**Como** estudiante comprador y proveedor,

**quiero** subir el comprobante digital (voucher) y que el proveedor pueda confirmarlo en tiempo real,

**para** asegurar la trazabilidad y cerrar la transacción exitosamente.

#### Criterios de Aceptación

  1. El comprador debe poder adjuntar la imagen del comprobante de pago.
  2. El proveedor recibirá una alerta para verificar el depósito y confirmar la entrega o servicio, generando una constancia virtual.


---

## Módulo: Reservas y Horarios

### HU-07: Reserva de Salas y Tutorías en Tiempo Real
* **Como** estudiante comprador,
* **quiero** visualizar la disponibilidad de horarios en tiempo real para tutorías o salas,
* **para** evitar cruces o duplicidad de citas.
* **Criterios de Aceptación:**
  1. Calendario interactivo con franjas horarias ocupadas y libres.
  2. Envío automático de confirmación de reserva al completarse el proceso.


---


## Módulo: Administración e Informes

### HU08: Visualización de Reportes Estadísticos

**Como** administrador general,

**quiero** visualizar reportes estadísticos de ventas, publicaciones activas y volumen de transacciones por facultad o categoría,

**para** supervisar el rendimiento y la actividad de la plataforma.

#### Criterios de Aceptación

  1. El panel de administración debe mostrar métricas actualizadas de la comunidad (hasta 15,000 estudiantes).
  2. Se deben incluir registros de auditoría y la opción de exportar reportes en formato Excel sobre disputas o incidencias.