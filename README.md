# Constellation · Checkout multi-orden (TESLA)

Prototipo navegable **paso a paso** del flujo de **checkout multi-orden** de Constellation (Rappi) — Payments. Un pago, N entregas: el checkout crea N órdenes bajo un `group_order_id`, evalúa fraude una vez y cobra una transacción por tienda.

## Ver el prototipo

Abre [`index.html`](./index.html) en el navegador (o sirve la carpeta con `python3 -m http.server`).

## Qué incluye

Layout tipo **stepper** con pantallas anotadas (callouts numerados ↔ leyenda):

- **Celular al centro** — mockups estilo Rappi, navegables con `‹ / ›` y "Paso X de N".
- **Pins numerados** sobre cada pantalla señalando los elementos clave y qué hacen.
- **Panel derecho** por pantalla: descripción, leyenda, bloque "A dónde va" (transición de sistema) y preguntas abiertas.

## Flujos

| Flujo | Pantallas |
|---|---|
| Happy path · 2 entregas | Checkout → Creando → Confirmando → Confirmado |
| N tiendas · 3 entregas | Checkout (3) → Creando → Confirmando → Confirmado |
| Regla de método de pago | Método no válido para todas las tiendas |
| Sin fondos · rollback | Falla la 1ª → fallan todas |
| Remedy · falla 2ª orden | On-hold → nuevo método / cancelar → devolución |
| Con BNPL · éxito | Órdenes creadas, cobro al entregar |
| Rechazo por fraude | Fallan por fraude del usuario *(propuesta UI)* |
| Remedy en fraude | Challenge solo en la orden de mayor valor *(propuesta UI)* |
| Comunicaciones | 1 cobro = 1 notificación · devolución *(propuesta UI)* |

Las pantallas marcadas **PROPUESTA UI** son diseños abiertos a discusión (los "¿Cómo comunicamos?" aún no están definidos).
