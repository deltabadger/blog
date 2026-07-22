---
title: How Many Stocks Do You Actually Need?
subtitle: Investing in the top-N Nasdaq or S&P 500 companies
description: Interactive backtest — drag the slider and watch concentration beat diversification (or not).
thumbnail: research002
date: 2026-07-21
published: true
pickers:
  index:
    type: switch
    options:
      - id: nasdaq-100
        label: Nasdaq-100
        etf: QQQ
        short: Nasdaq
        from: "1999-04"
        default: true
      - id: sp-500
        label: S&P 500
        etf: SPY
        short: S&P
        from: "2012-01"
  n:
    type: slider
    min: 1
    max: 20
    step: 1
    default: 5
    prompt: Index size
  mode:
    type: switch
    options:
      - id: dca
        label: DCA
        default: true
      - id: rdca
        label: RDCA
      - id: price
        label: Lump sum
  w:
    type: switch
    options:
      - id: mcap
        label: Mcap
        default: true
      - id: equal
        label: Equal
  period:
    type: daterange
    min: "1999-10"
    max: now
    scope: index
  tview:
    type: switch
    options:
      - id: absolute
        label: Total return
        default: true
      - id: relative
        label: vs benchmark
---

What if you had invested in just the biggest companies in the Nasdaq-100 or S&P 500 — how many would have been enough?

:::picker{index}

:::picker{mode}

:::picker{w}

:::picker{n}

:::picker{period}

:::chart{indexes="$index:$mode:$n:$w" symbols="$index.etf:US:$mode" names="$index.short-$n,$index.etf" start="$period.start" end="$period.end" opt.compact="true"}

<!-- Reconstructed history: nasdaq-100 from 1999-09 (annual rebalances to 2002, quarterly after), sp-500 from 2011-12; the chart clamps to the shared range. -->

:::picker{tview}

:::chart{table="$index:$tview:$n:$w:$mode" symbols="$index.etf:US" start="$period.start" end="$period.end"}

## Every starting year at a glance

Each row is a year you could have started; each column, how long you kept going. Green cells made money — or beat the benchmark, in the second view; red cells didn't. A dash means the window doesn't finish inside the selected period. The table follows every control above — index, strategy, weighting, size, and period — using the same simulations as the chart.

**DCA** — a fixed amount buys the current index basket every week, split by the selected weighting. Nothing is ever sold: a company that falls out of the top N keeps its shares and just stops receiving new money.

**RDCA** — rebalanced DCA. The same weekly schedule, but each contribution is steered toward whichever companies sit furthest below their index weight, and when a company falls out of the top N its shares are sold and the proceeds move into its replacement.

**Custom index** — each quarter, the selected index's companies are ranked by market value and the biggest N form the custom index. The lump-sum view buys this index on day one and fully rebalances it every quarter: leavers are sold and the portfolio is reset to the new weights.

**Mcap / Equal** — how money is split inside the basket. Mcap weights by market value, so bigger companies get more; Equal gives every company in the top N the same share.

**QQQ / SPY** — the benchmark. An ETF that holds the full selected index — the version you could actually buy. It follows the same schedule as the mode you pick.

All prices are split-adjusted with dividends reinvested; fees and taxes are ignored.
