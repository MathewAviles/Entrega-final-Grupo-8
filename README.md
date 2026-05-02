Entrega final prueba práctica

Integrantes:Mathew Avilés


Trabajo Práctico 1 
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