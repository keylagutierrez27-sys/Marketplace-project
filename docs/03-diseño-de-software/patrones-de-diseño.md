#  Patrones de Diseño Arquitectónicos y de Código

Para resolver los drivers arquitectónicos de mantenibilidad, flexibilidad y desacoplamiento en **UniMarket**, se han implementado patrones de diseño estándar en el desarrollo del monolito modular.

---

## 1. Patrones Estructurales y de Arquitectura

### 1.1. Patrón Repository (Repositorio)
* **Ubicación:** Capas de infraestructura y dominio de cada módulo (`catalog`, `orders`, `booking`, etc.).
* **Propósito:** Abstraer el acceso a la base de datos relacional (Supabase PostgreSQL) de la lógica de negocio pura. El dominio define interfaces puras (`ProductRepository`), y la capa de infraestructura implementa las consultas concretas con SQL/ORM.
* **Beneficio:** Permite modificar o cambiar la tecnología de persistencia sin alterar los casos de uso del negocio.

### 1.2. Patrón Ports and Adapters / Hexagonal (Puertos y Adaptadores)
* **Ubicación:** En todos los módulos del backend.
* **Propósito:** Aislar el núcleo de la aplicación (*Dominio* y *Casos de Uso*) del mundo exterior mediante contratos estrictos (puertos) y adaptadores concretos (infraestructura y presentación).
* **Beneficio:** Facilita la prueba unitaria de la lógica de negocio simulando (*mocking*) las interacciones externas.

---

## 2. Patrones de Comportamiento y Creacionales

### 2.1. Patrón Strategy (Estrategia)
* **Ubicación:** Módulo `orders` (`ADR-004`).
* **Propósito:** Gestionar de forma dinámica y desacoplada los diferentes medios de pago P2P y validaciones de comprobantes (Yape, Plin, Transferencia Bancaria).
* **Implementación:** Se define una interfaz común `PaymentValidationStrategy` y múltiples adaptadores específicos según el método elegido por el estudiante.
* **Beneficio:** Permite añadir nuevos medios de pago en el futuro sin modificar la lógica central del ciclo de vida de la orden.

### 2.2. Patrón Facade (Fachada)
* **Ubicación:** Módulo `search-ai` (`SearchAssistantFacade`) (`ADR-008`).
* **Propósito:** Proveer una interfaz unificada y simplificada hacia el subsistema de procesamiento de lenguaje natural y consultas inteligentes.
* **Beneficio:** Oculta la complejidad de la integración con la API de IA externa y garantiza que el sistema siga operando con normalidad si el servicio de IA no está disponible.

### 2.3. Inyección de Dependencias (Dependency Injection)
* **Ubicación:** Raíz de la aplicación (*Composition Root*) y configuración del framework Express.
* **Propósito:** Resolver y suministrar las dependencias (repositorios, servicios, casos de uso) de manera desacoplada durante la inicialización del monolito modular.
* **Beneficio:** Mejora la testabilidad del código y evita acoplamientos rígidos entre clases.