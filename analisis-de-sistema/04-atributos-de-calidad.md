# 04. Atributos de Calidad (Requisitos No Funcionales) - UniMarket

De acuerdo con la arquitectura técnica y el presupuesto optimizado planteado en la propuesta, se definen los siguientes atributos de calidad bajo escenarios de arquitectura de software:

---

## 1. Restricción de Costo y Eficiencia Económica
* **Definición:** La solución arquitectónica debe sostenerse bajo un modelo de costos ultra-bajo u operación gratuita (Free Tiers y PaaS ligeros), estimando un costo mensual real entre S/. 65.00 y S/. 85.00 soles para dar soporte a una comunidad proyectada de 15,000 estudiantes.
* **Métrica:** Presupuesto operativo mensual $\le \text{S/. } 100.00$.

## 2. Rendimiento y Escalabilidad (Performance)
* **Definición:** El backend desplegado en contenedores ligeros (Node.js/Express en Render) y el motor de base de datos relacional (Supabase PostgreSQL) deben responder de manera fluida ante consultas concurrentes de búsqueda y registro de transacciones.
* **Métrica:** Tiempos de respuesta en consultas de catálogo inferiores a $2.0$ segundos bajo concurrencia moderada.

## 3. Disponibilidad y Confiabilidad (Availability)
* **Definición:** El uso de servicios en la nube con CDN global (Vercel para la aplicación web SPA/Next.js) garantiza alta disponibilidad y despliegues automáticos con certificados SSL gratuitos.
* **Métrica:** Disponibilidad del servicio web superior al $99.0\%$ anual respaldada por la infraestructura en la nube.

## 4. Seguridad y Privacidad (Security)
* **Definición:** Las credenciales de acceso y sesiones de usuario deben protegerse mediante protocolos estándar de la industria (OAuth 2.0 / OpenID Connect) vinculados estrictamente al directorio institucional universitario.
* **Métrica:** Cero tolerancia a accesos no autorizados sin validación previa del correo institucional (`@universidad.edu.pe`).

## 5. Portabilidad y Compatibilidad
* **Definición:** La aplicación debe ser accesible tanto desde navegadores web modernos en computadoras como desde dispositivos móviles mediante una arquitectura multiplataforma (React Native).

## 6. Mantenibilidad y Modularidad
* **Arquitectura Modular (Clean Architecture / Componentes):** El backend de la API está estructurado en componentes desacoplados (Gestor de Usuarios, Controlador de Catálogo, Controlador de Servicios, Controlador de Reservas y Controlador de Pagos), lo que facilita realizar modificaciones, depuraciones y pruebas unitarias de forma independiente sin afectar al resto del sistema.
* **Despliegue Continuo Automatizado:** Integración con plataformas en la nube (Vercel para Frontend y Render para Backend) que permiten despliegues automatizados directos desde el repositorio de GitHub, reduciendo el esfuerzo operativo de mantenimiento.