---
title: How Many Stocks Do You Actually Need?
subtitle: Investing in the top-N Nasdaq companies
description: Interactive backtest — drag the slider and watch concentration beat diversification (or not).
date: 2026-07-21
published: false
pickers:
  n:
    type: slider
    min: 1
    max: 50
    step: 1
    default: 5
    prompt: Number of stocks in your index
  mode:
    type: switch
    prompt: Investment style
    options:
      - id: dca
        label: Weekly DCA
        default: true
      - id: price
        label: Lump sum
  period:
    type: daterange
    min: "2013-01"
    max: now
    prompt: Period
---

What if you had invested in just the biggest Nasdaq companies — how many would have been enough?

:::picker{n}

:::picker{mode}

:::picker{period}

:::chart{indexes="nasdaq-100:$mode:$n" symbols="QQQ:US:$mode" names="Nasdaq Top $n,QQQ" title="$mode.label — Nasdaq Top $n vs QQQ" start="$period.start" end="$period.end"}

<!-- Index history begins 2012-12-31 (first reconstructed rebalance snapshot). -->

Drag the slider. Fewer names means more concentration — watch what it does to the curve. Switch
between contributing every week and putting the whole amount in at the start of the period; both
views use total-return prices and ignore fees and taxes.
