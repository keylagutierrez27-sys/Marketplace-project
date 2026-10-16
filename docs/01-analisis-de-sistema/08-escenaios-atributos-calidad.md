# 8 Escenarios de Atributos de Calidad

Son pruebas concretas para medir cada atributo. Los valores son metas; se reportan con concurrencia, tasa de errores y percentiles de latencia.

| ID | Atributo | Fuente del estímulo | Estímulo | Artefacto | Respuesta del sistema | Medida |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **ESC-01** | Seguridad | Usuario externo no autenticado | Intenta crear una orden sin token Bearer válido | `auth / API REST` | Rechaza la solicitud y registra el intento en la auditoría | HTTP 401 en menos de 100 ms y 0% de fuga de datos |
| **ESC-02** | Rendimiento | 500 compradores concurrentes | Buscan en el catálogo en periodo de matrícula | `catalog / PostgreSQL` | La CDN sirve lo estático y los índices B-Tree agilizan la consulta | Latencia de API inferior a 300 ms en el 95% de las peticiones |
| **ESC-03** | Modificabilidad | Equipo de desarrollo | Reemplaza el proveedor de correo (SendGrid por Nodemailer / SMTP) | `notifications / infraestructura` | Se crea un nuevo adaptador que implementa `NotificationPort` sin tocar el dominio | Cambio desplegado en menos de 4 horas sin modificar los casos de uso |
| **ESC-04** | Disponibilidad | Proveedor cloud | Falla temporal del contenedor de la API | Backend monolítico | La plataforma reinicia el contenedor y Cloudflare degrada con suavidad | Recuperación en 2 minutos y disponibilidad mensual objetivo del 99.5%, con un plan sin suspensión por inactividad |
| **ESC-05** | Escalabilidad / integridad | Pico de 1,500 usuarios en campus | Reservas simultáneas de la misma sala y horario | `booking / PostgreSQL` | El backend *stateless* atiende las peticiones y la base aplica la restricción de exclusión | 0% de traslapes y latencia de API inferior a 1.5 s |
| **ESC-06** | Costo | Operación mensual continua | Tráfico, *vouchers* e invocaciones a la API de IA durante un mes | Infraestructura cloud | El consumo se mantiene en los límites de las capas elegidas y se activan alertas | Costo mensual dentro de S/ 100 (dominio `.PE` prorrateado y, si hace falta, plan básico del backend) |
| **ESC-07** | Privacidad | Estudiante autenticado | Intenta ver o descargar el *voucher* de una orden ajena | `orders / Storage` | Deniega el acceso y registra el intento; no genera URL firmada | HTTP 403 y 0 descargas de *vouchers* ajenos |