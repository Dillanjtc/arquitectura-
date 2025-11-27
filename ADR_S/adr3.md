# ADR 003 - Elección de React como biblioteca de frontend

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autores**: A. Administrador, D. Cliente

## Contexto y Problema a Resolver

El sistema Curse Fast requiere una interfaz de usuario que permita:

1. Búsqueda interactiva de recursos educativos sin recargar la página  
2. Filtrado dinámico por múltiples criterios (idioma, categoría, nivel académico)  
3. Experiencia de usuario fluida y responsiva  
4. Actualización del catálogo sin interrumpir la navegación del usuario  
5. Interfaz moderna y atractiva para estudiantes  

**Requisito del Cliente**: El cliente solicitó explícitamente el uso de React como tecnología frontend, basándose en su popularidad y demanda en el mercado laboral actual.

**Alternativas consideradas**:

- React: Biblioteca de componentes, muy popular, ecosistema extenso  
- Vue.js: Framework progresivo, curva de aprendizaje suave  
- Angular: Framework completo, más complejo y estructurado  
- HTML/CSS/JS puro: Más simple pero sin estructura ni reutilización de componentes  

## Decisión Tomada

Se selecciona **React** como biblioteca principal para el desarrollo del frontend de Curse Fast, en cumplimiento del requisito del cliente y por su capacidad para crear interfaces modernas e interactivas.

## Consecuencias

### Positivas

- Cumplimiento de requisito del cliente  
- Componentización y reutilización (SearchBar, ResourceCard, FilterPanel)  
- Ecosistema rico (React Router, librerías de UI)  
- Virtual DOM para actualizaciones eficientes  
- Habilidades marketables para el equipo junior  
- Misma base de conocimiento (JavaScript en frontend y backend)  
- Herramientas de desarrollo como React DevTools  

### Negativas o Riesgos

- Curva de aprendizaje para equipo junior (hooks, ciclo de vida, estado)  
- Gestión de estado compleja a medida que crece la app  
- Tamaño del bundle afecta tiempos de carga  
- SEO limitado por renderizado en cliente (SPA)  
- Posible sobre-ingeniería para un catálogo simple  
