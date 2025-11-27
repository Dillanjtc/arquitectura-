# ADR 004 - Elección de Google OAuth 2.0 como sistema de autenticación

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autores**: A. Administrador, D. Cliente

## Contexto y Problema a Resolver

El sistema Curse Fast necesita un mecanismo de autenticación que permita:

1. Identificar usuarios de forma segura  
2. Diferenciar roles para control de acceso  
3. Experiencia de registro/login sin fricción  
4. No gestionar credenciales sensibles internamente  
5. Facilitar integración con Google Académico  

**Requisito del Cliente**: El cliente solicitó específicamente Google OAuth como método de autenticación, priorizando la experiencia del usuario y la seguridad delegada.

**Alternativas consideradas**:

- Google OAuth: SSO con cuentas de Google  
- Autenticación propia: Control total, pero requiere gestión de credenciales  
- Auth0 / Firebase Auth: Servicios externos con costo  
- GitHub OAuth: Menos universal  
- Email Magic Links: Sin contraseñas, pero requiere acceso constante al correo  

## Decisión Tomada

Se selecciona **Google OAuth 2.0** como sistema de autenticación único, implementado mediante Passport.js, en cumplimiento del requisito del cliente y alineado con los objetivos de seguridad y experiencia de usuario.

## Consecuencias

### Positivas

- Cumplimiento de requisito del cliente  
- Experiencia de usuario simplificada  
- Seguridad delegada a Google  
- Adopción universal por usuarios con cuentas Google  
- Integración futura con servicios de Google  
- Costo cero para el volumen estimado  
- Implementación sencilla con Passport.js  
- Cumplimiento regulatorio (GDPR, etc.)  

### Negativas o Riesgos

- Dependencia de proveedor externo  
- Exclusión de usuarios sin cuenta Google  
- Cambios futuros en políticas de Google  
- Preocupaciones sobre privacidad del usuario  
- Limitaciones de personalización en pantalla de login  
- Bloqueo institucional de OAuth en algunas redes  
