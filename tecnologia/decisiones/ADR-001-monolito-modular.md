# ADR-001: Monolito modular

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA01 (Presupuesto), DA04 (Escalabilidad), DA05 (Mantenibilidad)

## Contexto
UniMarket atenderá hasta 15,000 estudiantes con picos de uso, un presupuesto máximo de S/. 100 mensuales y un equipo pequeño. La propuesta descarta microservicios como arquitectura principal.

## Decisión
Una sola aplicación backend (Node.js + Express) organizada en módulos independientes: Auth & Security, Users, Catalog, Search & Recommendations, Orders & Transactions, Booking & Schedule, Notifications, Administration & Reports y AI Assistant. El backend será stateless para poder replicarlo en varias instancias detrás de un balanceador.

## Alternativas consideradas
- **Microservicios:** escalan por componente, pero su costo operativo y de comunicación no cabe en el presupuesto ni en el alcance.
- **Monolito sin módulos:** más simple al inicio, pero los cambios afectarían a todo el sistema (DA05).

## Consecuencias
- (+) Un solo despliegue, bajo costo y módulos con responsabilidades claras.
- (+) Un módulo podrá extraerse a futuro sin rediseñar todo.
- (-) Se escala toda la aplicación y no cada módulo por separado.
- (-) Exige disciplina para que los módulos no se accedan entre sí saltándose sus servicios.
