# ADR-005 Integración de Pagos con MercadoLibre

## Contexto
El sistema necesita procesar pagos de clientes de manera segura y eficiente. Para esto, se integrará con la pasarela de pagos externa proporcionada por **MercadoLibre**, que ofrece soporte regional y cumple con estándares de seguridad.

El microservicio de Pagos será responsable de interactuar con la API de MercadoLibre para realizar transacciones, manejar confirmaciones de pago y emitir eventos de notificación a otros microservicios.

## Decisión tomada
Se decidió integrar el sistema de pagos con **MercadoLibre** mediante su **API REST**, utilizando los siguientes enfoques:
1. **OAuth 2.0**: Para autenticación segura con la plataforma.
2. **API REST**: El microservicio de Pagos se conectará a la API REST de MercadoLibre para procesar los pagos, obtener información sobre las transacciones y manejar confirmaciones.
3. **TLS**: Para garantizar la confidencialidad de las comunicaciones.
4. **Manejo asíncrono**: El microservicio de Pagos emitirá eventos de confirmación al bus de eventos para desacoplar la interacción con otros servicios.

## Razonamiento
- **Seguridad**: OAuth 2.0 y TLS aseguran que las transacciones sean protegidas y que solo los servicios autorizados interactúen con MercadoLibre.
- **Escalabilidad**: Al procesar pagos de forma asíncrona, se evita bloquear el flujo de pedidos en caso de problemas con la pasarela externa.
- **Compatibilidad**: MercadoLibre es una solución probada en la región, lo que minimiza riesgos de incompatibilidad o problemas regulatorios.

## Consecuencias
**Ventajas**:
- Transacciones seguras y confiables.
- Desacoplamiento del procesamiento de pagos mediante eventos asíncronos.
- Cumplimiento de normativas regionales de pagos.

**Desventajas**:
- Dependencia de la disponibilidad y desempeño de la plataforma de MercadoLibre.
- Necesidad de manejar errores y tiempos de espera en la comunicación.

## Implementación inicial
1. **Configurar la API de MercadoLibre**:
   - Obtener las credenciales necesarias para interactuar con la API de MercadoLibre (client ID, client secret).
   - Implementar la autenticación OAuth 2.0 para garantizar el acceso autorizado a la API.
   
2. **Configurar TLS**:
   - Asegurar que todas las comunicaciones con MercadoLibre sean seguras utilizando TLS.

3. **Publicación de eventos**:
   - Configurar el microservicio de Pagos para publicar eventos como `payments.completed` o `payments.failed` en el bus de eventos para que otros microservicios reaccionen.
