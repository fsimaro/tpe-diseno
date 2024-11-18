# Trabajo Práctico Especial - Diseño de Sistemas de Software 2024

## Descripción del sistema a diseñar
Una compañía de productos alimenticios pretende migrar su sistema existente, que posee una
arquitectura de naturaleza monolítica, hacia una arquitectura basada en microservicios, de
manera que la nueva arquitectura sea menos rígida y sea más fácil de evolucionar.
La arquitectura existente cuenta con una parte de clientes PC y móvil que acceden a los datos
de la empresa alojados en 2 Bases de datos SQL (Clientes, Pedidos). La base de Clientes
contiene datos de clientes y pagos mientras que la base de Pedidos se encarga de almacenar
los datos restantes. El acceso actual se pretende que sea sustituido por protocolos HTTP/REST
que faciliten el acceso desde los clientes PC y móvil.
La lógica de negocio de la empresa cuenta con los siguientes **módulos funcionales**, con
diferentes grados de criticidad.

- Clientes (crítico): Esta funcionalidad permite a acceder los datos de personales de los
clientes.
- Pedidos (semi-crítico): Esta funcionalidad permite a los clientes realizar pedidos de los
productos a la empresa. Si un cliente intenta realizar un pedido se le permite un número
máximo de 3 intentos. Las prestaciones y escalabilidad del sistema van a depender del
número de pedidos por hora. El sistema de pedidos pasa siempre por una cadena de tres
fases, a saber: preprocesado del pedido, autorización y aceptación, de manera que no es
posible pasar a un estado si no se ha procesado correctamente el estado anterior.
- Reparto y rutas (crítico): Este componente complejo cuenta con una funcionalidad que es
necesario desacoplar y gestiona el reparto de las flotas de transporte a los clientes y las
rutas de los camiones. La gestión cuenta con 2 algoritmos de optimización que se
seleccionan en función de la demora del camión.
- Estadísticas (no crítico): Esta funcionalidad proporciona información valiosa sobre el estado
de los pedidos y la situación en tiempo real de los camiones. Las estadísticas proporcionan
también información de clientes.
- Incidencias (semi-crítico): Esta funcionalidad reporta a los gestores de las rutas cualquier
tipo de incidencia (por ej., camión averiado, reparto no realizado, etc.)
- Pagos (crítico): Esta funcionalidad se apoya en una pasarela de pago externa que
proporciona la empresa MercadoLibre para garantizar la seguridad de los pagos y la
compatibilidad con otros clientes.

Asimismo, la gestión de los pedidos debe proporcionar una forma de gestionar todas las
peticiones de los pedidos de clientes y gestionar las incidencias en el reparto.
La nueva arquitectura debe contar con los elementos software y/o tecnología adecuados para
poder ejecutar los microservicios.
