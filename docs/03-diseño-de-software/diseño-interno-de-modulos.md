# 5. Diseño Interno de Módulos (Clean Architecture)

Cada uno de los ocho módulos del monolito modular de **UniMarket** (`auth`, `users`, `catalog`, `orders`, `booking`, `search-ai`, `notifications` y `administration`) se encuentra estrictamente aislado y organizado internamente en cuatro capas concéntricas, garantizando que las reglas de negocio sean independientes de los frameworks, bases de datos o interfaces externas.

---

## 5.1. Estructura de Capas por Módulo

```text
src/
└── modules/
    └── [nombre-modulo]/         # Ej: catalog, orders, booking
        ├── domain/              # Capa 1: Reglas de negocio puras
        │   ├── entities/        # Entidades y Objetos de Valor (Value Objects)
        │   ├── repositories/    # Interfaces de puertos (Repository Contracts)
        │   └── errors/          # Excepciones de dominio
        ├── application/         # Capa 2: Casos de uso / Orquestación
        │   ├── use-cases/       # Lógica de aplicación (ej. CreateProduct, BookRoom)
        │   └── dtos/            # Objetos de transferencia de datos (Input/Output)
        ├── infrastructure/      # Capa 3: Adaptadores de persistencia y servicios
        │   ├── persistence/     # Modelos ORM, clientes de Supabase y repositorios concretos
        │   └── services/        # Adaptadores externos (ej. Email, IA, Storage)
        └── presentation/        # Capa 4: Interfaces de entrada (API REST)
            ├── controllers/     # Controladores HTTP (Express)
            ├── routers/         # Definición de rutas y endpoints (/api/v1/...)
            └── middlewares/     # Validación de esquemas y permisos locales al módulo