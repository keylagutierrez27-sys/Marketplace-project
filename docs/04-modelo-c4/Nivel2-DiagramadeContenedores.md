# C4 - Nivel 2: Diagrama de contenedores

Muestra las aplicaciones y almacenes de datos que componen UniMarket y cómo se comunican.

```mermaid
flowchart TB
    U(["Compradores, Proveedores y Administrador"])
    CF["Cloudflare<br/>DNS, SSL, CDN, WAF"]
    subgraph UM["UniMarket"]
        WEB["PWA Web<br/>Next.js en Vercel"]
        MOB["App móvil<br/>React Native (prevista)"]
        API["API Backend<br/>Node.js + Express + TypeScript<br/>Monolito modular en Render"]
        DB[("PostgreSQL<br/>Supabase")]
        ST[("Storage privado<br/>Supabase: imágenes y vouchers")]
    end
    AUTH["Supabase Auth"]
    IA["Proveedor de IA (opcional)"]
    PUSH["Firebase Messaging / SMTP"]
    U --> CF
    CF --> WEB
    CF --> MOB
    WEB -->|"REST JSON /api/v1"| API
    MOB -->|"REST JSON /api/v1"| API
    API -->|"SQL / ORM"| DB
    API -->|"URL firmada"| ST
    API -->|"Verifica JWT"| AUTH
    API -.->|"Consultas IA"| IA
    API -->|"Push / correo"| PUSH
```

![Diagrama de contenedores](../img/diagrama-contenedores.png)

| Contenedor | Tecnología | Responsabilidad |
|---|---|---|
| PWA Web | Next.js (React), Vercel | Interfaz adaptable para los tres roles |
| App móvil | React Native | Cliente de la misma API; evolución prevista si el plazo es corto |
| API Backend | Node.js, Express, TypeScript, Render | Reglas de negocio, validación, autorización, orquestación; 8 módulos |
| Base de datos | PostgreSQL (Supabase) | Datos transaccionales ACID: usuarios, catálogo, órdenes, reservas, auditoría |
| Almacenamiento | Supabase Storage | Imágenes y vouchers; bucket privado con URL firmada de corta duración |
| Borde | Cloudflare | DNS, HTTPS/TLS, CDN, caché de contenido público (nunca rutas privadas) |

**Trazabilidad:** ADR-001, ADR-003, ADR-007, ADR-009, ADR-010 · RC04–RC10, RC13 · AC-02, AC-04, AC-05.