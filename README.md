# 📘 Entrega Final - Prueba Práctica

## 👥 Integrantes: Mathew Avilés, Jorge Brito


## 🔗 Trabajo Práctico 1
link: https://github.com/MathewAviles/Trabajo-pr-ctico-1.git

Preguntas:
1. ¿Qué riesgos implica depender de una fuente no oficial como la API pública de ESPN y cómo podrían mitigar estos problemas?

Los riezgos que implica depender de una fuente no oficial como la API pública de ESPN son:
    Las url se pueden romper por cambios que se hagan sin aviso
    El formato Json puede tener inconsistencias si se modifica de un día para otro
    Las consultas masivas puede provocar un bloqueo en el acceso a la API
    Las APIs no oficiales pueden violar terminos y condiciones de uso
    Los datos no podrían ser los correctos o estar incompletos

Como mitigarlos:

    Priorizando el uso de apps oficiales
    Crear capas de servicio que encapsule el acceso a ESPN, así si cambia la funete, solo se modifica esa capa
    Guardar resuldos en cache para reducir las consultas
    Usar TTL para evitar el exceso de llamadas y caidas temporales
    Tener un sistema de detección de fallos en la API lo antes posible
    Tener un respaldo como una segunda funete de datos


2. ¿Qué estrategias implementarían para escalar la API si muchos usuarios consultan resultados simultáneamente?

Las estrategias que se pueden implementar para escalar la API con muchos usuarios simultáneos son:

    Uso de cache en memoria como Redis para almacenar respuestas frecuentes
    Implementar cache HTTP o CDN para datos que no cambian constantemente
    Reducir el número de llamadas a la fuente original de datos
    Ejecutar múltiples instancias del backend (escalado horizontal)
    Mantener la API stateless para facilitar la escalabilidad
    Limitar el número de consultas por usuario o IP (rate limiting)

¿Cómo implementarlas?

    Implementar sistemas de cache como Redis para mejorar tiempos de respuesta
    Usar balanceadores de carga para distribuir las solicitudes entre servidores
    Configurar rate limiting para evitar abusos del sistema
    Diseñar la API de forma stateless para facilitar el escalado horizontal
    Optimizar consultas a base de datos y usar réplicas cuando sea necesario
    Implementar colas (como RabbitMQ o Celery) para procesos en segundo plano

    ---

---

## 📄 Trabajo Practico 2

## 🔗 Links del Proyecto

- 📌 Parte 1: https://github.com/PJSA0127/Parte-1-Construccion-del-API
- 🌐 Parte 2: https://github.com/PJSA0127/Parte-2-Web-Scrapping


### 1) Abuso del sistema para envío masivo de correos (spam)

Un atacante podría automatizar solicitudes al sistema para enviar grandes volúmenes de correos en poco tiempo, utilizando scripts o bots. Esto convertiría el sistema en una herramienta de spam.

Las consecuencias incluyen:

- Inclusión del servidor en listas negras (blacklist)
- Bloqueo de correos legítimos
- Consumo excesivo de recursos (CPU, memoria y red)
- Degradación o caída del servicio

**Medidas de mitigación:**

- Autenticación obligatoria
- Rate limiting por usuario o IP
- Validación de contenido y destinatarios
- Uso de CAPTCHA
- Monitoreo de actividad sospechosa

---

### 2) Defensa contra múltiples procesos de scraping concurrentes

Un atacante podría lanzar múltiples procesos de scraping simultáneamente, saturando los recursos del servidor (CPU, memoria y red), lo que puede provocar lentitud o caída total del sistema (denegación de servicio).

El impacto principal es la pérdida de disponibilidad del sistema para usuarios legítimos.

**Medidas de prevención:**

- Limitar la cantidad de procesos concurrentes
- Implementar rate limiting
- Uso de colas de tareas (Celery o Redis)
- Autenticación y control de acceso
- Monitoreo y alertas del sistema

---
