# ADR 013 - Elección de arquitectura SPA + API REST con backend monolítico modular

**Fecha**: 2025-10-20  
**Estado**: Aceptado  
**Autores**: A. Administrador

## Contexto y Problema a Resolver

El proyecto Curse Fast busca democratizar el acceso a recursos educativos gratuitos mediante un catálogo informativo accesible para estudiantes, profesionales e instituciones. Se espera un crecimiento moderado (~1,500 usuarios en 12–24 meses) y funcionalidades básicas como búsqueda por filtros, autenticación con Google, y comentarios.

El equipo de desarrollo es junior, por lo que se requiere una arquitectura clara, mantenible y de bajo costo, que permita escalar en el futuro sin introducir complejidad innecesaria desde el inicio.

Se necesita definir el estilo arquitectónico general del sistema, considerando:

- Separación entre frontend y backend  
- Comunicación eficiente y estándar  
- Facilidad de desarrollo y despliegue  
- Posibilidad de evolución hacia microservicios si el crecimiento lo exige  

## Alternativas Consideradas

- **Monolítico con SSR**: Menor separación, menos escalable, no compatible con SPA moderna  
- **Arquitectura en Capas**: Aplicable internamente, pero no como estilo principal del sistema  
- **Microservicios**: Escalable pero complejo para equipo junior y volumen actual  
- **SOA / EDA / Microkernel / P2P**: No aplicables al caso de uso ni al tipo de aplicación  
- **SPA + API REST con backend monolítico modular**: Separación clara, bajo acoplamiento, escalabilidad progresiva  

## Decisión Tomada

Se adopta una **arquitectura basada en SPA + API REST con backend monolítico modular**, que combina los siguientes estilos arquitectónicos:

- **Cliente-Servidor**: React SPA como cliente, Express como servidor  
- **REST**: Comunicación entre frontend y backend mediante API REST con JSON  
- **Monolítico Modular**: Backend estructurado en módulos (rutas, controladores, servicios) dentro de una sola aplicación  

## Consecuencias

### Positivas

- **Claridad y Mantenibilidad**: Separación de responsabilidades facilita el trabajo del equipo junior  
- **Desarrollo Independiente**: Frontend y backend pueden evolucionar por separado  
- **Escalabilidad Progresiva**: Posibilidad de extraer microservicios en el futuro si el tráfico o la complejidad lo requieren  
- **Compatibilidad con Apps Móviles**: La API REST puede ser reutilizada por otras interfaces (ej. React Native)  
- **Despliegue Económico**: Cada componente puede alojarse en servicios especializados de bajo costo  
- **Estándares Universales**: REST y JSON son ampliamente soportados y documentados  
- **Base para SSR futuro**: Si se requiere SEO, se puede migrar a Next.js sin reestructurar todo el sistema  

### Negativas o Riesgos

- **Complejidad Operacional Inicial**: Requiere configurar y coordinar múltiples entornos (frontend, backend, base de datos)  
- **Duplicación de Validaciones**: Validaciones deben hacerse tanto en frontend como en backend  
- **Latencia de Red**: Cada interacción requiere una llamada HTTP, añadiendo latencia  
- **Sin caché en MVP**: Mayor carga en la base de datos hasta que se implemente caché  
- **Migración a microservicios**: Si se requiere, implicará refactorización y reestructuración del backend  

## Estrategia de Mitigación

- Estructurar el backend con separación clara de módulos para facilitar futura extracción  
- Monitorear métricas de rendimiento desde el lanzamiento  
- Documentar endpoints REST con Swagger/OpenAPI  
- Evaluar implementación de caché (Redis) si el rendimiento lo requiere  
- Mantener la API REST como contrato estable para futuras interfaces  
