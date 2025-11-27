# ADR 011 - Búsqueda por filtros múltiples sin motor de búsqueda especializado

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autor**: A. Administrador

## Contexto y Problema a Resolver

Los usuarios necesitan encontrar recursos específicos dentro del catálogo mediante:

1. Búsqueda por texto libre (título, descripción)  
2. Filtro por idioma (Español, Inglés, etc.)  
3. Filtro por categoría (Programación, Diseño, etc.)  
4. Combinación de múltiples filtros simultáneamente  

Se espera un catálogo inicial de cientos de recursos, con potencial de crecimiento a miles.

**Alternativas consideradas**:

- MySQL LIKE con índices  
- MySQL Full-Text Search  
- Elasticsearch  
- Algolia/Typesense  
- PostgreSQL con pg_trgm  

## Decisión Tomada

Se implementa la **búsqueda mediante queries SQL de MySQL usando LIKE con índices** en las columnas relevantes (título, descripción, idioma, categoría).

## Consecuencias

### Positivas

- Implementación simple y conocida por el equipo  
- Sin infraestructura adicional  
- Consistencia transaccional  
- Rendimiento suficiente para el MVP  
- Filtros combinables fácilmente con cláusulas AND  
- Costo cero en servicios externos  
- Mantenimiento simplificado  

### Negativas o Riesgos

- Rendimiento degradado con crecimiento del catálogo  
- Sin búsqueda fuzzy ni tolerancia a errores tipográficos  
- Sin ranking de relevancia sofisticado  
- Limitaciones en búsqueda multilingüe  
- Sin autocompletado inteligente  
- Carga adicional en la base de datos  
- Migración futura compleja si se adopta Elasticsearch  

**Estrategia de Mitigación**:  
Se implementarán índices en las columnas clave desde el inicio. Si el rendimiento se degrada, se evaluará MySQL Full-Text Search como paso intermedio antes de considerar Elasticsearch.
