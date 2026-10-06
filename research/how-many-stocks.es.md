---
title: ¿Cuántas acciones necesitas realmente?
subtitle: Invertir en las N mayores empresas del Nasdaq o del S&P 500
description: Backtest interactivo — mueve el control deslizante y comprueba si la concentración supera a la diversificación (o no).
thumbnail: research002
date: 2026-07-21
published: false
pickers:
  index:
    type: switch
    prompt: Índice
    options:
      - id: nasdaq-100
        label: Nasdaq-100
        short: ND
        from: "1997-01"
        default: true
      - id: sp-500
        label: S&P 500
        short: S&P
        from: "1996-12"
  n:
    type: slider
    min: 1
    max: 30
    step: 1
    default: 4
    prompt: Tamaño del índice
  mode:
    type: switch
    prompt: Estrategia
    options:
      - id: rdca
        label: RDCA
        idx: rdca
        default: true
      - id: price
        label: Inversión única
        idx: lump
  threshold:
    type: slider
    min: 1
    max: 20
    step: 1
    default: 5
    prompt: Umbral de reequilibrio
    suffix: "%"
  tax:
    type: switch
    prompt: Impuestos
    options:
      - id: none
        label: Ninguno
        default: true
      - id: us
        label: US
  w:
    type: switch
    prompt: Asignación
    options:
      - id: mcap
        label: Mcap
      - id: equal
        label: Igual
        default: true
  benchmark:
    type: switch
    prompt: Índice de referencia
    options:
      - id: spy
        label: SPY
        short: SPY
        sym: SPY
        ex: US
        default: true
      - id: qqq
        label: QQQ
        short: QQQ
        sym: QQQ
        ex: US
        from: "1999-04"
  period:
    type: daterange
    min: "1996-12"
    max: now
    scope: [index, benchmark]
  tview:
    type: switch
    options:
      - id: absolute
        label: Rentabilidad total
        default: true
      - id: relative
        label: vs. referencia
  mw:
    type: switch
    prompt: Asignación
    options:
      - id: mcap
        label: Mcap
        default: true
      - id: equal
        label: Igual
      - id: both
        label: Ambos
  mmode:
    type: switch
    prompt: Estrategia
    options:
      - id: rdca
        label: RDCA
        default: true
      - id: lump
        label: Inversión única
      - id: both
        label: Ambos
  mhorizon:
    type: switch
    prompt: Plazo
    options:
      - { id: "1", label: 1 a, default: true }
      - { id: "3", label: 3 a }
      - { id: "5", label: 5 a }
      - { id: "10", label: 10 a }
      - { id: "15", label: 15 a }
      - { id: "20", label: 20 a }
  mbench:
    type: switch
    prompt: Índice de referencia
    options:
      - id: spy
        label: SPY
        short: SPY
        sym: SPY
        ex: US
      - id: qqq
        label: QQQ
        short: QQQ
        sym: QQQ
        ex: US
        from: "1999-04"
        default: true
---

