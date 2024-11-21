# ADR-003 Seguridad en Clientes con OAuth 2.0

## Contexto
El módulo de Clientes maneja datos sensibles (información personal y autenticación de usuarios) y es crítico para garantizar la seguridad del sistema en general. Además, el sistema debe permitir a los clientes autenticarse de forma segura y controlar el acceso a los recursos de manera granular. Dada la migración a microservicios, es esencial contar con un esquema de autenticación y autorización que sea escalable y compatible con una arquitectura distribuida.

## Decisión tomada
Se decidió implementar **OAuth 2.0** para la autenticación y autorización en el módulo de Clientes, utilizando un proveedor de tokens centralizado. Esto incluye:
1. Un servidor central de autorización para gestionar las credenciales y emitir tokens de acceso.
2. Cada microservicio verificará los tokens emitidos para autenticar solicitudes y aplicar políticas de autorización basadas en **scopes** (permisos asignados a los tokens).

## Razonamiento
- **Desacoplamiento de la seguridad**: OAuth 2.0 separa la lógica de autenticación y autorización del negocio principal, permitiendo que los microservicios se concentren en sus responsabilidades específicas.
- **Compatibilidad con microservicios**: El uso de tokens permite una gestión eficiente de las solicitudes entre servicios en una arquitectura distribuida.
- **Estándar probado**: OAuth 2.0 es un estándar ampliamente utilizado y soportado, con múltiples implementaciones listas para usar (por ejemplo, Keycloak, Auth0 o Spring Authorization Server).

## Alternativas consideradas
1. **JWT sin OAuth 2.0**:
   - **Ventajas**: Implementación más simple y directa.
   - **Desventajas**: No ofrece un control centralizado de los tokens ni un mecanismo estándar para scopes o expiración de tokens.

2. **OAuth 2.0 (Seleccionada)**:
   - **Ventajas**: Control centralizado de autenticación y autorización. Escalable para múltiples microservicios y compatible con estándares modernos.
   - **Desventajas**: Requiere configurar y mantener un servidor de autorización.

## Consecuencias
**Ventajas**:
- Mejora la seguridad mediante un sistema centralizado de autenticación y autorización.
- Facilita la gestión de permisos a nivel granular mediante scopes.
- Compatible con otras plataformas externas que también utilicen OAuth 2.0.
- Alineado con estándares modernos, reduciendo riesgos de incompatibilidad.

**Desventajas**:
- Requiere un esfuerzo inicial para configurar el servidor de autorización y gestionar los tokens.
- Añade un nivel de complejidad operacional, especialmente en sistemas distribuidos.
