# Restricciones

En este documento, se enumeran algunas restrcciones obtenidos en base a la descripción del sistema a diseñar.

## Restricciones Tecnológicas

- Uso de protocolos HTTP/REST: Toda interacción entre los clientes (PC y móvil) y el backend debe realizarse mediante APIs HTTP/REST.
- Integración con la pasarela de pagos MercadoLibre: El módulo de Pagos debe conectarse a la pasarela externa proporcionada por MercadoLibre.

## Restricciones de Infraestructura

- Bases de datos separadas por dominio: Las bases de datos actuales (Clientes y Pedidos) deben mantenerse como sistemas separados.
- La solución debe ser accesible desde dispositivos móviles y de escritorio, sin depender de tecnologías específicas de cliente.

## Restricciones de Negocio

- Modularización por dominio funcional: Los módulos funcionales actuales deben traducirse en servicios independientes (Clientes, Pedidos, etc.).
- Cadena de procesos en Pedidos: Los pedidos deben pasar obligatoriamente por tres fases secuenciales (preprocesado, autorización y aceptación).
- Un cliente tiene un máximo de 3 intentos fallidos para realizar un pedido.

## Restricciones de Atributos de Calidad

- Escalabilidad: El sistema debe poder escalar horizontalmente para soportar picos de demanda, especialmente en Pedidos y Pagos.
- Alta disponibilidad (99.9%): Los módulos críticos (Clientes, Rutas y Pagos) deben estar disponibles prácticamente todo el tiempo.

## Restricciones de Seguridad

- Cumplimiento de estándares de seguridad: Toda comunicación debe estar encriptada (TLS/SSL).
- Autenticación y autorización deben seguir estándares.
- Almacenar datos sensibles (como contraseñas) encriptados.

## Restricciones Operativas

- Registro y auditoría: El sistema debe mantener registros completos de operaciones sensibles (por ejemplo, creación de pedidos, transacciones de pago).
- Compatibilidad con infraestructura existente: La solución debe ser compatible con las bases de datos SQL actuales.