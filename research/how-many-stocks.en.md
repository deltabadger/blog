---
title: How Many Stocks Do You Actually Need?
subtitle: Investing in the top-N Nasdaq or S&P 500 companies
description: Interactive backtest — drag the slider and watch concentration beat diversification (or not).
thumbnail: research002
date: 2026-07-21
published: false
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
    prompt: Index size
  mode:
    type: switch
    prompt: Strategy
    options:
      - id: rdca
        label: RDCA
        idx: rdca
        default: true
      - id: price
        label: Lump sum
        idx: lump
  threshold:
    type: slider
    min: 1
    max: 20
    step: 1
    default: 5
    prompt: Rebalancing threshold
    suffix: "%"
  tax:
    type: switch
    prompt: Taxes
    options:
      - id: none
        label: None
        default: true
      - id: us
        label: US
  w:
    type: switch
    prompt: Allocation
    options:
      - id: mcap
        label: Mcap
      - id: equal
        label: Equal
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
        label: Total return
        default: true
      - id: relative
        label: vs benchmark
  mw:
    type: switch
    prompt: Allocation
    options:
      - id: mcap
        label: Mcap
        default: true
      - id: equal
        label: Equal
      - id: both
        label: Both
  mmode:
    type: switch
    prompt: Strategy
    options:
      - id: rdca
        label: RDCA
        default: true
      - id: lump
        label: Lump sum
      - id: both
        label: Both
  mhorizon:
    type: switch
    prompt: Timeframe
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

This interactive tool accompanies *The Myth of Index Investing* series: [I](https://sovereignoptimist.com/p/the-myth-of-index-investing), [II](https://sovereignoptimist.com/p/the-myth-of-index-investing).

It explores a simple question:

**If you build a small index from the largest companies in the S&P 500 or the Nasdaq-100, how many stocks should it hold to perform best?**

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

## Methodology

**RDCA** — rebalanced DCA. A fixed amount goes in every week, split among the companies below their target weights, in proportion to each one's shortfall. It steers new money without selling to rebalance, so a company that exceeds its target weight simply stops receiving money until the others catch up. Only companies that drop out of the index are sold, and the proceeds are reinvested.

**Lump sum** — the whole amount goes in on day one, split by index weight. With Mcap allocation, the portfolio is fully rebalanced when the index's constituents change. With Equal allocation, dropouts are sold and the proceeds reinvested; further rebalancing occurs when a holding differs from its target weight by more than the selected threshold (5 percentage points by default).

**Custom index** — the largest N companies in the selected index form the custom index, based on historical market-cap rankings generally updated quarterly. Some older history uses less frequent snapshots. Between updates, Mcap target weights move with prices; Equal target weights remain equal.

**Mcap / Equal** — how money is split inside the basket. Mcap weights by market value, so bigger companies get more; Equal gives every company in the top N the same target weight.

**Benchmark** — what the custom index is measured against, chosen independently of the index it is built from. **QQQ** and **SPY** are the ETFs you could actually buy for the full Nasdaq-100 and S&P 500. The benchmark is bought the same way as the strategy you pick: the same amount every week for RDCA, or all at once on day one for a lump sum.

**Taxes** — when set to US, the simulation deducts taxes on gains realized when stocks are sold to rebalance or replace dropouts, plus taxes on dividends along the way. This highlights the tax cost of maintaining your own index: you sell individual stocks, while an ETF handles rebalancing internally without you selling your ETF shares. The end of the simulation is a snapshot of a portfolio you still hold, not a reason to sell everything at once. We therefore leave out any tax on a hypothetical final sale for both portfolios. The ETF benchmark pays the same tax on its dividends; it never sells, so it pays no tax on gains.

All prices are split-adjusted with dividends reinvested.

## So how many stocks are enough?

The charts above show one index size at a time. This one shows all of them side by side, from 1 to 30 companies, so you can see which size did best. Each point combines every available starting year for the selected holding period — 1, 3, 5, 10, 15 or 20 years. The default is 1 year, and the Timeframe switch updates both charts. It has its own controls below: the date range, taxes and threshold above don't apply here. Results are before tax, dropouts are sold the day they leave, and an equal-weight lump sum uses the default threshold of 5 percentage points.

:::picker{mw}

:::picker{mmode}

:::picker{mhorizon}

:::picker{mbench}

:::chart{ncurve="$index:$mw:$mmode:$mhorizon" symbols="$mbench.sym:$mbench.ex" n="$n"}

**Top chart: how often it beat the benchmark.** The share of starting years that ended ahead after the selected holding period.

**Bottom chart: how much it beat the benchmark by, per year.** Each point is the median result for that size across starting years, over the selected holding period. The results are annualized so that shorter and longer holding periods are easier to compare. Read the two charts together: the best size is one that wins often *and* by a decent margin.

<br>
