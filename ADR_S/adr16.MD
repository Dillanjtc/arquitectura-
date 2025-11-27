ADR-016 – Protocolo de Exposición de API pública

Fecha: 2025-11-25
Estado: Aprobado

Contexto

Los usuarios son developers. Necesitan una forma flexible de extraer datos, filtrar versiones, integrarse con bots o crear sus propios dashboards.

Decisión

Exponer el catálogo mediante GraphQL sobre HTTP.

Razones

Los devs pueden solicitar exactamente lo que necesitan (evita over‑fetching).

Permite búsquedas complejas con filtros por versión, deals, proveedor o tags.

Facilita que terceros desarrollen clientes, extensiones o bots.

Esquema mínimo propuesto
type Resource {
  id: ID!
  title: String!
  provider: String!
  techTags: [String!]!
  dealType: String!
  url: String!
  expiresAt: String
}


type Query {
  resources(filter: ResourceFilter): [Resource!]!
}
Consecuencias

La API será auto‑documentada.

Gran compatibilidad con herramientas modernas.