# ADR002 - Arquitectura Basada en Eventos (EDA)

## Contexto
Se requiere una comunicación eficiente entre microservicios desacoplados. El patrón de comunicación asíncrona mediante un **bus de eventos** permite que los microservicios publiquen eventos y otros los consuman sin necesidad de una interacción directa, logrando desacoplamiento y mejor tolerancia a fallos.

## Decisión tomada
Se decide utilizar un **bus de eventos** para manejar la comunicación entre los microservicios, especialmente en flujos críticos como el procesamiento de pedidos y pagos. La herramienta 
seleccionada será **Kafka** (o **RabbitMQ**) por sus características de alta disponibilidad, escalabilidad y soporte para comunicación asíncrona.

## Alternativas consideradas
- **Comunicación directa (síncrona) entre microservicios:**
-- Ventajas: Implementación inicial más simple.
-- Desventajas: Aumenta el acoplamiento y reduce la resiliencia.
- **Uso de un bus de eventos**:
-- Ventajas: Desacoplamiento, alta resiliencia y escalabilidad.
-- Desventajas: Mayor complejidad en la configuración inicial.

## Razonamiento
Un bus de eventos proporciona una comunicación asíncrona, mejorando la resiliencia y escalabilidad del sistema al reducir el acoplamiento entre los microservicios. Además, facilita la integración futura de nuevos servicios sin alterar los existentes.

## Consecuencias
**Ventajas**: 
- Desacoplamiento, resiliencia y escalabilidad mejoradas. Permite incorporar nuevos servicios sin afectar los existentes.
**Desventajas**:
- Mayor complejidad en la configuración y monitoreo del bus de eventos.
