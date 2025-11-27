# ADR 010 - Estrategia de despliegue con hosting económico separado

**Fecha**: 2025-10-14  
**Estado**: Aceptado  
**Autores**: A. Administrador, D. Cliente

## Contexto y Problema a Resolver

Con un presupuesto limitado, se requiere una estrategia de despliegue que:

1. Sea económicamente viable  
2. Soporte ~1,000 usuarios concurrentes  
3. Ofrezca alta disponibilidad (>85%)  
4. Permita escalabilidad futura  
5. No requiera conocimientos avanzados de DevOps  

Se necesita hosting para:

- Frontend (archivos estáticos)  
- Backend (servidor Node.js)  
- Base de datos MySQL  

**Alternativas evaluadas**:

- Todo en un VPS  
- Servicios serverless  
- Hosting compartido tradicional  
- Servicios especializados separados  

## Decisión Tomada

Se adopta una **estrategia de despliegue con servicios especializados económicos** separados para cada componente:

- Frontend: Vercel o Netlify  
- Backend: Railway, Render o Heroku  
- Base de datos: PlanetScale, Railway DB o FreeSQLDatabase  

## Consecuencias

### Positivas

- Costo mensual optimizado (<$20)  
- Configuración simplificada con CI/CD automático  
- Escalabilidad automática según demanda  
- Mantenimiento mínimo sin administración de servidores  
- SSL/HTTPS automático  
- CDN global incluido para frontend  
- Backups automáticos en base de datos  
- Monitoreo básico incluido  

### Negativas o Riesgos

- Vendor lock-in múltiple  
- Mayor complejidad de coordinación entre servicios  
- Límites de uso en tiers gratuitos  
- Latencia entre servicios en distintas regiones  
- Conocimiento fragmentado del equipo  
- Costos variables difíciles de predecir  
- Limitaciones de personalización en servicios gestionados  
