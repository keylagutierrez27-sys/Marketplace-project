
**ARQUITECTURA C4**

**1. Diagrama de contexto**
```mermaid
flowchart TD
    Comprador["👤 Estudiante Comprador<br/>Compra libros, productos usados,<br/>tutorías, reservas de salas"]
    Proveedor["👤 Estudiante Proveedor<br/>Vende productos y ofrece<br/>tutorías, diseño, programación, impresión"]

    Sistema["🖥️ Marketplace Universitario<br/>Conecta a compradores y<br/>proveedores estudiantiles dentro del campus"]

    Pagos["Pasarela de Pagos<br/>Procesa cobros y pagos entre usuarios"]
    Auth["Autenticación Universitaria<br/>Valida la identidad institucional del estudiante"]
    Notif["Servicio de Notificaciones<br/>Envía correos y notificaciones push"]

    Comprador -->|Busca, compra y reserva| Sistema
    Proveedor -->|Publica y gestiona su oferta| Sistema
    Sistema -->|Delega el cobro/pago en| Pagos
    Sistema -->|Valida usuarios contra| Auth
    Sistema -->|Envía alertas mediante| Notif
```

**2. Diagrama de contenedores**
```mermaid
flowchart TD
    Comprador["👤 Estudiante Comprador"]
    Proveedor["👤 Estudiante Proveedor"]

    subgraph Sistema["Marketplace Universitario"]
        Web["Aplicación Web<br/>[React / Next.js]<br/>Buscar, comprar, publicar, reservar"]
        Movil["Aplicación Móvil<br/>[React Native]<br/>Acceso a funciones principales"]
        API["API Backend<br/>[Node.js / REST]<br/>Lógica de negocio del marketplace"]
        BD["Base de Datos<br/>[PostgreSQL]<br/>Usuarios, productos, servicios, reservas, transacciones"]
        Busqueda["Motor de Búsqueda<br/>[Elasticsearch]<br/>Indexa productos y servicios"]
        Storage["Almacenamiento de Archivos<br/>[Cloud Storage/S3]<br/>Fotos, portafolios, comprobantes"]
    end

    Pagos["Pasarela de Pagos"]
    Auth["Autenticación Universitaria"]
    Notif["Servicio de Notificaciones"]

    Comprador -->|Usa| Web
    Comprador -->|Usa| Movil
    Proveedor -->|Usa| Web
    Proveedor -->|Usa| Movil

    Web -->|HTTPS/JSON| API
    Movil -->|HTTPS/JSON| API

    API -->|Lee/Escribe SQL| BD
    API -->|Indexa y consulta| Busqueda
    API -->|Sube/descarga archivos| Storage
    API -->|Procesa transacciones| Pagos
    API -->|Valida sesión| Auth
    API -->|Dispara notificaciones| Notif
```

**3. Diagrama de componentes (API Backend)**
```mermaid
flowchart TD
    subgraph API["API Backend"]
        CtrlServicios["Controlador de Servicios<br/>Tutorías, diseño, programación, impresión"]
        Gestor["Gestor de Usuarios<br/>Perfiles comprador/proveedor"]
        CtrlCatalogo["Controlador de Catálogo<br/>Publicación y compra de bienes"]
        CtrlAuth["Controlador de Autenticación<br/>Login, registro, sesión"]
        CtrlReservas["Controlador de Reservas<br/>Salas y agenda de tutorías"]
        CtrlPagos["Controlador de Pagos<br/>Coordina cobro/pago P2P"]
        SrvBusqueda["Servicio de Búsqueda<br/>Consulta al motor de búsqueda"]
        SrvNotif["Servicio de Notificaciones<br/>Arma y envía eventos"]
        DAO["Capa de Acceso a Datos<br/>[ORM]"]
    end

    BD[("Base de Datos")]
    AuthExt["Autenticación Universitaria"]
    PagosExt["Pasarela de Pagos"]
    Motor["Motor de Búsqueda"]
    NotifExt["Servicio de Notificaciones (externo)"]

    CtrlServicios --> DAO
    Gestor --> DAO
    CtrlCatalogo --> DAO
    CtrlReservas --> DAO
    CtrlPagos --> DAO
    CtrlAuth -->|Valida credenciales| AuthExt
    CtrlPagos -->|Ejecuta cobro/pago| PagosExt
    SrvBusqueda -->|Consulta índice| Motor
    SrvNotif -->|Envía evento| NotifExt
    DAO -->|Lee/Escribe| BD
    CtrlAuth --> DAO
    SrvBusqueda --> DAO
    SrvNotif --> DAO
```

