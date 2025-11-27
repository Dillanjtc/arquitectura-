ADR-015 – Protocolo de Ingesta y Verificación de Links

Fecha: 2025-11-25
Estado: Aprobado

Contexto

La mayoría de ofertas gratuitas provienen de plataformas como Udemy, Hotmart, Domestika, YouTube o GitHub. Muchas poseen sistemas anti‑bot (Cloudflare, CAPTCHA) y expiran en cuestión de horas. Las verificaciones con simples peticiones HTTP (GET) suelen fallar o devolver información incompleta.

Decisión

Implementar un Headless Browser Protocol basado en Puppeteer o Playwright, coordinado mediante colas de validación, para simular un usuario real.

Detalles del protocolo

El verificador debe usar:

User-Agent real

Esperas dinámicas (waitForNavigation)

Manejo de challenge pages (Cloudflare)

Ejecución sandbox aislada

Cada verificación debe devolver un objeto estándar:

{
  "url": "https://udemy.com/...",
  "status": "Valid",
  "price": 0,
  "currency": "USD",
  "isFree": true,
  "detectedAt": "2025-11-25T15:30:11Z"
}

Si el recurso no es gratuito, disparar evento de dominio:

CuponExpirado

EnlaceRotoDetectado

Consecuencias

Permite validar miles de enlaces sin falsos positivos.

Evita bloqueos por mecanismos anti-bot.

Incrementa el costo computacional, pero asegura precisión.