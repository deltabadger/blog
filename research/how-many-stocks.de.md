---
title: Wie viele Aktien brauchen Sie wirklich?
subtitle: Investieren in die N größten Unternehmen des Nasdaq oder S&P 500
description: Interaktiver Backtest – ziehen Sie den Regler und sehen Sie, ob Konzentration die Diversifikation schlägt (oder nicht).
thumbnail: research002
date: 2026-10-06
published: true
pickers:
  index:
    type: switch
    prompt: Index
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
    prompt: Indexgröße
  mode:
    type: switch
    prompt: Strategie
    options:
      - id: rdca
        label: RDCA
        idx: rdca
        default: true
      - id: price
        label: Einmalanlage
        idx: lump
  threshold:
    type: slider
    min: 1
    max: 20
    step: 1
    default: 5
    prompt: Rebalancing-Schwelle
    suffix: "%"
  tax:
    type: switch
    prompt: Steuern
    options:
      - id: none
        label: Keine
        default: true
      - id: us
        label: USA
  w:
    type: switch
    prompt: Gewichtung
    options:
      - id: mcap
        label: Marktkap.
      - id: equal
        label: Gleich
        default: true
  benchmark:
    type: switch
    prompt: Benchmark
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
        label: Gesamtrendite
        default: true
      - id: relative
        label: vs. Benchmark
  mw:
    type: switch
    prompt: Gewichtung
    options:
      - id: mcap
        label: Marktkap.
        default: true
      - id: equal
        label: Gleich
      - id: both
        label: Beide
  mmode:
    type: switch
    prompt: Strategie
    options:
      - id: rdca
        label: RDCA
        default: true
      - id: lump
        label: Einmalanlage
      - id: both
        label: Beide
  mhorizon:
    type: switch
    prompt: Zeitraum
    options:
      - { id: "1", label: 1y, default: true }
      - { id: "3", label: 3y }
      - { id: "5", label: 5y }
      - { id: "10", label: 10y }
      - { id: "15", label: 15y }
      - { id: "20", label: 20y }
  mbench:
    type: switch
    prompt: Benchmark
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

