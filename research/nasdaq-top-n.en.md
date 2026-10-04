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
        from: "1996-12"
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
    default: 5
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
    prompt: Rebalancing threshold (%)
  sell:
    type: switch
    prompt: Sell dropouts
    options:
      - id: instant
        label: At once
        default: true
      - id: month
        label: Monthly
      - id: year
        label: Yearly
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
        default: true
      - id: equal
        label: Equal
  benchmark:
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
      - id: dca
        label: DCA
      - id: both
        label: Both
  mbench:
    type: dropdown
    prompt: Benchmark
    options:
      - id: spy
        label: SPY — S&P 500 ETF
        short: SPY
        sym: SPY
        ex: US
      - id: qqq
        label: QQQ — Nasdaq-100 ETF
        short: QQQ
        sym: QQQ
        ex: US
        default: true
      - id: ndx
        label: NDX — Nasdaq-100 index
        short: NDX
        sym: NDX
        ex: INDX
---

What if you had invested in just the biggest companies in the Nasdaq-100 or S&P 500 — how many would have been enough?

:::picker{index}

:::picker{w}

:::picker{n}

:::picker{mode}

:::picker{sell}

:::when{mode=price}

:::when{w=equal}

:::picker{threshold}

:::

:::

:::picker{tax}

:::picker{benchmark}

:::picker{period}

:::chart{indexes="$index:$mode.idx:$n:$w::$sell:$tax:$threshold" symbols="$benchmark.sym:$benchmark.ex:$mode" names="$index.short-$n,$benchmark.short" start="$period.start" end="$period.end" opt.compact="true"}

<!-- Picker floor is 1996-12. Total-return reconstruction (the DCA math, include_dividends) only reaches 1995-12 for sp-500 mcap; nasdaq-100 (both weightings) and sp-500 equal floor at 1999-09-30, so their pre-2000 cells dash. Split-adjusted price-only data reaches 1996 across the board, but the returns here use total return. -->

:::picker{tview}

:::chart{table="$index:$tview:$n:$w:$mode.idx:$sell:$tax:$threshold" symbols="$benchmark.sym:$benchmark.ex" start="$period.start" end="$period.end"}

## Every starting year at a glance

Each row is a year you could have started; each column, how long you kept going. Green cells made money — or beat the benchmark, in the second view; red cells didn't. A dash means there's no complete window to show — either it hasn't finished yet, or the index or benchmark has no history that far back. The table follows every control above — index, strategy, sell schedule, taxes, weighting, size, benchmark and period — using the same simulations as the chart: rows start within the period, and only windows that end inside it are shown.

**RDCA** — rebalanced DCA. A fixed amount goes in every week, steered toward whichever companies sit furthest below their index weight.

**Lump sum** — the whole amount goes in on day one, split by index weight. With **Mcap** allocation it then behaves like an index fund: its holdings rise and fall with the index, so between index changes there is nothing to correct and nothing is traded. Whenever the top N changes, the leavers are sold and every company is rebalanced to its index weight on that day — so the sell schedule below does not apply to it. With **Equal** allocation the weights do drift, and the portfolio is rebalanced only when it drifts far enough: once any company sits more than the **rebalancing threshold** away from its weight (5 percentage points by default), the most overweight company is sold back to its weight and the proceeds buy the most underweight ones, until every company is back inside the band — the same way a Deltabadger index bot rebalances.

In RDCA and in an equal-weight lump sum, a company that falls out of the top N is sold and the proceeds move into its replacement. That sale is separate from the threshold, so a small leaver is sold even though it never drifts far. **Sell dropouts** sets when it happens: at once on the day the index changes (the default), or held until the next month or year boundary counted from your start date. **Taxes** charges US federal tax on every sale as it happens — 24% on gains held a year or less, 15% on longer ones, with losses carried forward — and on the dividends received along the way, so less money is reinvested. Nothing is charged for selling at the end of the period: the result is what you hold, not what you would keep after cashing out. The benchmark is shown before tax.

**Custom index** — each quarter, the selected index's companies are ranked by market value and the biggest N form the custom index, weighted by the selected allocation.

**Mcap / Equal** — how money is split inside the basket. Mcap weights by market value, so bigger companies get more; Equal gives every company in the top N the same share.

**Benchmark** — what the custom index is measured against, chosen independently of the index it is built from. **QQQ** and **SPY** are the ETFs you could actually buy for the full Nasdaq-100 and S&P 500. The benchmark follows the same schedule as the mode you pick.

All prices are split-adjusted with dividends reinvested; fees are ignored, and so are taxes unless you turn them on. The one exception is NDX, the Nasdaq-100 index offered as a benchmark further down: it is a price index that excludes dividends, so against the total-return strategies it is a slightly conservative bar.

## So how many is enough?

Both views above answer for one index size at a time. This one puts the size itself on the x-axis: every N from 1 to 20, scored across every starting year and all five window lengths at once.

:::picker{mw}

:::picker{mmode}

:::picker{mbench}

:::chart{ncurve="$index:$mw:$mmode" symbols="$mbench.sym:$mbench.ex" n="$n"}

The top panel is the median **annualized** edge over the benchmark. Annualizing matters here: a +638 pp gap over twenty years and a +122 pp gap over three sound wildly different, but they are +4.8 %/yr and +20.7 %/yr — the short window is the bigger edge. Ranking sizes on raw percentage points would just rank the longest windows first.

The bottom panel is the share of windows that finished ahead. Read the two together: the best size is where a real edge shows up often enough to be worth holding through the bad years.

On **RDCA** — where you actually sell down to N names — the curve has a floor as well as a ceiling. One or two companies is not a strategy, it is a bet on a company: the edge is wild when it lands, and the share of winning windows sits on a coin flip. Past roughly a dozen names the edge decays toward zero, which it must: each name you add moves your portfolio closer to the index you are measuring against, so the gap has nowhere to go but down. The interesting region is the low-to-mid single digits.

Switch to **DCA** and the floor disappears — the edge just falls away as N grows, smallest sizes on top. That isn't a contradiction, it's what holding dropouts does. A top-1 DCA investor buys whichever company is largest each week and never sells, so after thirty years they own every company that was ever number one. The size in that mode is the size of this week's purchase, not the size of the portfolio, which quietly diversifies itself. Concentration is only concentration if you sell to maintain it.

Two cautions. The windows overlap heavily — a twenty-year figure drawn from thirty years of history is close to a single observation, so read the share of windows as a description of the past, not as odds on the future. And the benchmark matters: measured against SPY, a Nasdaq-derived index mostly shows Nasdaq beating the S&P, not concentration beating breadth. Against QQQ, concentration is the only thing still varying.
