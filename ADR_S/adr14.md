# ADR 014 - Levantamiento de caso: acceso a cursos de autoaprendizaje para jóvenes

**Fecha**: 2025-10-17  
**Estado**: Justificación de caso  
**Autores**: A. Administrador

## Contexto y Problema a Resolver

Curse Fast es una plataforma orientada a democratizar el acceso al conocimiento mediante la distribución de recursos educativos gratuitos. Uno de los casos funcionales y de negocio más relevantes es el de **jóvenes que desean autoeducarse en temas específicos**, ya sea por iniciativa propia o bajo la orientación de instituciones educativas superiores.

Este caso plantea la necesidad de:

1. Compartir información clara y accesible sobre cursos disponibles en distintas plataformas externas  
2. Permitir que estudiantes encuentren recursos relevantes según su perfil, idioma, nivel académico o área de interés  
3. Facilitar el descubrimiento de contenido sin requerir registro en múltiples plataformas  
4. Servir como puente entre instituciones educativas y estudiantes autoformativos  

## Objetivo del Caso

Diseñar y justificar una funcionalidad que permita a jóvenes —individuales o vinculados a instituciones— **acceder fácilmente a cursos de autoaprendizaje**, organizados por metadatos y filtrables por criterios relevantes.

Esta funcionalidad debe:

- Ser accesible desde el frontend SPA sin fricción  
- Mostrar recursos educativos con información suficiente para decidir si son útiles  
- Redirigir al usuario a la fuente original del curso sin almacenar contenido propio  
- Permitir que instituciones recomienden recursos a sus estudiantes  

## Usuarios Involucrados

- **Jóvenes autoeducativos**: estudiantes que buscan complementar su formación  
- **Instituciones educativas**: que desean orientar a sus estudiantes hacia recursos confiables  
- **Profesionales**: que buscan actualizar sus conocimientos de forma autónoma  

## Alternativas Consideradas

Aunque no se han formalizado alternativas técnicas aún, se contemplan enfoques como:

- Catálogo abierto con filtros por metadatos (idioma, categoría, plataforma)  
- Recomendaciones personalizadas por rol (institución, estudiante, profesional)  
- Integración futura con sistemas de recomendación o seguimiento de progreso  

## Justificación

Este caso funcional y de negocio **justifica la existencia del sistema Curse Fast** como un catálogo informativo. La decisión de **no almacenar contenido directamente**, sino actuar como agregador de metadatos (ver ADR 006), responde directamente a este caso.

Además, la arquitectura SPA + API REST (ver ADR 005 y ADR 013) permite implementar esta funcionalidad de forma eficiente, escalable y mantenible.

## Consecuencias

### Positivas

- Alineación directa con el objetivo del proyecto  
- Facilita el acceso a contenido educativo sin barreras técnicas ni legales  
- Permite escalar el catálogo sin costos adicionales de almacenamiento  
- Ofrece valor tanto a usuarios individuales como a instituciones  
- Justifica decisiones previas sobre arquitectura, almacenamiento y diseño de roles  

### Negativas

- Requiere curaduría inicial de recursos para garantizar calidad  
- Depende de la disponibilidad y estabilidad de enlaces externos  
- Necesita validación de instituciones para evitar spam o contenido irrelevante  
- Puede requerir funcionalidades adicionales como comentarios, favoritos o seguimiento en el futuro  

