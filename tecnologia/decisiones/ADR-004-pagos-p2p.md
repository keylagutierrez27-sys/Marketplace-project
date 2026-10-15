# ADR-004: Pagos P2P con puertos y adaptadores

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA03 (Pagos P2P)

## Contexto
Los pagos se hacen directo entre estudiantes (Yape, Plin o transferencia) y UniMarket no procesa ni retiene fondos. Aun así debe haber trazabilidad para resolver disputas.

## Decisión
El módulo Orders & Transactions maneja el flujo: orden pendiente, datos o QR del proveedor, carga del comprobante, confirmación del proveedor y constancia virtual automática. El dominio depende de puertos (`RepositorioOrdenes`, `AlmacenComprobantes`, `NotificadorUsuario`) y la infraestructura aporta los adaptadores (PostgreSQL, Supabase Storage, correo y push).

## Alternativas consideradas
- **Pasarela de pagos:** descartada por las comisiones y porque la propuesta pide P2P.
- **Registrar pagos sin comprobante:** sin trazabilidad ante disputas.

## Consecuencias
- (+) No hay comisiones ni custodia de fondos.
- (+) Se puede cambiar el almacenamiento o el servicio de notificaciones sin tocar el dominio.
- (-) La confirmación depende de que el proveedor responda a tiempo.
- (-) Hay que definir un plazo de confirmación y el manejo de disputas.
