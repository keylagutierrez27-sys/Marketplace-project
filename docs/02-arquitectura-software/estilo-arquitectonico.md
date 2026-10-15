# Estilo arquitectónico

**Monolito modular** (ocho módulos) con **Clean Architecture** y **Arquitectura Hexagonal** dentro de cada módulo (ADR-001, ADR-002, ADR-004). Clean Architecture fija la dirección de las dependencias; la Hexagonal aporta puertos y adaptadores para aislar el dominio de bases de datos, frameworks y APIs externas.

## Capas por módulo

| Capa | Contiene | No debe hacer |
|---|---|---|
| Dominio | Entidades, objetos de valor, invariantes y reglas esenciales | Importar Express, Supabase, SDK de IA ni detalles HTTP |
| Aplicación | Casos de uso, coordinación, DTO y transacciones a través de puertos | Contener reglas de transporte HTTP ni consultas SQL |
| Infraestructura | Repositorios, almacenamiento, correo y clientes de APIs | Decidir políticas de negocio |
| Presentación | Rutas, controladores, validación de entrada y respuestas HTTP | Acceder directo a la BD o duplicar reglas de negocio |

**Regla de dependencias:** presentación e infraestructura dependen de aplicación y de los contratos hacia el núcleo; el dominio no depende de frameworks ni de servicios externos. Las implementaciones se conectan en el *composition root*.

![Capas de Clean Architecture](img/Clean-arquitecture.png)

## Estructura de carpetas

```
src/modules/orders/
  domain/          entities/ value-objects/ services/ ports/
  application/     use-cases/ dto/ ports/
  infrastructure/  persistence/ integrations/
  presentation/http/  controllers/ routes/ validators/
```

## Patrones y adaptadores

Strategy (medios P2P), Adapter (IA, almacenamiento, correo), Facade (búsqueda asistida) y Observer (notificaciones por evento). Detalle en `03-diseño-de-software`.

## Seguridad transversal

- Validar autenticación y permisos en el backend; ocultar un botón en el frontend no es autorización.
- Validar entradas, tamaño y tipo MIME de archivos; controlar el acceso a comprobantes y limitar el abuso.
- Secretos en variables de entorno del hosting, nunca en el repositorio ni en el frontend.
- Auditoría sin contraseñas, tokens completos ni datos bancarios sensibles.
- La caché de Cloudflare se limita a contenido público; las rutas privadas de la API se excluyen.