Esta herramienta interactiva acompaña a la serie *The Myth of Index Investing*: [I](https://sovereignoptimist.com/p/the-myth-of-index-investing), [II](https://sovereignoptimist.com/p/the-myth-of-index-investing).

Explora una pregunta sencilla:

**Si construyes un índice pequeño con las mayores empresas del S&P 500 o del Nasdaq-100, ¿cuántas acciones debería tener para rendir mejor?**

<br>

:::picker{index}

:::picker{w}

:::picker{n}

:::picker{mode}

:::when{mode=price}

:::when{w=equal}

:::picker{threshold}

:::

:::

:::picker{tax}

:::picker{benchmark}

:::picker{period}

:::chart{indexes="$index:$mode.idx:$n:$w::instant:$tax:$threshold" symbols="$benchmark.sym:$benchmark.ex:$mode" names="$index.short-$n,$benchmark.short" start="$period.start" end="$period.end" opt.compact="true" opt.showYAxis="false" opt.showYLabels="false"}

<!-- Picker floor is 1996-12. Total-return reconstruction (the DCA math, include_dividends) only reaches 1995-12 for sp-500 mcap; nasdaq-100 (both weightings) and sp-500 equal floor at 1999-09-30, so their pre-2000 cells dash. Split-adjusted price-only data reaches 1996 across the board, but the returns here use total return. -->

:::picker{tview}

:::chart{table="$index:$tview:$n:$w:$mode.idx:instant:$tax:$threshold" symbols="$benchmark.sym:$benchmark.ex" start="$period.start" end="$period.end"}

<br>

## Metodología

**RDCA** — DCA con reequilibrio. Cada semana entra una cantidad fija, repartida entre las empresas que están por debajo de su peso objetivo, en proporción a su déficit. Dirige el dinero nuevo sin vender para reequilibrar, de modo que una empresa que supera su peso objetivo simplemente deja de recibir dinero hasta que las demás la alcanzan. Solo se venden las empresas que salen del índice, y lo obtenido se reinvierte.

**Inversión única** — todo el importe entra el primer día, repartido según el peso en el índice. Con asignación Mcap, la cartera se reequilibra por completo cuando cambian los componentes del índice. Con asignación Igual, se venden las empresas que salen y lo obtenido se reinvierte; se reequilibra de nuevo cuando una posición se desvía de su peso objetivo en más del umbral seleccionado (5 puntos porcentuales por defecto).

**Índice personalizado** — las N mayores empresas del índice seleccionado forman el índice personalizado, según clasificaciones históricas de capitalización bursátil que se actualizan, por lo general, cada trimestre. Parte del historial más antiguo usa instantáneas menos frecuentes. Entre actualizaciones, los pesos objetivo Mcap se mueven con los precios; los pesos objetivo Igual se mantienen iguales.

**Mcap / Igual** — cómo se reparte el dinero dentro de la cesta. Mcap pondera por valor de mercado, así que las empresas más grandes reciben más; Igual da a cada empresa del top N el mismo peso objetivo.

**Índice de referencia** — aquello con lo que se compara el índice personalizado, elegido con independencia del índice del que se construye. **QQQ** y **SPY** son los ETF que realmente podrías comprar para replicar el Nasdaq-100 y el S&P 500 completos. La referencia se compra igual que la estrategia que elijas: la misma cantidad cada semana en RDCA, o todo de una vez el primer día en una inversión única.

**Impuestos** — con la opción US, la simulación deduce los impuestos sobre las ganancias realizadas cuando se venden acciones para reequilibrar o sustituir a las que salen, además de los impuestos sobre los dividendos a lo largo del camino. Esto pone de relieve el coste fiscal de mantener tu propio índice: vendes acciones individuales, mientras que un ETF gestiona el reequilibrio internamente sin que tú vendas tus participaciones del ETF. El final de la simulación es una instantánea de una cartera que sigues manteniendo, no un motivo para venderlo todo de golpe. Por eso omitimos cualquier impuesto sobre una hipotética venta final en ambas carteras. El ETF de referencia paga el mismo impuesto sobre sus dividendos; nunca vende, así que no paga impuestos sobre ganancias.

Todos los precios están ajustados por splits y con los dividendos reinvertidos.

## Entonces, ¿cuántas acciones son suficientes?

Los gráficos de arriba muestran un tamaño de índice cada vez. Este los muestra todos uno junto a otro, de 1 a 30 empresas, para que veas qué tamaño funcionó mejor. Cada punto combina todos los años de inicio disponibles para el periodo de tenencia seleccionado: 1, 3, 5, 10, 15 o 20 años. Por defecto es 1 año, y el selector de Plazo actualiza ambos gráficos. Tiene sus propios controles más abajo: el rango de fechas, los impuestos y el umbral de arriba no se aplican aquí. Los resultados son antes de impuestos, las empresas que salen se venden el mismo día en que salen, y una inversión única con pesos iguales usa el umbral por defecto de 5 puntos porcentuales.

:::picker{mw}

:::picker{mmode}

:::picker{mhorizon}

:::picker{mbench}

:::chart{ncurve="$index:$mw:$mmode:$mhorizon" symbols="$mbench.sym:$mbench.ex" n="$n"}

**Gráfico superior: con qué frecuencia superó a la referencia.** El porcentaje de años de inicio que terminaron por delante tras el periodo de tenencia seleccionado.

**Gráfico inferior: por cuánto superó a la referencia, por año.** Cada punto es el resultado mediano de ese tamaño entre los años de inicio, durante el periodo de tenencia seleccionado. Los resultados están anualizados para facilitar la comparación entre periodos más cortos y más largos. Lee ambos gráficos juntos: el mejor tamaño es el que gana a menudo *y* con un margen apreciable.

<br>
