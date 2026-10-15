# 02. Historias de Usuario - UniMarket

A continuación se detallan las historias de usuario clave agrupadas por módulos funcionales del sistema UniMarket.

---

## Módulo 1: Gestión de Usuarios y Accesos (`auth/users`)

| ID | Historia de usuario | Criterios de aceptación |
| :--- | :--- | :--- |
| **HU-01** | Como estudiante de la comunidad universitaria, quiero iniciar sesión con mi correo institucional verificado, para garantizar que solo miembros verificados accedan a UniMarket. | **1)** El sistema rechaza correos fuera del dominio institucional.<br>**2)** El correo se verifica por enlace o código y se emite un token JWT.<br>**3)** Todo usuario recibe el rol Comprador; al activar su perfil de proveedor obtiene también el rol Proveedor. |

---

## Módulo 2: Publicación y Catálogo (`catalog/search-ai`)

| ID | Historia de usuario | Criterios de aceptación |
| :--- | :--- | :--- |
| **HU-02** | Como estudiante proveedor, quiero publicar libros o artículos usados con categoría, estado, precio e imágenes, para ofrecerlos a los compradores del campus. | **1)** El formulario exige título, categoría, estado (Nuevo/Usado), precio en soles e imágenes.<br>**2)** Las imágenes se almacenan en la nube (Supabase Storage).<br>**3)** La publicación aparece de inmediato en el catálogo. |
| **HU-03** | Como estudiante proveedor de servicios (tutorías, programación, diseño, impresión), quiero registrar mi portafolio, tarifas y disponibilidad, para que los compradores conozcan mis habilidades y me contraten. | **1)** Permite adjuntar evidencias de portafolio o una descripción detallada.<br>**2)** Muestra la tarifa (por hora, página, proyecto o unidad).<br>**3)** Permite definir franjas de disponibilidad en las tutorías.<br>**4)** Asocia la publicación al perfil del proveedor. |
| **HU-04** | Como estudiante comprador, quiero buscar y filtrar productos o servicios por categoría, facultad, precio y valoración, para encontrar rápido lo que necesito al mejor precio. | **1)** Barra de búsqueda con filtros dinámicos por rango de precios, facultad, categoría y valoración.<br>**2)** Respuesta de búsqueda inferior a 1.5 segundos en las pruebas de carga.<br>**3)** La búsqueda funciona sin IA; la IA solo añade consultas en lenguaje natural (HU-10). |

---

## Módulo 3: Transacciones y Pagos P2P (`orders`)

| ID | Historia de usuario | Criterios de aceptación |
| :--- | :--- | :--- |
| **HU-05** | Como estudiante comprador, quiero ver los datos de pago o el código QR (Yape, Plin o transferencia) del proveedor, para pagar directamente sin intermediarios. | **1)** Al crear la orden, el sistema muestra los datos de pago y el QR del proveedor.<br>**2)** UniMarket no retiene ni custodia fondos ni cobra comisión.<br>**3)** La orden queda en estado `Pendiente de pago`. |
| **HU-06** | Como estudiante comprador y proveedor, quiero subir y revisar el comprobante digital (voucher), para asegurar la trazabilidad y cerrar la transacción. | **1)** El comprador adjunta una imagen legible del voucher y la orden pasa a `Comprobante enviado`.<br>**2)** El proveedor recibe una notificación, revisa el voucher y confirma o rechaza.<br>**3)** Al confirmar, el estado pasa a `Pago confirmado` y el sistema emite la constancia virtual.<br>**4)** La orden pasa a `Completada` cuando el comprador confirma la recepción del bien o servicio.<br>**5)** Si el proveedor no responde en el plazo configurado, la orden pasa a `Vencida` y ambos son notificados. |

---

## Módulo 4: Reservas y Agendamiento (`booking`)

| ID | Historia de usuario | Criterios de aceptación |
| :--- | :--- | :--- |
| **HU-07** | Como estudiante comprador, quiero ver la disponibilidad de tutorías y salas de estudio en tiempo real, para agendar citas sin cruces ni duplicidad. | **1)** Calendario que muestra solo franjas libres.<br>**2)** Al solicitar una reserva, la franja se bloquea de inmediato mediante transacción en la base de datos.<br>**3)** Se envían confirmaciones por correo o push al comprador y al proveedor (en salas, al administrador del espacio). |

---

## Módulo 5: Administración y Auditoría (`administration`)

| ID | Historia de usuario | Criterios de aceptación |
| :--- | :--- | :--- |
| **HU-08** | Como administrador general, quiero ver reportes estadísticos de ventas, publicaciones y transacciones por facultad, para supervisar el rendimiento de la plataforma. | **1)** Panel con métricas de usuarios activos, publicaciones activas y volumen transaccional por facultad o categoría.<br>**2)** Acceso a registros de auditoría.<br>**3)** Exportación de reportes en formato Excel (`.xlsx`). |
| **HU-11** | Como administrador general, quiero moderar publicaciones, suspender usuarios y atender incidencias o disputas entre compradores y proveedores, para resolver conflictos con evidencia. | **1)** Puede ocultar o eliminar publicaciones inapropiadas y suspender cuentas.<br>**2)** Un participante puede reportar una incidencia sobre una orden, que pasa a `En disputa`.<br>**3)** El administrador ve la trazabilidad completa (estados, voucher, notificaciones) y registra su resolución en la auditoría. |

---

## Módulo 6: Reputación y Asistencia Inteligente (`users/search-ai`)

| ID | Historia de usuario | Criterios de aceptación |
| :--- | :--- | :--- |
| **HU-09** | Como estudiante comprador, quiero calificar con estrellas y reseñar a un proveedor tras completar una orden, para orientar a otros compradores. | **1)** Solo puede calificar quien tenga una orden `Completada` con ese proveedor.<br>**2)** Se permite una reseña por orden.<br>**3)** El perfil público del proveedor muestra su promedio e historial. |
| **HU-10** | Como estudiante comprador, quiero hacer consultas en lenguaje natural, para que el asistente me sugiera productos o servicios relevantes. | **1)** Función opcional, activable por configuración.<br>**2)** El asistente solo sugiere publicaciones existentes en el catálogo.<br>**3)** Si el proveedor de IA falla o se agota su cuota, la búsqueda normal sigue funcionando. |