# ADR 009 - Patrón de comunicación mediante API REST con JSON

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autor**: A. Administrador

## Contexto y Problema a Resolver

El frontend (React) y el backend (Node.js/Express) necesitan comunicarse para:

1. Autenticar usuarios  
2. Buscar recursos con filtros  
3. Obtener detalles de recursos específicos  
4. Agregar nuevos recursos (instituciones)  
5. Actualizar y eliminar recursos (futuro)  

Se requiere definir el protocolo y formato de comunicación entre ambas aplicaciones.

**Alternativas consideradas**:

- REST con JSON  
- GraphQL  
- gRPC  
- WebSockets  
- REST con XML  

## Decisión Tomada

Se implementa una **API REST utilizando JSON** como formato de intercambio de datos, siguiendo las convenciones estándar de HTTP (GET, POST, PUT, DELETE).

## Consecuencias

### Positivas

- Estándar de la industria ampliamente documentado  
- Simplicidad en el mapeo de operaciones CRUD  
- JSON nativo en JavaScript  
- Debugging sencillo con Postman, Insomnia, DevTools  
- Aprovechamiento de caché HTTP  
- Arquitectura stateless facilita escalabilidad  
- Configuración CORS estándar  
- Documentación automática con Swagger/OpenAPI  

### Negativas o Riesgos

- Over-fetching y under-fetching en consultas  
- Necesidad de versionado de API en el futuro  
- Falta de tipado fuerte en JSON  
- Verbosidad en consultas complejas  
- Validación y sanitización manual por endpoint  
