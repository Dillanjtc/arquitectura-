# ADR 008 - Uso de Vite como bundler y herramienta de desarrollo frontend

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autores**: A. Administrador

## Contexto y Problema a Resolver

El desarrollo del frontend en React requiere una herramienta que:

1. Transpile JSX a JavaScript compatible  
2. Gestione módulos y dependencias  
3. Proporcione servidor de desarrollo con hot-reload  
4. Optimice el código para producción  
5. Sea rápida y fácil de configurar  

**Alternativas consideradas**:

- Create React App (CRA)  
- Vite  
- Webpack manual  
- Parcel  

## Decisión Tomada

Se selecciona **Vite** como herramienta de build y servidor de desarrollo para el frontend de Curse Fast, por su velocidad, simplicidad y experiencia de desarrollo superior.

## Consecuencias

### Positivas

- Velocidad de desarrollo excepcional  
- Hot Module Replacement instantáneo  
- Configuración mínima  
- Build optimizado con Rollup  
- Documentación clara en español  
- Soporte nativo para TypeScript  
- Ecosistema de plugins amplio  
- Menor consumo de recursos en desarrollo  

### Negativas o Riesgos

- Compatibilidad limitada con navegadores antiguos  
- Comunidad más pequeña que CRA  
- Diferencias estructurales con CRA  
- Dependencia de ES modules (requiere configuración para librerías antiguas)  
