# Tradeoff 003 - Google OAuth vs autenticación propia vs Auth0

**Fecha**: 2025-10-21  
**Autores**: A. Administrador

## Contexto

Curse Fast necesita implementar un sistema de autenticación para permitir acceso diferenciado según roles (ver ADR 007). Dado que el equipo es junior y el presupuesto limitado, se busca una solución segura, fácil de implementar y escalable.

Actualmente se ha adoptado **Google OAuth 2.0** como mecanismo de autenticación (ver ADR 004), pero se considera si sería mejor usar una solución propia o un proveedor como Auth0.

Este tradeoff analiza las ventajas y desventajas de cada opción.

## Alternativa A: Google OAuth 2.0

### Ventajas
- Implementación rápida con bibliotecas como Passport.js  
- Seguridad delegada a Google (gestión de contraseñas, MFA, recuperación)  
- Experiencia de usuario fluida (SSO, login con un clic)  
- Verificación de identidad confiable para instituciones educativas  
- Sin necesidad de almacenar contraseñas ni gestionar sesiones complejas  
- Gratuito para uso básico  

### Desventajas
- Dependencia de un proveedor externo  
- Requiere que el usuario tenga cuenta Google  
- Menor control sobre flujo de autenticación y datos del usuario  
- Limitaciones si se desea integrar otros métodos (ej. email/password, redes sociales)  
- No apto para usuarios sin cuenta Google  

## Alternativa B: Autenticación propia (email + contraseña)

### Ventajas
- Control total sobre flujo de login, registro, recuperación  
- Posibilidad de personalizar experiencia de usuario  
- No depende de terceros ni requiere cuentas externas  
- Compatible con cualquier tipo de usuario  

### Desventajas
- Requiere almacenamiento seguro de contraseñas (hashing, salting)  
- Mayor responsabilidad en seguridad (MFA, recuperación, protección contra ataques)  
- Implementación más compleja para equipo junior  
- Mayor riesgo legal si hay brechas de seguridad  
- Requiere desarrollo y mantenimiento continuo  

## Alternativa C: Auth0

### Ventajas
- Plataforma especializada en autenticación y autorización  
- Soporte para múltiples métodos (Google, email/password, redes sociales, enterprise)  
- Seguridad robusta y cumplimiento normativo (GDPR, SOC2, etc.)  
- Panel de administración para gestión de usuarios y roles  
- SDKs y documentación extensa  

### Desventajas
- Costos mensuales si se supera el tier gratuito  
- Curva de aprendizaje para configuración avanzada  
- Dependencia de proveedor externo  
- Puede ser excesivo para un MVP con pocos usuarios  

## Decisión actual

Se mantiene **Google OAuth 2.0** como solución de autenticación para el MVP de Curse Fast, priorizando simplicidad, seguridad delegada y velocidad de implementación. Se evaluará migrar a Auth0 o desarrollar una solución propia si se requiere mayor control, soporte para usuarios sin cuenta Google, o integración con múltiples métodos de autenticación.

## Criterios de reevaluación

- Usuarios sin cuenta Google representan >20% del tráfico  
- Necesidad de autenticación por email/password o redes sociales  
- Requerimientos de seguridad avanzados (MFA, auditoría, recuperación)  
- Escalamiento del sistema a múltiples dominios o clientes  
- Presión legal o institucional para controlar el flujo de autenticación  
