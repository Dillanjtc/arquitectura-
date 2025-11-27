# Tradeoff 001 - Monolito modular vs Microservicios

**Fecha**: 2025-10-21  
**Autores**: A. Administrador

## Contexto

Curse Fast ha adoptado una arquitectura separada con frontend SPA y backend API REST (ver ADR 005 y ADR 013). Actualmente, el backend está diseñado como un **monolito modular** en Node.js/Express, estructurado por rutas, controladores y servicios.

A medida que el proyecto crece y se considera incorporar funcionalidades como comentarios, moderación, métricas o dashboards, surge la pregunta de si mantener el monolito o migrar hacia una arquitectura de **microservicios**.

Este tradeoff analiza las ventajas y desventajas de ambas opciones para orientar futuras decisiones de evolución arquitectónica.

## Alternativa A: Monolito modular

### Ventajas
- Simplicidad de desarrollo y despliegue  
- Menor complejidad operativa (una sola base de código, un solo servidor)  
- Fácil de entender para equipos junior  
- Comunicación interna directa (sin red ni APIs entre módulos)  
- Testing más sencillo (todo en un solo entorno)  
- Menor costo de infraestructura y monitoreo  

### Desventajas
- Escalabilidad limitada por componente (todo se escala junto)  
- Riesgo de acoplamiento entre módulos si no se mantiene disciplina  
- Dificultad para aislar fallos (un error puede afectar todo el sistema)  
- Despliegues más riesgosos (todo se actualiza junto)  
- Menor flexibilidad tecnológica (todos los módulos comparten stack)  

## Alternativa B: Microservicios

### Ventajas
- Escalabilidad independiente por servicio (ej. comentarios, búsqueda, autenticación)  
- Aislamiento de fallos (un servicio puede fallar sin afectar los demás)  
- Despliegues independientes por servicio  
- Flexibilidad tecnológica (cada servicio puede usar el stack más adecuado)  
- Mejor alineación con equipos distribuidos o especializados  

### Desventajas
- Mayor complejidad operativa (orquestación, monitoreo, logging, tracing)  
- Requiere infraestructura adicional (gateway, balanceadores, contenedores, etc.)  
- Curva de aprendizaje más alta para el equipo  
- Comunicación entre servicios vía red (latencia, errores, seguridad)  
- Testing más complejo (requiere mocks, entornos distribuidos)  
- Costos mayores en hosting, mantenimiento y observabilidad  

## Decisión actual

Se mantiene la arquitectura **monolítica modular** para el backend de Curse Fast, priorizando simplicidad, velocidad de desarrollo y bajo costo. La estructura modular permite separar responsabilidades y facilita una futura migración a microservicios si el crecimiento lo exige.

## Criterios de reevaluación

- Tráfico concurrente >5,000 usuarios  
- Incorporación de funcionalidades con alta carga o desacoplamiento natural (ej. comentarios, métricas, búsqueda avanzada)  
- Necesidad de despliegues independientes por servicio  
- Aumento del equipo técnico con especialización por dominio  
- Problemas recurrentes de acoplamiento o escalabilidad en el monolito  
