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
    options:
      - id: rdca
        label: RDCA
        default: true
      - id: lump
        label: Lump sum
      - id: both
        label: Both
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

What if you had invested in just the biggest companies in the Nasdaq-100 or S&P 500 — how many would have been enough?

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

## Every starting year at a glance

Each row is a year you could have started; each column, how long you kept going. Green cells made money — or beat the benchmark, in the second view; red cells didn't. A dash means there's no complete window to show — either it hasn't finished yet, or the index or benchmark has no history that far back. The table follows every control above — index, strategy, threshold, taxes, weighting, size, benchmark and period — using the same simulations as the chart: rows start within the period, and only windows that end inside it are shown.

**RDCA** — rebalanced DCA. A fixed amount goes in every week, split among the companies that sit below their weight, in proportion to how far below each one is. It only steers new money: nothing is sold to rebalance, so a company that runs ahead of its weight keeps its lead and simply stops receiving money until the others catch up.

**Lump sum** — the whole amount goes in on day one, split by index weight. With **Mcap** allocation it then behaves like an index fund: its holdings rise and fall with the index, so between index changes there is nothing to correct and nothing is traded. Whenever the top N changes, the leavers are sold and every company is rebalanced to its index weight on that day. With **Equal** allocation the weights do drift, and the portfolio is rebalanced only when it drifts far enough: once any company sits more than the **rebalancing threshold** away from its weight (5 percentage points by default), the most overweight company is sold back to its weight and the proceeds buy the most underweight ones, until every company is back inside the band — the same way a Deltabadger index bot rebalances.

In RDCA and in an equal-weight lump sum, a company that falls out of the top N is sold on the day the index changes, even a small one that never drifted far. The money goes to whichever companies sit furthest below their weight — usually its replacement. In an equal-weight lump sum this always comes first, before the threshold is checked, so the newcomer is paid for by the company that left rather than by trimming the ones you keep: selling those would only realise gains you didn't need to. **Taxes** charges US federal tax on every sale as it happens — 24% on gains held a year or less, 15% on longer ones, with losses carried forward — and on the dividends received along the way, so less money is reinvested. Nothing is charged for selling at the end of the period: the result is what you hold, not what you would keep after cashing out. The benchmark is shown before tax.

**Custom index** — each quarter, the selected index's companies are ranked by market value and the biggest N form the custom index, weighted by the selected allocation.

**Mcap / Equal** — how money is split inside the basket. Mcap weights by market value, so bigger companies get more; Equal gives every company in the top N the same share.

**Benchmark** — what the custom index is measured against, chosen independently of the index it is built from. **QQQ** and **SPY** are the ETFs you could actually buy for the full Nasdaq-100 and S&P 500. The benchmark is bought the same way as the strategy you pick: the same amount every week for RDCA, or all at once on day one for a lump sum.

All prices are split-adjusted with dividends reinvested; fees are ignored, and so are taxes unless you turn them on.

## So how many is enough?

The charts above show one index size at a time. This one shows all of them side by side, from 1 to 30 companies, so you can see which size did best. Each point sums up every starting year and every holding period from the table above — 3, 5, 10, 15 and 20 years — over the index's whole history. It has its own controls below: the period, taxes and threshold above don't apply here. Results are before tax, dropouts are sold the day they leave, and an equal-weight lump sum uses the default 5% threshold. The gray line follows the index size you picked above; on the Nasdaq-100, the blue dashed line marks 4 companies, the sweet spot.

:::picker{mw}

:::picker{mmode}

:::picker{mbench}

:::chart{ncurve="$index:$mw:$mmode" symbols="$mbench.sym:$mbench.ex" n="$n"}

**Top chart: how often it beat the benchmark.** The share of periods that ended ahead.

**Bottom chart: how much it beat the benchmark by, per year.** Each point is the typical result for that size — half of the periods did better, half did worse. It's shown per year so that short and long periods can be compared fairly: beating SPY by 122% over 3 years is actually a bigger lead (+20.7% a year) than beating it by 638% over 20 years (+4.8% a year). Read the two together: the best size is one that wins often *and* by a decent margin.

With **RDCA** — where you sell anything that drops out, so you always hold exactly N companies — there's a sweet spot. Against QQQ, two companies is the weakest size: it wins only about half the time. Three to five do best, beating QQQ in roughly three periods out of four by about 1.5–2% a year, with four the most consistent. Add more and the lead shrinks, because the more companies you hold, the closer you get to simply owning the whole index.

With a **lump sum** the sweet spot sits in the same place: 3 to 5 companies, with two the worst size. It fades faster on the way out, though: from about ten companies it trails RDCA, and with **Equal** allocation it falls behind QQQ altogether. On the S&P 500 the edge is thin for both strategies: only 3 to 5 companies come out ahead of SPY, by about 1% a year at most.

Two things to keep in mind. The periods overlap a lot — a 20-year period out of 30 years of history is almost a single data point — so treat these numbers as what happened, not as odds for the future. And pick the right benchmark: against SPY, a Nasdaq-based portfolio mostly shows that the Nasdaq beat the S&P 500, not that fewer companies beat more. Against QQQ, what's left is how many companies you hold — and, with Equal allocation, how you weight them.
