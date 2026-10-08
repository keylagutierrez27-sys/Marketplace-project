# 03. Requisitos funcionales - UniMarket

Requisitos funcionales extraídos de la propuesta técnica. La interfaz adaptativa pasó a atributos de calidad (AC07) y la infraestructura perimetral a restricciones (RC08), porque no son requisitos funcionales.

## Gestión de usuarios y accesos (Auth & Security / Users)
| ID | Requisito |
|---|---|
| RF-01 | El sistema debe validar que el usuario pertenezca a la comunidad universitaria mediante correo institucional (`@universidad.edu.pe`) y sus credenciales de red. |
| RF-02 | El sistema debe asignar permisos y roles diferenciados (Estudiante Comprador, Estudiante Proveedor y Administrador) tras el inicio de sesión. |

## Publicación y catálogo (Catalog / Search)
| ID | Requisito |
|---|---|
| RF-03 | Los proveedores deben poder publicar bienes (libros, productos usados) con categoría, estado, precio e imágenes. |
| RF-04 | Los proveedores de servicios (tutorías, diseño, programación, impresión) deben registrar su portafolio y tarifas por hora o proyecto. |
| RF-05 | El sistema debe permitir búsqueda avanzada y filtrado por categoría, rango de precios y valoración. |

## Transacciones y pagos (Orders & Transactions)
| ID | Requisito |
|---|---|
| RF-06 | El sistema debe mostrar los datos o el código QR de pago del proveedor (Yape, Plin o transferencia) en cada transacción, sin procesar ni retener fondos. |
| RF-07 | El sistema debe permitir al comprador cargar el comprobante digital, al proveedor confirmarlo en tiempo real, y generar una constancia virtual automática para ambas partes. |

## Reservas y horarios (Booking & Schedule / Notifications)
| ID | Requisito |
|---|---|
| RF-08 | El sistema debe mostrar la disponibilidad de horarios en tiempo real para tutorías y salas, evitando cruces o duplicidad de citas. |
| RF-09 | El sistema debe enviar confirmaciones y notificaciones automáticas (correo y push) de reservas, pedidos y cambios de estado. |

## Administración e informes (Administration & Reports)
| ID | Requisito |
|---|---|
| RF-10 | El administrador debe ver reportes estadísticos de ventas, publicaciones activas y volumen de transacciones por facultad o categoría. |
| RF-11 | El sistema debe mantener registros de auditoría y generar reportes exportables en Excel sobre incidencias y disputas. |

## Reputación y asistente (Catalog / AI Assistant)
| ID | Requisito |
|---|---|
| RF-12 | El sistema debe permitir valorar a los proveedores tras una transacción completada y mostrar su historial de ventas y reputación. |
| RF-13 | De forma opcional, el sistema podrá incluir un asistente inteligente ligero que interprete consultas en lenguaje natural y sugiera productos o servicios. |

## Relación entre historias de usuario (HU) y requisitos funcionales (RF)
| Historia de usuario | Requisitos funcionales |
|---|---|
| HU01 Autenticación institucional | RF-01, RF-02 |
| HU02 Publicación de bienes | RF-03 |
| HU03 Registro de servicios profesionales | RF-04, RF-08 |
| HU04 Búsqueda y filtrado avanzado | RF-05 |
| HU05 Realizar pagos directos P2P | RF-06 |
| HU06 Carga de comprobantes y validación | RF-07, RF-09 |
| HU07 Reserva de salas y tutorías en tiempo real | RF-08, RF-09 |
| HU08 Visualización de reportes estadísticos | RF-10, RF-11 |
| HU09 Valoración y reputación de proveedores | RF-12 |
| HU10 Consultas en lenguaje natural | RF-13 |