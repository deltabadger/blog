---
title: How Many Stocks Do You Actually Need?
subtitle: DCA into the top-N Nasdaq companies
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
---

What if you had DCA'd into just the biggest Nasdaq companies — how many would have been enough?

:::picker{n}

:::chart{indexes="nasdaq-100:dca:$n" symbols="QQQ:US:dca" title="Weekly DCA — Nasdaq Top $n vs QQQ" start="2016-01-01"}

Drag the slider. Fewer names means more concentration — watch what it does to the curve.
