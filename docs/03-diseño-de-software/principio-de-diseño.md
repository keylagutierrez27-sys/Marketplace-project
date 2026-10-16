#  Principios de Diseño de Software

Para garantizar que el código fuente y la arquitectura de **UniMarket** sean mantenibles, legibles y fáciles de escalar a lo largo del tiempo, se aplican los siguientes principios fundamentales de ingeniería de software:

---

## 1. Principios Arquitectónicos y Estructurales

### 1.1. Separación de Responsabilidades (Separation of Concerns - SoC)
* **Definición:** El sistema se divide en capas y módulos diferenciados, donde cada componente tiene una única responsabilidad bien definida.
* **Aplicación en UniMarket:** Las reglas de negocio puras (`Domain`), la orquestación (`Application`), los accesos a datos (`Infrastructure`) y la exposición HTTP (`Presentation`) no se mezclan entre sí.

### 1.2. Principio de Inversión de Dependencias (Dependency Inversion Principle - DIP)
* **Definición:** Los módulos de alto nivel no deben depender de módulos de bajo nivel; ambos deben depender de abstracciones. Además, las abstracciones no deben depender de los detalles.
* **Aplicación en UniMarket:** El dominio define interfaces puras (puertos) para los repositorios y servicios externos, y la capa de infraestructura implementa dichos contratos, invirtiendo la dirección tradicional de las dependencias hacia el centro de la arquitectura.

### 1.3. Independencia de Frameworks y Entornos Externos
* **Definición:** La arquitectura no debe depender de la existencia de alguna librería o framework cargado de funcionalidades.
* **Aplicación en UniMarket:** La lógica central del negocio puede probarse y ejecutarse de manera completamente aislada, sin necesidad de levantar un servidor HTTP o conectarse directamente a la base de datos real.

### 1.4. Alta Cohesión y Bajo Acoplamiento
* **Definición:** Los elementos dentro de un mismo módulo deben estar fuertemente relacionados (alta cohesión), mientras que las interacciones entre diferentes módulos deben minimizarse al máximo (bajo acoplamiento).
* **Aplicación en UniMarket:** Los ocho módulos del monolito (`auth`, `users`, `catalog`, `orders`, `booking`, `search-ai`, `notifications`, `administration`) operan de forma lógica e independiente bajo contratos claros.

---

## 2. Principios de Código Limpio y Patrones

### 2.1. Principios SOLID
* **S (Single Responsibility):** Cada clase, caso de uso o controlador tiene una única razón para cambiar.
* **O (Open/Closed):** Las entidades del dominio y los casos de uso están abiertos a la extensión pero cerrados a la modificación (por ejemplo, al añadir nuevos adaptadores de pago sin tocar el núcleo).
* **L (Liskov Substitution):** Las implementaciones concretas de los repositorios y adaptadores pueden sustituirse sin alterar el comportamiento del sistema.
* **I (Interface Segregation):** Las interfaces creadas son específicas para cada cliente, evitando forzar métodos que no se utilizan.
* **D (Dependency Injection):** Las dependencias se inyectan explícitamente en los constructores o contenedores de servicios.

### 2.2. Ley de Demeter (Principio de Mínimo Conocimiento)
* **Definición:** Un objeto debe hablar únicamente con sus amigos cercanos y no conocer detalles internos de objetos ajenos, reduciendo el impacto ante cambios estructurales en cascada.