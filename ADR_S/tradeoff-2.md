# Tradeoff 002 - SPA con React vs SSR con Next.js

**Fecha**: 2025-10-21  
**Autores**: A. Administrador

## Contexto

Curse Fast utiliza una arquitectura separada con frontend SPA (React + Vite) y backend API REST (ver ADR 005, ADR 008, ADR 013). Esta elección prioriza velocidad de desarrollo, simplicidad y experiencia interactiva para los usuarios.

Sin embargo, se considera la posibilidad de migrar a **Server-Side Rendering (SSR)** con Next.js para mejorar aspectos como SEO, rendimiento inicial y control de rutas. Este tradeoff analiza las ventajas y desventajas de mantener una SPA vs adoptar SSR.

## Alternativa A: SPA con React

### Ventajas
- Experiencia de desarrollo rápida y moderna (Vite, HMR, JSX)  
- Interactividad fluida sin recargas de página  
- Despliegue simple como archivos estáticos (Vercel, Netlify)  
- Separación clara entre frontend y backend  
- Ideal para aplicaciones tipo dashboard o catálogo interactivo  
- Bajo consumo de recursos en el cliente tras carga inicial  

### Desventajas
- SEO limitado (contenido renderizado en el cliente)  
- Tiempo de carga inicial más alto (JavaScript + datos)  
- Menor control sobre headers HTTP y prerendering  
- Requiere configuración adicional para compartir metadatos sociales (Open Graph, Twitter Cards)  
- No ideal para contenido indexable por motores de búsqueda  

## Alternativa B: SSR con Next.js

### Ventajas
- SEO optimizado (contenido renderizado en el servidor)  
- Tiempo de carga inicial más rápido para usuarios nuevos  
- Control total sobre rutas, headers, prerendering y metadatos  
- Soporte para generación estática (SSG) y renderizado híbrido  
- Mejor rendimiento en dispositivos lentos o redes débiles  
- Integración directa con Vercel para despliegue y análisis  

### Desventajas
- Curva de aprendizaje más alta (getServerSideProps, routing, configuración)  
- Mayor complejidad en despliegue y testing  
- Requiere backend acoplado al frontend para SSR dinámico  
- Menor separación entre frontend y backend si se usa API interna  
- Puede aumentar el costo de hosting si se renderiza en tiempo real  

## Decisión actual

Se mantiene la arquitectura **SPA con React + Vite** para el MVP de Curse Fast, priorizando simplicidad, velocidad de desarrollo y bajo costo. El enfoque SPA es suficiente para un catálogo informativo con usuarios autenticados y filtros dinámicos.

## Criterios de reevaluación

- Necesidad de mejorar SEO para indexación de recursos  
- Requerimientos de compartir contenido en redes sociales con metadatos enriquecidos  
- Métricas de rendimiento muestran latencia alta en carga inicial  
- Aumento de tráfico orgánico desde buscadores  
- Necesidad de prerenderizar contenido para accesibilidad o compatibilidad con navegadores antiguos  
