# ADR 005 - Arquitectura separada Frontend-Backend (SPA + API REST)

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autores**: A. Administrador, D. Cliente

## Contexto y Problema a Resolver

El proyecto Curse Fast debe estructurarse de manera que permita:

1. Desarrollo organizado y mantenible para un equipo junior  
2. Separación clara de responsabilidades (UI vs lógica de negocio)  
3. Escalabilidad futura (posible app móvil reutilizando la misma API)  
4. Testing independiente de frontend y backend  
5. Facilitar el trabajo en paralelo si el equipo crece  

El equipo de desarrollo tiene experiencia limitada y necesita una estructura que sea fácil de entender, ordenada y que evite el código "spaghetti".

**Alternativas consideradas**:

- Monolito con Server-Side Rendering (SSR): Frontend y backend en el mismo servidor  
- Arquitectura Separada (SPA + API): Frontend React independiente consumiendo API REST  
- Arquitectura Serverless: Funciones independientes en la nube (demasiado complejo para equipo junior)  

## Decisión Tomada

Se adopta una **arquitectura separada con Frontend (React SPA) y Backend (Node.js/Express API REST)** como aplicaciones independientes que se comunican mediante HTTP.

## Consecuencias

### Positivas

- Separación clara de responsabilidades  
- Organización del código por aplicación  
- Desarrollo y despliegue independientes  
- Reutilización futura de la API  
- Testing desacoplado entre frontend y backend  
- Escalabilidad diferenciada por componente  
- Uso de tecnologías especializadas  
- Onboarding simplificado para nuevos desarrolladores  

### Negativas o Riesgos

- Complejidad operacional inicial (dos servidores en desarrollo)  
- Configuración adicional de CORS  
- Duplicación de validaciones entre frontend y backend  
- SEO limitado por ser SPA  
- Dos despliegues independientes  
- Latencia de red por llamadas HTTP adicionales  
