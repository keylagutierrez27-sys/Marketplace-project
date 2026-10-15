# ADR-008: IA como servicio desacoplado

**Estado:** Aceptada · **Fecha:** 2026-10-08
**Drivers relacionados:** DA08 (IA opcional)

## Contexto
El asistente inteligente es opcional y debe apoyarse en herramientas gratuitas o de código abierto, sin infraestructura de ML propia.

## Decisión
El módulo AI Assistant usa un puerto (`AsistenteBusqueda`) implementado por un adaptador que llama a una API externa o de código abierto (por ejemplo, mediante Supabase Edge Functions). Si el servicio falla, la búsqueda normal sigue funcionando.

## Alternativas consideradas
- **Modelo propio alojado por el proyecto:** costo y operación fuera del presupuesto.
- **No incluir IA:** se pierde un objetivo opcional de la propuesta.

## Consecuencias
- (+) El núcleo no depende de la IA y el proveedor se puede cambiar.
- (-) Dependencia de límites y cuotas gratuitas del servicio externo.
