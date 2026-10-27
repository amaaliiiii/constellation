# Constellation · Flujos de pago multicart & multicheckout

Artifact **visual e interactivo** para alinear a Product, Payments, Fraude y Tech sobre el comportamiento del **checkout multi-orden** de Rappi: un método de pago, varias tiendas, un cobro independiente por orden. Ejemplo con **2 tiendas / 2 órdenes**, extensible a N.

## Ver el artifact

Abre [`index.html`](./index.html) en el navegador (o sirve la carpeta con `python3 -m http.server`).

## Estructura

1. **Condiciones que debe cumplir el flujo** — reglas base, distinguiendo *definidas* vs *propuestas pendientes de validar*.
2. **Simulador de escenarios** — toggle **Con BNPL / Sin BNPL**. Al elegir un escenario muestra, en paralelo por cada orden: estado, qué pasa a nivel de sistema, qué ve el usuario (mockup), qué acciones puede tomar, qué pasa después y qué comunicaciones recibe.
3. **Preguntas y decisiones pendientes** — puntos abiertos para Payments, Fraude y Tech.

## Escenarios

**Con BNPL** (no se cobra al crear; rechazo por fraude)
- A · Ambas órdenes se crean
- B · Usuario bloqueado por seguridad (ninguna orden)
- C · Falla la 2ª orden → continuar con la 1ª / cancelar todo

**Sin BNPL** (se intenta el pago al crear; fraude o fondos/cupo)
- D · Ambas órdenes y pagos OK
- E · Usuario bloqueado por seguridad (ninguna orden)
- F · Falla la 2ª (seguridad) → continuar / cancelar ambas (reversión)
- G · Falla el pago de la 1ª por fondos/cupo → cambiar tarjeta / volver
- H · Falla el pago de la 2ª por fondos/cupo → cambiar tarjeta (2ª) / continuar con la 1ª / cancelar ambas

Los textos de usuario son amigables (sin términos internos como *fraude*, *remedy* u *on hold*). Las propuestas sin cerrar llevan la etiqueta **Pendiente de validar**.