Dieses interaktive Tool begleitet die Serie *The Myth of Index Investing*: [I](https://sovereignoptimist.com/p/the-myth-of-index-investing), [II](https://sovereignoptimist.com/p/the-myth-of-index-investing-part).

Es geht einer einfachen Frage nach:

**Wenn Sie aus den größten Unternehmen des S&P 500 oder des Nasdaq-100 einen kleinen Index bauen: Wie viele Aktien sollte er enthalten, um die beste Wertentwicklung zu erzielen?**

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

## Methodik

**RDCA** – Rebalanced DCA. Jede Woche fließt ein fester Betrag ein und wird auf die Unternehmen unterhalb ihrer Zielgewichtung verteilt, im Verhältnis zu ihrem jeweiligen Fehlbetrag. Das neue Geld steuert die Gewichtung, ohne dass zum Rebalancing verkauft wird: Überschreitet ein Unternehmen sein Zielgewicht, erhält es einfach kein Geld mehr, bis die anderen aufgeholt haben. Verkauft werden nur Unternehmen, die aus dem Index ausscheiden; der Erlös wird reinvestiert.

**Einmalanlage** – der gesamte Betrag wird am ersten Tag investiert, aufgeteilt nach Indexgewicht. Bei Gewichtung nach Marktkapitalisierung wird das Portfolio vollständig neu gewichtet, wenn sich die Indexmitglieder ändern. Bei gleicher Gewichtung werden ausgeschiedene Titel verkauft und der Erlös reinvestiert; weiteres Rebalancing erfolgt, wenn eine Position um mehr als die gewählte Schwelle von ihrem Zielgewicht abweicht (standardmäßig 5 Prozentpunkte).

**Eigener Index** – die N größten Unternehmen des gewählten Index bilden den eigenen Index, basierend auf historischen Marktkapitalisierungs-Rankings, die in der Regel vierteljährlich aktualisiert werden. Ältere Daten stammen teils aus selteneren Momentaufnahmen. Zwischen den Aktualisierungen bewegen sich die Zielgewichte bei Marktkapitalisierungs-Gewichtung mit den Kursen; bei gleicher Gewichtung bleiben sie gleich.

**Marktkap. / Gleich** – wie das Geld innerhalb des Korbs aufgeteilt wird. „Marktkap.“ gewichtet nach Marktwert, sodass größere Unternehmen mehr erhalten; „Gleich“ gibt jedem Unternehmen unter den Top N dasselbe Zielgewicht.

**Benchmark** – der Maßstab, an dem der eigene Index gemessen wird, unabhängig vom Index, aus dem er gebaut ist. **QQQ** und **SPY** sind die ETFs, die Sie tatsächlich für den gesamten Nasdaq-100 bzw. S&P 500 kaufen könnten. Der Benchmark wird genauso gekauft wie die gewählte Strategie: jede Woche derselbe Betrag bei RDCA oder alles auf einmal am ersten Tag bei einer Einmalanlage.

**Steuern** – bei der Einstellung „USA“ zieht die Simulation Steuern auf Gewinne ab, die beim Verkauf von Aktien zum Rebalancing oder zum Ersatz ausgeschiedener Titel realisiert werden, sowie laufend Steuern auf Dividenden. Das zeigt die Steuerkosten, die beim Pflegen eines eigenen Index entstehen: Sie verkaufen einzelne Aktien, während ein ETF das Rebalancing intern erledigt, ohne dass Sie Ihre ETF-Anteile verkaufen. Das Ende der Simulation ist eine Momentaufnahme eines Portfolios, das Sie weiterhin halten, kein Anlass, alles auf einmal zu verkaufen. Wir lassen deshalb für beide Portfolios jede Steuer auf einen hypothetischen Schlussverkauf weg. Der ETF-Benchmark zahlt dieselbe Steuer auf seine Dividenden; er verkauft nie und zahlt daher keine Steuer auf Gewinne.

Alle Kurse sind um Aktiensplits bereinigt, Dividenden werden reinvestiert.

## Wie viele Aktien genügen also?

Die Diagramme oben zeigen jeweils eine Indexgröße. Dieses zeigt alle nebeneinander, von 1 bis 30 Unternehmen, sodass Sie sehen, welche Größe am besten abgeschnitten hat. Jeder Punkt fasst alle verfügbaren Startjahre für die gewählte Haltedauer zusammen – 1, 3, 5, 10, 15 oder 20 Jahre. Standard ist 1 Jahr, und der Zeitraum-Schalter aktualisiert beide Diagramme. Es hat unten eigene Regler: Zeitraum, Steuern und Schwelle von oben gelten hier nicht. Die Ergebnisse verstehen sich vor Steuern, ausgeschiedene Titel werden am Tag ihres Ausscheidens verkauft, und eine gleichgewichtete Einmalanlage verwendet die Standardschwelle von 5 Prozentpunkten.

:::picker{mw}

:::picker{mmode}

:::picker{mhorizon}

:::picker{mbench}

:::chart{ncurve="$index:$mw:$mmode:$mhorizon" symbols="$mbench.sym:$mbench.ex" n="$n"}

**Oberes Diagramm: wie oft es den Benchmark geschlagen hat.** Der Anteil der Startjahre, die nach der gewählten Haltedauer vorne lagen.

**Unteres Diagramm: wie deutlich es den Benchmark geschlagen hat, pro Jahr.** Jeder Punkt ist das Medianergebnis dieser Größe über alle Startjahre, bezogen auf die gewählte Haltedauer. Die Ergebnisse sind annualisiert, damit sich kürzere und längere Haltedauern leichter vergleichen lassen. Lesen Sie beide Diagramme zusammen: Die beste Größe ist eine, die oft gewinnt *und* mit ordentlichem Abstand.

<br>
