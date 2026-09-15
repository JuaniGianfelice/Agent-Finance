# Reglas de señal

> **Este archivo lo editás vos.** El agente lo lee literalmente cada mañana y no agrega criterios propios.
> Cambiar un número acá cambia el comportamiento del agente al día siguiente. No hace falta tocar nada más.

---

## Perfil y objetivos

- **Perfil:** moderado. En formación, con la guía de un asesor financiero.
- **Aporte:** un monto fijo por mes.
- **Dos bolsillos, dos plazos:**

| Bolsillo | Objetivo | Plazo | ¿Le sirve esta estrategia? |
|----------|----------|-------|----------------------------|
| 🚗 **Auto** | Comprar el primer auto | **Menos de 2 años** | **No del todo.** Ver la advertencia de abajo. |
| 🏦 **Largo** | Ahorro general / jubilación | Años | Sí, es exactamente para esto. |

> ### ⚠️ Advertencia sobre el bolsillo del auto
>
> Esta estrategia se banca las caídas porque asume que no tocás la plata en mucho tiempo. Con un plazo
> de menos de 2 años eso no se cumple: si el mercado está en baja justo cuando necesitás el auto,
> vendés perdiendo o postergás la compra.
>
> **Esto es una pregunta para tu asesor, no para este agente ni para Claude.** Preguntale qué parte del
> aporte mensual debería ir a cada objetivo y en qué instrumento conviene tener la plata del auto.
> Hasta que lo definas, el agente separa los dos bolsillos en el historial pero no cambia las señales:
> los umbrales de abajo aplican igual para los dos.

---

## Estrategia

**Acumulación de largo plazo.** La idea no es adivinar el piso: es comprar cuando el precio está lejos de sus máximos y cerca o por debajo de su promedio largo, y no comprar cuando está estirado. Se acepta de entrada que a veces vas a comprar y va a seguir bajando.

---

## 🟢 ZONA DE COMPRA

Entra si cumple **al menos una** de estas condiciones:

- El precio está **por debajo de la SMA 200** (distancia a SMA200 ≤ 0 %)
- La posición en el rango de 52 semanas es **≤ 25 %**
- La caída desde el máximo de 52 semanas es **≥ 20 %** **Y ADEMÁS** el precio no está más de **+15 %** por encima de la SMA 200

> **Por qué esa tercera condición tiene dos partes.** En la corrida de prueba del 01/09/2026, SanDisk
> apareció como compra por estar 33 % abajo de su máximo, cuando en realidad venía de subir 2.900 % en
> el año y seguía 59 % por encima de su promedio de 200 ruedas. La caída desde el máximo, sola, se
> dispara en cualquier acción que se fue muy arriba y corrigió un poco. El filtro de la SMA 200 evita eso.

## 🟡 OBSERVAR

Entra si no calificó arriba y cumple **al menos una**:

- La caída desde el máximo de 52 semanas está entre **10 % y 20 %**
- El precio está entre **0 % y +5 %** por encima de la SMA 200
- La posición en el rango de 52 semanas está entre **25 % y 45 %**

## ⚪ NEUTRO / CARA

Todo lo demás. En particular, cuando la caída desde el máximo es menor al 10 % o el precio está más de 10 % arriba de la SMA 50.

---

## Dólar CCL implícito — **informativo, no cambia las señales**

El agente calcula a qué tipo de cambio estás entrando y lo compara con el CCL de mercado del día:

```
CCL implícito = (precio del CEDEAR en ARS × ratio) ÷ precio de la acción en USD
Sobreprecio  = (CCL implícito − CCL de mercado) ÷ CCL de mercado × 100
```

Cómo se muestra en el informe:

| Sobreprecio | Cómo lo marca |
|-------------|---------------|
| ≤ 0,5 % | ✅ el dólar implícito está en línea con el mercado |
| 0,5 % a 2 % | ➖ diferencia normal |
| > 2 % | ⚠️ estás pagando el dólar por encima del mercado |

**Esto no degrada ni bloquea ninguna señal.** Es un número más en la mesa para que vos decidas. Si en algún momento querés que sí frene las compras, se cambia acá.

---

## Reglas de disciplina (las decide Juani, el agente solo las recuerda)

- **Presupuesto mensual:** _completar_ — cuánto destinás por mes, como máximo.
- **Reparto entre bolsillos:** _completar después de hablar con el asesor_ — qué % va al auto y qué % al largo plazo.
- **Máximo por empresa:** no más del **25 %** del total invertido en un solo ticker.
- **Compras por mes:** máximo **2** entradas, para no gastar todo el presupuesto en la primera señal del mes.
- **Regla del cajón:** si una señal aparece y a las 24 hs seguís queriendo comprar, comprás. Nada se compra el mismo minuto que aparece.

> Estas reglas no las ejecuta nadie automáticamente. Están escritas acá para que el agente te las recuerde cuando marca una señal.

---

## Cosas que este agente NO mira (a propósito, por ahora)

- RSI y otros indicadores de corto plazo.
- Noticias, balances y contexto de la empresa.
- Comisiones y costos de tu bróker.
- Cualquier instrumento que no sea un CEDEAR (plazos fijos, obligaciones negociables, fondos). Si el asesor te sugiere mover la plata del auto a otro lado, este agente no lo va a seguir.
