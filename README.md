# Agent Finance

Un agente que cada mañana mira las empresas de tu lista, calcula qué tan lejos están de sus máximos y de sus promedios, calcula a qué dólar estarías entrando, y te dice cuáles cruzaron los umbrales que vos definiste. Vos ejecutás la compra en tu bróker.

**Lo que no es:** un asesor. No predice precios, no te dice qué comprar y no opina sobre cómo repartir tu plata. Te ahorra el laburo de mirar veinte pantallas, con reglas que están escritas en un archivo que podés leer y cambiar.

---

## ⚠️ Lo primero, antes de usar nada de esto

Tenés dos objetivos con plazos muy distintos: **el auto (menos de 2 años)** y **el largo plazo (jubilación)**. Esta estrategia está diseñada para el segundo. Para el primero puede jugarte en contra: se banca las caídas porque asume que no tocás la plata en años, y vos esa plata la vas a necesitar pronto.

**Preguntale a tu asesor:** *"tengo un objetivo a menos de 2 años y otro a largo plazo, ¿qué parte del aporte mensual debería ir a cada uno y en qué instrumento conviene tener la plata del auto?"*

Mientras tanto el agente separa los dos bolsillos en el historial, para que sepas cuánta plata tenés comprometida en cada uno.

---

## Los archivos

```
Agent-Finance/
├── README.md            ← esto
├── prompt-agente.md     ← las instrucciones que corre el agente cada mañana
├── config/
│   ├── cedears.md       ← TU LISTA          ← lo editás vos
│   └── reglas.md        ← LOS UMBRALES      ← lo editás vos
├── historial/
│   └── compras.md       ← qué compraste     ← lo cargás vos
└── informes/
    └── AAAA-MM-DD.md    ← la salida diaria  ← lo escribe el agente
```

Solo tres archivos son tuyos: **cedears.md**, **reglas.md** y **compras.md**. Todo lo demás se maneja solo.

---

## Cómo funciona un día normal

1. **10:00** — la tarea programada arranca sola, de lunes a viernes.
2. El agente lee tu lista y tus reglas, busca los datos en la web y hace las cuentas.
3. Te llega el informe al chat y queda guardado en `informes/`.
4. Vos mirás **Zona de compra**. Si hay algo, decidís de qué bolsillo sale y esperás 24 horas. Si no hay nada, cerrás y seguís con tu día.
5. Si comprás, anotás la operación en `historial/compras.md`.

El paso 5 es el único que da trabajo y es el que hace que dentro de un año esto valga algo.

---

## Los cuatro números que vas a ver (y qué significan)

No hace falta que aprendas nada más que esto.

**Caída desde el máximo.** Cuánto bajó respecto de lo más alto que valió en los últimos 12 meses. Si dice −25 %, está un cuarto más barata que en su mejor momento del año.

**Distancia a la SMA 200.** La SMA 200 es el precio promedio de las últimas 200 ruedas: la línea "normal" de esa acción en el último año. Si el precio está por debajo, está más barata que su propio promedio reciente. Es el criterio central de la estrategia.

**Posición en el rango de 52 semanas.** De 0 a 100. 0 es el precio más bajo del año, 100 el más alto. Si dice 15, está cerca del piso del año.

**Dólar implícito.** Cuando comprás un CEDEAR pagás pesos y recibís un pedacito de una acción que vale dólares. Dividiendo una cosa por la otra sale el tipo de cambio al que entraste. El agente lo compara con el CCL de mercado del día: si estás pagando bastante más, la acción puede estar barata y la operación salirte mal igual. **No frena ninguna señal**, es un dato más para que decidas.

Los tres primeros no dicen si la empresa está bien o mal. Dicen si el precio de hoy está caro o barato **respecto de sí mismo**. Una acción puede estar barata porque el negocio se rompió — por eso la decisión sigue siendo tuya.

---

## Cómo cambiar algo

- **Agregar o sacar una empresa** → editás `config/cedears.md`. Efecto en la corrida siguiente.
- **Que avise más o menos seguido** → editás los porcentajes de `config/reglas.md`. Umbrales más exigentes (ej. caída ≥ 30 %) = menos señales, más contundentes.
- **Que el dólar caro sí frene las compras** → está explicado en `reglas.md`, se cambia una línea.
- **Cambiar horario, formato o agregar un criterio nuevo** → abrí un chat conmigo y pedímelo. El prompt vive en `prompt-agente.md`.

---

## Límites que conviene tener presentes

- Los datos salen de páginas públicas de finanzas. Pueden tener retraso o algún error puntual; el agente te avisa cuándo es el dato y qué no pudo conseguir.
- Los ratios de los CEDEARs cambian de vez en cuando. El agente los verifica en cada corrida, pero si un ratio está mal el cálculo del dólar da cualquier cosa.
- No mira balances, noticias ni contexto de la empresa. Una caída del 30 % puede tener un motivo de fondo que estos números no ven.
- No conoce las comisiones de tu bróker.
- No sabe nada de instrumentos que no sean CEDEARs. Si tu asesor te sugiere mover la plata del auto a un plazo fijo o algo similar, este agente no te va a acompañar en eso.

Esto es información de mercado, no una recomendación de inversión.
