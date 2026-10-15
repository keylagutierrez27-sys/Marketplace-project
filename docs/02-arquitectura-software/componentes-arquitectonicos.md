# Componentes arquitectónicos

UniMarket define **ocho módulos** dentro del backend. El asistente de IA es una capacidad interna de Search & AI, no un noveno módulo.

| # | Módulo | Responsabilidades y límites | Requisitos |
|---|---|---|---|
| 1 | Auth & Security (`auth`) | Autenticación, validación de tokens, RBAC, 2FA del administrador, políticas de acceso | RF-01, RF-02 |
| 2 | Users (`users`) | Perfil universitario, perfil público del proveedor, reputación y reseñas verificadas | RF-12 |
| 3 | Catalog (`catalog`) | Publicaciones de bienes y servicios, categorías, imágenes, tarifas, estado | RF-03, RF-04, RF-05 |
| 4 | Orders (`orders`) | Órdenes, estados, comprobantes P2P, verificación del proveedor, constancias, incidencias | RF-06, RF-07, RF-14 |
| 5 | Booking (`booking`) | Disponibilidad de tutorías y salas, franjas, prevención de reservas duplicadas | RF-08 |
| 6 | Search & AI (`search-ai`) | Búsqueda, filtros, recomendaciones y asistente de lenguaje natural opcional | RF-05, RF-13 |
| 7 | Notifications (`notifications`) | Correo o push ante cambios de estado, con adaptadores a proveedores externos | RF-09 |
| 8 | Administration (`administration`) | Moderación, métricas, auditoría, incidencias y exportación de reportes | RF-10, RF-11, RF-14 |

## Diagrama de componentes


![Diagrama de componentes del backend](img/Diagrama-Componentes-Backend.png)

## Reglas de interacción

Los módulos solo se comunican por **servicios de aplicación, puertos públicos o eventos internos**; ningún módulo importa repositorios ni entidades internas de otro (puede verificarse en CI con `dependency-cruiser`).

| Origen | Destino | Mecanismo | Motivo |
|---|---|---|---|
| orders | catalog | Interfaz pública `ListingReader` | Verificar publicación activa y precio |
| orders | notifications | Evento `OrderStatusChanged` | Avisar cambios de estado |
| orders | administration | `AuditLogPort` | Auditar resolución de disputas |
| users | orders | Interfaz pública de consulta | Validar orden Completada antes de reseñar |
| booking | notifications | Evento `ReservationConfirmed` | Confirmaciones de reserva |
| booking | catalog | Interfaz pública | Asociar tutoría a la publicación |
| search-ai | catalog | `SearchReader` (solo lectura) | Búsqueda y recomendaciones |
| todos | auth | `authMiddleware` / `TokenVerifierPort` | Autenticación y RBAC |