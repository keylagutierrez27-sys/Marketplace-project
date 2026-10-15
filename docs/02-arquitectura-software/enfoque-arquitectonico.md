# Enfoque arquitectónico: DDD dentro del monolito

Domain-Driven Design organiza el dominio; no es una tecnología independiente. Se aplica de forma ligera dentro del monolito modular (ADR-001, ADR-002).

- **Lenguaje ubicuo:** usar de forma consistente *Publicación, Orden, Comprobante, Reserva, Proveedor* y *Estado de la orden*. En código los nombres van en inglés (`Listing`, `Order`, `PaymentEvidence`, `Reservation`).
- **Límites de contexto:** Catalog administra publicaciones, Orders el ciclo de compra y Booking las citas y la disponibilidad. Una orden no modifica directamente las tablas internas de Booking.
- **Dependencias entre módulos:** solo mediante servicios de aplicación o interfaces públicas, sin importar repositorios ni entidades internas de otro módulo.
- **Persistencia:** PostgreSQL es compartido, pero cada módulo accede a sus datos con sus propios repositorios. La separación es lógica, no bases de datos independientes.
- **Eventos internos:** `OrderStatusChanged` notifica a Notifications después de confirmar la transacción. Si se necesita mayor fiabilidad, puede añadirse Transactional Outbox (diferido).

## Por qué este enfoque (drivers)

| Driver | Cómo lo atiende el enfoque |
|---|---|
| DA05 Modificabilidad | Límites de contexto claros: cambiar un módulo no afecta a otros |
| DA01 Costo | Un solo despliegue; sin la complejidad operativa de microservicios |
| DA07 Reservas sin cruces | Las reglas de agenda viven en el dominio de Booking y se refuerzan con restricción de exclusión en PostgreSQL (ADR-006) |