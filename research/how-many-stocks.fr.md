---
title: De combien d'actions avez-vous réellement besoin ?
subtitle: Investir dans les N premières entreprises du Nasdaq ou du S&P 500
description: Backtest interactif — déplacez le curseur et voyez la concentration battre la diversification (ou pas).
thumbnail: research002
date: 2026-10-06
published: true
pickers:
  index:
    type: switch
    prompt: Indice
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
    prompt: Taille de l'indice
  mode:
    type: switch
    prompt: Stratégie
    options:
      - id: rdca
        label: RDCA
        idx: rdca
        default: true
      - id: price
        label: Versement unique
        idx: lump
  threshold:
    type: slider
    min: 1
    max: 20
    step: 1
    default: 5
    prompt: Seuil de rééquilibrage
    suffix: "%"
  tax:
    type: switch
    prompt: Fiscalité
    options:
      - id: none
        label: Aucune
        default: true
      - id: us
        label: États-Unis
  w:
    type: switch
    prompt: Allocation
    options:
      - id: mcap
        label: Capi.
      - id: equal
        label: Égale
        default: true
  benchmark:
    type: switch
    prompt: Indice de référence
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
        label: Rendement total
        default: true
      - id: relative
        label: vs indice de référence
  mw:
    type: switch
    prompt: Allocation
    options:
      - id: mcap
        label: Capi.
        default: true
      - id: equal
        label: Égale
      - id: both
        label: Les deux
  mmode:
    type: switch
    prompt: Stratégie
    options:
      - id: rdca
        label: RDCA
        default: true
      - id: lump
        label: Versement unique
      - id: both
        label: Les deux
  mhorizon:
    type: switch
    prompt: Période
    options:
      - { id: "1", label: 1 an, default: true }
      - { id: "3", label: 3 ans }
      - { id: "5", label: 5 ans }
      - { id: "10", label: 10 ans }
      - { id: "15", label: 15 ans }
      - { id: "20", label: 20 ans }
  mbench:
    type: switch
    prompt: Indice de référence
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

Cet outil interactif accompagne la série *The Myth of Index Investing* : [I](https://sovereignoptimist.com/p/the-myth-of-index-investing), [II](https://sovereignoptimist.com/p/the-myth-of-index-investing).

Il explore une question simple :

**Si vous construisez un petit indice à partir des plus grandes entreprises du S&P 500 ou du Nasdaq-100, combien d'actions doit-il contenir pour offrir la meilleure performance ?**

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

## Méthodologie

**RDCA** — DCA rééquilibré. Un montant fixe est investi chaque semaine, réparti entre les entreprises situées sous leur pondération cible, proportionnellement à l'écart de chacune. Il oriente les nouveaux fonds sans vendre pour rééquilibrer : une entreprise qui dépasse sa pondération cible cesse simplement de recevoir de l'argent jusqu'à ce que les autres la rattrapent. Seules les entreprises qui sortent de l'indice sont vendues, et le produit est réinvesti.

**Versement unique** — la totalité du montant est investie dès le premier jour, répartie selon les pondérations de l'indice. Avec l'allocation Capi., le portefeuille est entièrement rééquilibré lorsque les composants de l'indice changent. Avec l'allocation Égale, les sorties sont vendues et le produit réinvesti ; un nouveau rééquilibrage a lieu lorsqu'une ligne s'écarte de sa pondération cible de plus que le seuil sélectionné (5 points de pourcentage par défaut).

**Indice personnalisé** — les N plus grandes entreprises de l'indice sélectionné forment l'indice personnalisé, d'après les classements historiques de capitalisation boursière, généralement mis à jour chaque trimestre. Une partie de l'historique plus ancien repose sur des instantanés moins fréquents. Entre deux mises à jour, les pondérations cibles Capi. évoluent avec les cours ; les pondérations cibles Égales restent égales.

**Capi. / Égale** — la façon dont l'argent est réparti au sein du panier. Capi. pondère par la valeur de marché, si bien que les plus grandes entreprises reçoivent davantage ; Égale donne à chaque entreprise du top N la même pondération cible.

**Indice de référence** — ce à quoi l'indice personnalisé est comparé, choisi indépendamment de l'indice dont il est issu. **QQQ** et **SPY** sont les ETF que vous pourriez réellement acheter pour le Nasdaq-100 et le S&P 500 complets. L'indice de référence est acheté de la même manière que la stratégie choisie : le même montant chaque semaine pour le RDCA, ou en une seule fois dès le premier jour pour un versement unique.

**Fiscalité** — lorsque l'option États-Unis est sélectionnée, la simulation déduit l'impôt sur les plus-values réalisées lors de la vente d'actions pour rééquilibrer ou remplacer les sorties, ainsi que l'impôt sur les dividendes perçus en cours de route. Cela met en évidence le coût fiscal de l'entretien de votre propre indice : vous vendez des actions individuelles, alors qu'un ETF gère le rééquilibrage en interne sans que vous ayez à vendre vos parts d'ETF. La fin de la simulation est un instantané d'un portefeuille que vous détenez toujours, pas une raison de tout vendre d'un coup. Nous excluons donc tout impôt sur une vente finale hypothétique pour les deux portefeuilles. L'ETF de référence paie le même impôt sur ses dividendes ; il ne vend jamais, il ne paie donc aucun impôt sur les plus-values.

Tous les cours sont ajustés des fractionnements, dividendes réinvestis.

## Alors, combien d'actions suffisent ?

Les graphiques ci-dessus montrent une seule taille d'indice à la fois. Celui-ci les montre toutes côte à côte, de 1 à 30 entreprises, pour que vous voyiez quelle taille a le mieux fonctionné. Chaque point combine toutes les années de départ disponibles pour la durée de détention sélectionnée — 1, 3, 5, 10, 15 ou 20 ans. La valeur par défaut est 1 an, et le sélecteur Période met à jour les deux graphiques. Il dispose de ses propres commandes ci-dessous : la plage de dates, la fiscalité et le seuil ci-dessus ne s'appliquent pas ici. Les résultats sont avant impôt, les sorties sont vendues le jour où elles quittent l'indice, et un versement unique à pondération égale utilise le seuil par défaut de 5 points de pourcentage.

:::picker{mw}

:::picker{mmode}

:::picker{mhorizon}

:::picker{mbench}

:::chart{ncurve="$index:$mw:$mmode:$mhorizon" symbols="$mbench.sym:$mbench.ex" n="$n"}

**Graphique du haut : à quelle fréquence il a battu l'indice de référence.** La part des années de départ qui se sont terminées en tête après la durée de détention sélectionnée.

**Graphique du bas : de combien il a battu l'indice de référence, par an.** Chaque point est le résultat médian pour cette taille sur l'ensemble des années de départ, pour la durée de détention sélectionnée. Les résultats sont annualisés afin de comparer plus facilement les durées plus courtes et plus longues. Lisez les deux graphiques ensemble : la meilleure taille est celle qui gagne souvent *et* avec une marge honorable.

<br>
