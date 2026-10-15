# 03. Requisitos funcionales - UniMarket

Son 14 requisitos agrupados por módulo del backend. El asistente de IA (**RF-13**) pertenece al módulo **Search & AI**, no a un módulo aparte.

---

## Módulo 1: Gestión de Usuarios y Accesos (`auth / users`)

| ID | Requisito funcional | Descripción |
| :--- | :--- | :--- |
| **RF-01** | **Autenticación institucional obligatoria** | Validar que el usuario pertenezca a la comunidad universitaria mediante correo institucional (`@unsch.edu.pe`) verificado. SSO/OAuth solo si la universidad lo habilita. |
| **RF-02** | **Control de acceso basado en roles (RBAC)** | Asignar permisos y roles (Comprador, Proveedor, Administrador). El Comprador se asigna al registrarse, el Proveedor al activar su perfil de proveedor, y el administrador exige 2FA. |

---

## Módulo 2: Publicación y Catálogo (`catalog / search-ai`)

| ID | Requisito funcional | Descripción |
| :--- | :--- | :--- |
| **RF-03** | **Publicación de bienes físicos** | Publicar libros, herramientas y materiales con título, categoría, estado (Nuevo/Usado), precio en soles e imágenes. |
| **RF-04** | **Registro de servicios profesionales** | Registrar portafolio de evidencias y tarifas por hora, página o proyecto para tutorías, diseño, programación e impresión. |
| **RF-05** | **Búsqueda avanzada y filtrado** | Buscar y filtrar publicaciones por categoría, facultad, rango de precios y valoración. |

---

## Módulo 3: Transacciones y Pagos P2P (`orders`)

| ID | Requisito funcional | Descripción |
| :--- | :--- | :--- |
| **RF-06** | **Datos de pago P2P** | Mostrar el medio de pago del proveedor (Yape, Plin o transferencia) y su código QR en cada orden, sin procesar ni retener fondos. |
| **RF-07** | **Comprobante y constancia virtual** | Permitir al comprador adjuntar el voucher, al proveedor confirmarlo o rechazarlo, y emitir una constancia virtual automática al confirmar. |

---

## Módulo 4: Reservas y Notificaciones (`booking / notifications`)

| ID | Requisito funcional | Descripción |
| :--- | :--- | :--- |
| **RF-08** | **Agendamiento en tiempo real** | Mostrar la disponibilidad de tutorías (publicada por proveedores) y de salas de estudio (publicada por el administrador), bloqueando franjas para evitar traslapes. |
| **RF-09** | **Notificaciones automáticas** | Enviar correos y notificaciones push sobre cambios de estado de órdenes, confirmaciones de reservas y nuevas ventas. |

---

## Módulo 5: Administración y Auditoría (`administration`)

| ID | Requisito funcional | Descripción |
| :--- | :--- | :--- |
| **RF-10** | **Dashboard y métricas estadísticas** | Mostrar reportes visuales de ventas, publicaciones activas y volumen transaccional por facultad o categoría. |
| **RF-11** | **Logs de auditoría y reportes exportables** | Registrar eventos de auditoría de forma inmutable y permitir exportar reportes en Excel (`.xlsx`). |

---

## Módulo 6: Reputación y Asistencia Inteligente (`users / ai-assistant`)

| ID | Requisito funcional | Descripción |
| :--- | :--- | :--- |
| **RF-12** | **Reputación y calificación** | Permitir calificar con estrellas y reseña verificada a un proveedor tras una orden `Completada`, y mostrar públicamente su promedio e historial. |
| **RF-13** | **Asistente conversacional (opcional)** | Interpretar consultas en lenguaje natural y sugerir publicaciones del catálogo. El sistema debe operar íntegramente sin este módulo. |
| **RF-14** | **Moderación e incidencias** | Moderar publicaciones, suspender usuarios y gestionar incidencias o disputas sobre órdenes (estado `En disputa`), con su resolución auditada. |

---

## Matriz de Trazabilidad: Historias de Usuario (HU) vs. Requisitos Funcionales (RF)

| Historia de usuario | Requisitos cubiertos | Módulo backend |
| :--- | :--- | :--- |
| **HU-01** Autenticación institucional | RF-01, RF-02 | `auth/users` |
| **HU-02** Publicación de bienes | RF-03 | `catalog` |
| **HU-03** Registro de servicios y disponibilidad | RF-04, RF-08 | `catalog/booking` |
| **HU-04** Búsqueda y filtrado avanzado | RF-05 | `catalog/search-ai` |
| **HU-05** Datos de pago P2P | RF-06 | `orders` |
| **HU-06** Comprobante, confirmación y constancia | RF-07, RF-09 | `orders/notifications` |
| **HU-07** Reserva de salas y tutorías | RF-08, RF-09 | `booking/notifications` |
| **HU-08** Reportes estadísticos y auditoría | RF-10, RF-11 | `administration` |
| **HU-09** Valoración y reputación | RF-12 | `users` |
| **HU-10** Consultas en lenguaje natural | RF-13 | `search-ai` |
| **HU-11** Moderación e incidencias | RF-14, RF-11, RF-09 | `administration / orders / notifications` |

> *Todos los requisitos RF-01 a RF-14 están cubiertos por al menos una historia de usuario, y todas las historias HU-01 a HU-11 referencian requisitos existentes.*