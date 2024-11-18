# Atributos de calidad

En este documento, se enumeran algunos requisitos que asumimos que serían importantes para el sistema.

## Escalabilidad

- Se espera un número creciente de clientes y pedidos concurrentes.
- Se debe añadir soporte para manejar miles de pedidos simultáneos.
- Capacidad de escalar horizontalmente los servicios críticos (Clientes, Pedidos, Rutas).

## Disponibilidad

- Las funcionalidades críticas deben estar siempre disponibles.
- Clientes, Pagos y Reparto/Rutas deben tener una disponibilidad alta.
- Uso de replicación de servicios y bases de datos para evitar puntos únicos de falla.

## Modificabilidad

- Los microservicios deben ser independientes y permitir actualizaciones sin afectar el resto del sistema.
- Separación clara de responsabilidades para facilitar cambios en módulos específicos.

## Seguridad

- El manejo de datos sensibles de clientes y transacciones requiere protección avanzada.
- Autenticación y autorización mediante estándares.
- Auditorías completas para módulos sensibles (Clientes, Pagos).

## Rendimiento

- Se debe garantizar que las operaciones clave sean rápidas y eficientes.
- Se requiere un tiempo de respuesta inferior a 1 segundo para la mayoría de las operaciones.
- Se requiere un procesamiento de pedidos en menos de 5 segundos en condiciones normales.

## Tolerancia a fallos

- El sistema debe continuar funcionando ante fallos parciales.
- Se requiere soporte para recuperación automática en caso de caídas de servicios.

## Usabilidad
- Los usuarios deben interactuar fácilmente con las aplicaciones cliente (PC y móvil).
