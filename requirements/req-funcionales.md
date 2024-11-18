# Requerimientos Funcionales

Este documento contiene los requerimientos funcionales obtenidos en base a la descripción del sistema a diseñar.

## Módulo Clientes (Crítico)

- Gestión de datos personales: prioridad para proteger datos sensibles (nombre, dirección, teléfono).
- Búsqueda de clientes por criterios específicos (ID, nombre, historial de pedidos).
- Actualización de información personal, garantizando consistencia.
- Soporte para múltiples tipos de usuarios (administradores y operadores).

## Pedidos (Semi-crítico)

- Crear nuevos pedidos para clientes.
- Gestión de intentos (máximo 3 intentos por pedido fallido).
- Control de flujo de estados para cada pedido
- Capacidad para cancelar pedidos en estado previo a aceptación.
- Manejo de concurrencia para múltiples pedidos simultáneos.

## Reparto y Rutas (Crítico)

- Asignación de pedidos a rutas y camiones disponibles.
- Optimización de rutas utilizando dos algoritmos (por ejemplo, en función de tiempo o distancia).
- Notificaciones en caso de demoras o cambios en rutas.
- Integración con servicios de mapas y geolocalización.

## Estadísticas (No crítico)

- Generación de reportes sobre pedidos procesados en tiempo real.
- Generación de reportes sobre estado actual de los camiones.
- Generación de reportes sobre comportamiento de clientes (frecuencia de pedidos, métodos de pago).
- Exportación a formatos estándar (CSV, PDF).

## Incidencias (Semi-crítico)

- Registro de incidencias asociadas a rutas o pedidos (camión averiado, pedido no entregado).
- Actualización del estado de las incidencias.
- Notificación automática al gestor de flota.
- Búsqueda de incidencias por tipo, prioridad o estado.

## Pagos (Crítico)

- Integración con la pasarela de pagos de MercadoLibre.
- Verificación de pagos exitosos antes de autorizar pedidos.
- Registro de transacciones (fecha, monto, estado).
- Auditoría completa de transacciones.
