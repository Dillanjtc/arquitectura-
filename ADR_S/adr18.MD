ADR-018 – Protocolo Interno de Actualización de Estado

Fecha: 2025-11-25
Estado: Aprobado

Contexto

Servicios internos deben sincronizar estado de recursos, reputación y disponibilidad sin acoplamiento fuerte.

Decisión

Usar eventos de dominio distribuidos por mensajería (RabbitMQ / Kafka / NATS).

Evento estándar
{
  "event": "CuponExpirado",
  "resourceId": "uuid-12345",
  "occurredAt": "2025-11-25T18:00:00Z"
}
Consecuencias

Arquitectura desacoplada.

Procesos distribuidos pueden reaccionar sin dependencia directa.