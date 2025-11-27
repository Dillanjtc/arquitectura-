ADR-017 – Protocolo de Notificaciones (Alertas de Ofertas)

Fecha: 2025-11-25
Estado: Aprobado

Contexto

Los devs desean enterarse al instante cuando un curso pasa a ser gratuito o cuando un cupón está por expirar. El correo suele ser lento.

Decisión

Utilizar WebPush (VAPID) y Telegram Bot Webhooks como canales principales.

Detalles del protocolo
1. WebPush

El servidor generará notificaciones con payload estándar:

{
  "title": "Nuevo curso gratis disponible",
  "body": "Docker + Kubernetes – Solo por 24h",
  "url": "https://tusitio.com/curso/docker-kubernetes"
}
2. Telegram Webhook

Formato recomendado:

POST /webhooks/telegram
{
  "chat_id": "12345678",
  "text": "⚡ Curso GRATIS: React 18 desde cero – Cupón válido 48h"
}
Consecuencias

Permite alertas instantáneas.

Facilita integraciones con comunidades, canales y bots.