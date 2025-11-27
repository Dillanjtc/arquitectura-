# ADR 001 - Elección de Node.js con Express como framework backend

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autores**: A. Administrador, D. Cliente

## Contexto y Problema a Resolver

El proyecto "Curse Fast" requiere un servidor backend que pueda gestionar:

1. Búsqueda y filtrado de recursos educativos en tiempo real  
2. Integración con servicios externos (DevTalles, Coursera, Google Académico)  
3. Autenticación de usuarios mediante Google OAuth  
4. API REST para comunicación con el frontend  
5. Manejo de conexiones concurrentes de hasta 1,000 usuarios  

El equipo de desarrollo tiene experiencia limitada (nivel junior) y necesita una tecnología con buena documentación, curva de aprendizaje moderada y que permita desarrollo rápido dentro del presupuesto limitado.

**Alternativas consideradas**:

- Node.js + Express: JavaScript en backend, ecosistema amplio, arquitectura orientada a eventos  
- Python + Django: Framework robusto, más opinado, requiere conocimientos de Python  
- PHP + Laravel: Framework maduro, hosting económico, sintaxis diferente a JavaScript  
- Java + Spring Boot: Muy robusto pero complejo, curva de aprendizaje pronunciada  

## Decisión Tomada

Se selecciona **Node.js con Express.js** como plataforma de desarrollo backend para Curse Fast, por su simplicidad, familiaridad con JavaScript, y facilidad para estructurar APIs REST de forma mantenible.

## Consecuencias

### Positivas

- Lenguaje unificado (JavaScript en frontend y backend)  
- Desarrollo rápido con Express  
- Ecosistema npm amplio  
- Arquitectura asíncrona ideal para operaciones I/O  
- Organización clara del código  
- Hosting económico  

### Negativas o Riesgos

- Experiencia limitada del equipo con asincronía  
- Tipado débil de JavaScript  
- Rendimiento limitado en operaciones CPU-intensive  
- Riesgo de código desorganizado si no se establecen buenas prácticas  