**4. Arquitectura técnica (con presupuesto optimizado)**
```mermaid
flowchart TD
    Comprador["Estudiante Comprador"]
    Proveedor["Estudiante Proveedor"]

    AuthInst["Sistema de Autenticación Institucional<br/>SSO/OAuth 2.0<br/>@universidad.edu.pe"]

    subgraph UniMarket["UniMarket - Marketplace Universitario"]
        WebSrv["Servidor Web<br/>Frontend Cloud / Vercel<br/>Node.js Runtime, CDN"]
        AppMovil["Aplicación Móvil<br/>React Native"]
        APICloud["API Cloud<br/>Render — Node.js 20.x / Express<br/>0.5 vCPU, 512 MB RAM"]
        StorageCloud["Almacenamiento de Archivos<br/>Supabase/Cloudinary"]
        BDCloud[("Base de Datos<br/>Supabase PostgreSQL 15+")]
    end

    PagosExt["Pasarela de Pagos<br/>Yape/Plin/Stripe"]
    NotifExt["Servicio de Notificaciones<br/>Firebase / Correo"]

    Comprador -->|Usa| WebSrv
    Comprador -->|Usa| AppMovil
    Proveedor -->|Usa| WebSrv
    Proveedor -->|Usa| AppMovil

    WebSrv -->|HTTPS| APICloud
    AppMovil -->|HTTPS| APICloud

    APICloud -->|Lee/Escribe SQL| BDCloud
    APICloud -->|Sube/descarga archivos| StorageCloud
    APICloud -->|Ejecuta cobro/pago| PagosExt
    APICloud -->|Valida credenciales| AuthInst
    APICloud -->|Envía evento| NotifExt
```

**5. Diagrama de secuencia (compra/reserva)**
```mermaid
sequenceDiagram
    actor Comprador as Estudiante Comprador
    participant App as Aplicación Web/Móvil
    participant API as API Backend
    participant Auth as Autenticación Universitaria
    participant Busqueda as Motor de Búsqueda
    participant BD as Base de Datos
    participant Pagos as Pasarela de Pagos
    participant Notif as Notificaciones
    actor Proveedor as Estudiante Proveedor

    Comprador->>App: Inicia sesión
    App->>API: Valida credenciales
    API->>Auth: Valida credenciales
    Auth-->>API: Sesión válida

    Comprador->>App: Busca producto o servicio
    App->>API: GET /buscar
    API->>Busqueda: Consulta índice
    Busqueda-->>API: Resultados
    API-->>App: Resultados

    Comprador->>App: Confirma compra o reserva
    App->>API: POST /orden
    API->>BD: Registra orden pendiente
    API->>Pagos: Solicita cobro

    alt Pago aprobado
        Pagos-->>API: Pago aprobado
        API->>BD: Marca orden como pagada
        API->>Notif: Notifica nueva orden
        Notif-->>Proveedor: Aviso de nueva venta o tutoría

        alt Proveedor confirma a tiempo
            Proveedor->>API: Confirma entrega o servicio
            API->>BD: Cierra orden
            API->>Notif: Notifica confirmación
            Notif-->>Comprador: Aviso de compra completada
        else Proveedor no confirma a tiempo
            API->>Notif: Notifica vencimiento
            Notif-->>Comprador: Aviso de reembolso o reasignación
        end
    else Pago rechazado
        Pagos-->>API: Pago rechazado
        API->>BD: Cancela orden
        API-->>App: Informa rechazo
        App-->>Comprador: Muestra error de pago
    end
```