# Mi lista de CEDEARs

> **Este archivo lo editás vos.** Una línea por empresa, con el ticker del activo original en USA
> (el que cotiza en Nueva York), no el símbolo local. Ese ticker es el que el agente usa para buscar los datos.
>
> Formato: `- TICKER — Nombre — ratio X:1`
> El **ratio** es cuántos CEDEARs equivalen a 1 acción original. Hace falta para calcular a qué dólar estás entrando.
> Si no lo sabés, escribí `ratio ?` y el agente lo busca y te lo completa en la primera corrida.

## Activas (el agente las revisa todos los días)

- AAPL — Apple — ratio 20:1
- MELI — Mercado Libre — ratio 120:1
- NVDA — Nvidia — ratio 24:1
- GOOGL — Google (Alphabet clase A) — ratio 58:1
- NU - Nu Holdings - ratio ?

<!-- Ratios verificados el 01/09/2026 contra dos fuentes independientes; ambas coinciden. -->

## En pausa (el agente NO las revisa)

- SNDK — SanDisk — ratio 170:1
  <!-- Pausada el 01/09/2026: el CEDEAR casi no se opera (última rueda con operaciones: 25/08/2026).
       Un CEDEAR sin volumen no se puede comprar ni vender a un precio razonable.
       Para reactivarla, movela de vuelta a "Activas". -->

<!-- Movés un ticker acá cuando no lo querés seguir, en vez de borrarlo. -->

---

## Cómo saber el ticker correcto

El CEDEAR local y la acción original comparten símbolo en la mayoría de los casos (AAPL, KO, MSFT, MELI). Donde suele confundir:

- Google → **GOOGL**
- Meta / Facebook → **META**
- Berkshire → **BRKB**
- Vista Energy → **VIST**
- Nvidia → **NVDA**

Si no estás seguro de alguno, ponelo igual y en la primera corrida el agente te va a avisar cuál no pudo encontrar.

> **Ojo con los ratios:** cambian de vez en cuando (las empresas hacen splits, o BYMA ajusta el ratio del CEDEAR).
> El agente verifica el ratio contra la fuente cada vez que corre y te avisa si no coincide con lo que dice este archivo.
