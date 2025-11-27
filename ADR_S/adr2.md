# ADR 002 - Elección de MySQL como sistema de gestión de base de datos

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autores**: A. Administrador, D. Cliente

## Contexto y Problema a Resolver

El sistema Curse Fast necesita almacenar y gestionar:

1. Información de usuarios (proveniente de Google OAuth)  
2. Catálogo de recursos educativos (título, descripción, URL, idioma, categoría, plataforma)  
3. Metadatos adicionales (fechas de creación, roles de usuario)  
4. Relaciones entre entidades (usuarios que agregan recursos, favoritos, historial)  

Se estima un volumen inicial de cientos de recursos educativos y hasta 1,000 usuarios concurrentes. Los datos son predominantemente relacionales con necesidad de consultas con filtros múltiples (idioma, categoría, búsqueda por texto).

**Alternativas evaluadas**:

- MySQL: Base de datos relacional, equipo familiarizado, madurez comprobada  
- PostgreSQL: Más avanzada, pero menor experiencia del equipo  
- MongoDB: NoSQL, flexible, pero no óptima para datos relacionales  
- SQLite: Demasiado limitada para una aplicación web con múltiples usuarios  

## Decisión Tomada

Se selecciona **MySQL** como sistema de gestión de base de datos relacional, por su estabilidad, experiencia del equipo, y adecuación al modelo de datos.

## Consecuencias

### Positivas

- Familiaridad del equipo  
- Documentación extensa y comunidad activa  
- Modelo relacional adecuado  
- Buen rendimiento en búsquedas  
- Herramientas de administración (MySQL Workbench)  
- Costo nulo y hosting económico  
- Buena integración con Node.js (mysql2)  

### Negativas o Riesgos

- Funcionalidades avanzadas limitadas (JSONB, etc.)  
- Escalabilidad horizontal compleja  
- Búsqueda de texto completo básica  
- Posibles cuellos de botella en concurrencia de escritura  
