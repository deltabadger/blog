---
title: "Rebalanced DCA"
description: "Combine DCA with portfolio rebalancing to automatically maintain your target allocations while avoiding tax events. Works with any basket, from BTC-ETH to a full portfolio."
published: true
---

Many people know about *rebalancing* and [*DCA*](/academy/dca-bot), but how about doing both at the same time?

Meet **Rebalanced DCA** — our *special sauce*.

The bot achieves rebalancing using only BUY orders; you never sell, so there are **no tax events** while still targeting your desired allocation.

With rebalanced DCA, you diversify in a systematic way. You pick two or more assets and a target allocation; the bot buys a bit more of whatever is currently below its target, and at the same time, it keeps your risk under control.

### Examples:

**BTC-ETH** — "Digital gold" meets Web3. Cover 74% of the crypto market with a simple, no-hassle portfolio that rebalances on autopilot.

**ETH-SOL** — Which Web3 platform will win? Invest in both and let the market decide. Rebalancing ensures you end up on the winning side.

**BTC-PAXG** — Cross-asset diversification. Pax Gold is a unique stablecoin that is not correlated with crypto but still offers attractive upside.

Pairs are the classic use, but nothing stops at two: a portfolio bot rebalances a whole basket the same way, buying whatever is furthest below its target.

## Market Cap Weighting

Most of the options are the same as for the basic [DCA bot](/academy/dca-bot), but with rebalancing comes one that is new: **Market Cap adjusted** allocation.

Instead of setting the allocations manually, you can weight them based on market caps.

This allows you to stay neutral and **let the market pick the winner**.

Some people think Solana may one day replace Ethereum; by setting a bot that DCAs in both with market cap weighting, you don't have to predict the future. The bot will adjust allocation as the market changes.

## Market Cap Explained

**Market cap** is a way to measure how big or valuable an asset is. It's calculated by multiplying the total number of coins by the current price of one coin. In your bot, the coin with the bigger market cap gets a larger share of your investment.

Example:

Coin A: 2 million coins exist, each worth $10.

`Market Cap = 2M × $10 = $20M`

Coin B: 1 million coins exist, each worth $1.

`Market Cap = 1M × $1 = $1M`

If you invest $100, the bot will split it proportionally to their market caps: $95.2 to Coin A, $4.8 to Coin B.

But if Coin B's price rises to $3, its market cap becomes $3M. Now, the next $100 will allocate $87 to Coin A and $13 to Coin B.

### Pay attention!

However, **not all market caps are created equal**. Many crypto projects hold a large portion of their coins in reserve, creating artificial scarcity. When prices rise, project founders can dump these reserved coins on the market, diluting value for other holders. This is why you need to look at "circulating supply" rather than just total supply when evaluating market caps.

For established cryptocurrencies like Bitcoin and Ethereum, market cap remains one of the most reliable metrics for gauging their significance in the market. Bitcoin's supply is truly decentralized with no large holders who could manipulate the market, while Ethereum's transition to proof-of-stake has made its tokenomics even more transparent.
