# ADR-001 Estrategia de Migración: Strangler Pattern

## Contexto

El sistema actual es un monolito que debe ser migrado a una arquitectura de microservicios para cumplir con los requerimientos funcionales y los atributos de calidad definidos. La migración debe minimizar riesgos, mantener la disponibilidad del sistema y garantizar una modularización adecuada para facilitar la escalabilidad y la evolución futura.

## Decisión tomada

Se seleccionó la estrategia de migración Strangler Pattern como referencia arquitectónica para la transición a microservicios. Esta estrategia permite encapsular el monolito existente con un API Gateway mientras se extraen funcionalidades de manera incremental hacia microservicios.

## Alternativas consideradas

- **Big Bang:**
-- Ventajas: Transición rápida hacia microservicios.
-- Desventajas: Alto riesgo de interrupciones y errores debido a la magnitud del cambio.

- **Desacoplamiento gradual:**
-- Ventajas: Reducción de riesgos al dividir la migración en etapas.
-- Desventajas: Similar a Strangler Pattern, pero sin capa inicial de protección.

- **Strangler Pattern:**
-- Ventajas: Mantiene la funcionalidad del monolito mientras se extraen servicios. Reduce el riesgo de fallos al desacoplar funcionalidades de forma incremental.
-- Desventajas: Complejidad inicial en la configuración del "strangler".

## Razonamiento
La estrategia Strangler Pattern fue seleccionada debido a su capacidad para mantener la disponibilidad del sistema durante la migración, su enfoque modular y el bajo riesgo de interrupciones. Esta decisión está alineada con los drivers arquitectónicos prioritarios.

## Consecuencias

**Ventajas:**
- Modularización progresiva, lo que permite priorizar funcionalidades críticas como Clientes y Pedidos.
- Baja probabilidad de fallos gracias a la coexistencia inicial del monolito y los microservicios.
- Facilita la transición sin interrumpir el servicio existente.

**Desventajas:**
- Complejidad inicial en la configuración del API Gateway y el manejo de datos compartidos.
- Requiere inversión en herramientas de monitoreo y gestión de microservicios.

## Artefactos generados
- Diagrama de transición del sistema: Representa el monolito encapsulado por un API Gateway, con los primeros servicios desacoplados.