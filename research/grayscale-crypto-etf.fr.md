---
title: Décrypter l'ETF multi-crypto de Grayscale
subtitle: Index Universe, CD20, CD5 — comment les indices CoinDesk façonnent discrètement le marché
description: "Le nouvel ETF de Grayscale suit l'indice CoinDesk 5 — pas simplement les 5 premières cryptos par capitalisation, mais un filtre institutionnel complexe. De l'Index Universe au CD5, cette méthodologie à quatre niveaux révèle où l'argent institutionnel affluera ensuite."
thumbnail: grayscale-crypto-etf
date: 2025-07-10
published: true
---

## L'ère des indices crypto commence

Le 1er juillet 2025, la SEC a [ouvert un nouveau chapitre pour l'investissement crypto](https://cointelegraph.com/news/sec-conversion-grayscale-large-cap-crypto-fund-etf) en approuvant la transformation du Grayscale Digital Large Cap Fund (GDLC) en un ETF (Exchange-Traded Fund) au comptant, qui sera coté sur le NYSE Arca avec 775 millions de dollars d'actifs sous gestion.

Pour Grayscale, il s'agit d'un tournant majeur par rapport à la structure de fonds fermé qui limitait auparavant l'accès des investisseurs. Désormais, les investisseurs institutionnels comme particuliers peuvent obtenir une exposition à la crypto via un véhicule familier et réglementé, sans avoir à gérer de portefeuilles ni de clés privées.

Malheureusement, comme pour les autres ETF américains, les investisseurs de l'UE n'y auront qu'un accès limité, exigeant généralement le statut d'investisseur professionnel ou le recours à un courtier hors zone UE.

Ce qui retient l'attention, ce n'est pas seulement la taille, mais la composition :

<!-- PAYWALL -->

## De l'Index Universe au CoinDesk 5

L'ETF offre une exposition diversifiée aux principales cryptomonnaies, avec **Bitcoin qui domine à environ 80 %** du portefeuille, complété par **Ethereum, XRP, Solana et Cardano**.

Alors que la plupart supposent que l'ETF suit simplement les 5 premières cryptomonnaies par capitalisation boursière, il suit en réalité l'**indice CoinDesk 5 (CD5)** — une méthodologie complexe conçue pour les investisseurs institutionnels, qui livre de subtils indices sur la prochaine direction que pourrait prendre l'argent institutionnel, ce qui mérite qu'on s'y attarde.

Le CD5 se situe au sommet d'une **méthodologie à quatre niveaux** développée par [CoinDesk Indices](https://indices.coindesk.com). Contrairement aux classements par capitalisation boursière populaires sur des sites comme CoinGecko ou CoinPaprika, le CD5 a été spécialement conçu pour les investisseurs institutionnels. Cela signifie que sa méthodologie complexe peut surprendre les passionnés de crypto — elle est bien plus sélective que le simple choix des plus grosses cryptos par capitalisation boursière.

<figure class="article__figure">
<img src="/research/coindesk-methodology.svg" alt="Les quatre niveaux de la méthodologie CoinDesk">
<figcaption class="article__figure__caption">Les quatre niveaux de la méthodologie CoinDesk</figcaption>
</figure>

### Index Universe

Tout commence par l'**Index Universe** — la méthodologie fondamentale de CoinDesk qui détermine quelles cryptomonnaies méritent même d'être envisagées pour un investissement institutionnel.

L'Index Universe part des **250 premières cryptomonnaies par capitalisation boursière**, puis applique une série de filtres de qualité stricts :

**Ce qui est éliminé d'emblée :**

❌ **Les stablecoins** (USDT, USDC) — ils sont censés rester stables, pas croître  
❌ **Les memecoins** (oui, même s'ils valent des milliards) — trop volatils et spéculatifs  
❌ **Les tokens wrapped ou stakés** — ce sont des dérivés, pas les actifs sous-jacents  
❌ **Les privacy coins** — les préoccupations réglementaires en font des exclusions institutionnelles  
❌ **Les titres financiers** — tout ce qui pourrait être classé comme un titre financier au regard du droit américain  

**Ce qui subsiste doit prouver sa liquidité :**

✅ Coté sur au moins 3 grandes plateformes d'échange avec des paires USD/USDC  
✅ Au moins une cotation doit avoir plus de 90 jours (pas de tokens flambant neufs)  
✅ Négociation active au cours des 30 derniers jours sur plusieurs plateformes  
✅ Disponible pour les clients américains sur au moins une plateforme  
✅ Volume de négociation quotidien médian suffisant (le point médian de l'activité de négociation quotidienne sur 90 jours)  

Ce processus de filtrage crée l'Index Universe — une liste sélectionnée de cryptomonnaies répondant aux standards d'investissement institutionnels. Bien que CoinDesk ne communique pas publiquement le nombre exact de cryptomonnaies qui franchissent ces filtres, il est probablement d'environ 50 actifs — nous savons seulement avec certitude qu'il est supérieur à 20 mais inférieur à 250.

Ce manque de transparence sur la taille réelle de l'Index Universe constitue l'une des limites actuelles, au même titre que la documentation encore embryonnaire du CD5. Une plus grande clarté sur ces chiffres aiderait les investisseurs à mieux comprendre la nature de l'indice.

:::playbook

Les indices CoinDesk offrent un moyen simple de suivre les flux d'argent institutionnels. Explorons les deux indices les plus importants : le CD20 et le CD5 (que suit le GDLC) :

### CoinDesk 20

L'[indice CoinDesk 20 (CD20)](https://indices.coindesk.com/coindesk20) reprend cet univers filtré et y ajoute une couche supplémentaire de gestion de portefeuille. C'est aussi la partie de l'offre la mieux documentée en ligne.

**Pondération par capitalisation boursière avec garde-fous** : la pondération par capitalisation de l'indice, que les utilisateurs de Deltabadger connaissent grâce au [bot DCA rééquilibré](https://deltabadger.com/academy/rebalanced-dca), est ajustée par l'ajout de plafonds (30 % maximum pour le plus grand, 20 % pour les autres). On ne comprend pas vraiment pourquoi ce plafond a été ajouté, et la documentation officielle de CoinDesk ne l'explique pas.

<figure class="article__figure" data-controller="pie-chart" data-pie-chart-data-value="#F7931A,BTC,Bitcoin,30.53
#7349A4,ETH,Ethereum,24.83
#2F2C56,XRP,XRP,18.25
#00FFA3,SOL,Solana,11.84
#0045D0,ADA,Cardano,3.05
#8DC351,BCH,Bitcoin Cash,1.50
#4DA6FF,SUI,Sui,1.33
#375BD2,LINK,Chainlink,1.29
#E84142,AVAX,Avalanche,1.10
#7D00FF,XLM,Stellar,1.08
COLUMN_BREAK
#BFBBBB,LTC,Litecoin,0.96
#40826D,HBAR,Hedera,0.93
#FF007A,UNI,Uniswap,0.65
#B6509E,AAVE,Aave,0.61
#000000,APT,Aptos,0.44
#29ABE2,ICP,Internet Computer,0.39
#00C08B,NEAR,Near,0.38
#E6007A,DOT,Polkadot,0.32
#8247E5,MATIC,Polygon,0.24
#0090FF,FIL,Filecoin,0.22">
<div class="pie-chart-wrapper">
<svg data-pie-chart-target="svg" width="300" height="300" class="pie-chart"></svg>
<div data-pie-chart-target="legend" class="pie-legend"></div>
</div>
<figcaption class="article__figure__caption">Répartition de l'indice CoinDesk 20 (CD20)</figcaption>
</figure>

**Rééquilibrage trimestriel** : tous les trois mois, l'ensemble du portefeuille est recalibré en fonction des conditions de marché actuelles, avec des « règles tampons » pour éviter une rotation excessive.

Ces règles sont conçues pour limiter la rotation excessive en accordant aux constituants actuels de l'indice une préférence pour y rester, même s'ils ont légèrement reculé dans le classement.

Le CD20 utilise un **système de tampon** :

**Critères d'entrée** :
1. Un actif doit figurer dans le top **40** par volume de négociation pour être pris en compte  
2. **Les 15 premières places** :  
- Reviennent aux plus grands actifs par capitalisation boursière (quel que soit leur statut actuel)  
3. **Les 5 places restantes** :  
- Les constituants actuels classés de la 16e à la 25e place par capitalisation boursière obtiennent la préférence  
- Si les constituants actuels ne sont pas assez nombreux à se qualifier, les nouveaux actifs les mieux classés comblent les places restantes  

**Critères de sortie** : un actif existant perd sa place s'il se produit l'un des cas suivants :  
1. Il tombe sous le rang **50** en volume de négociation (échec de liquidité), OU  
2. Il tombe sous le rang **25** en capitalisation boursière (échec de taille)  

Sans règles tampons, les actifs qui oscillent autour de la ligne de coupure seraient sans cesse ajoutés puis retirés chaque trimestre, générant des coûts de transaction inutiles et de l'instabilité.

### CoinDesk 5

Cependant, ce n'est pas le CD20 qui est utilisé pour le premier ETF multi-crypto, mais son petit frère :

Le **CD5** représente les 5 premiers actifs du CD20, sélectionnés par **capitalisation boursière** parmi les constituants déjà filtrés du CD20. Comme le CD20 applique déjà des filtres de liquidité stricts (y compris le criblage par volume de négociation), le CD5 hérite de ces standards de qualité tout en se concentrant sur les actifs les plus grands et les plus liquides.

L'indice est bien plus jeune et ne bénéficie pas encore de la même couverture en ligne, mais l'étude de sa construction montre clairement qu'il a été pensé pour un usage institutionnel.

La principale différence avec le CD20, c'est que **les plafonds sont supprimés**. Là où le CD20 limite le plus grand constituant à 30 % et les autres à 20 %, le CD5 utilise une pondération par pure capitalisation boursière. Résultat : Bitcoin atteint actuellement plus de 80 % de la répartition — un rappel à la réalité qui reflète la position dominante et le profil de liquidité de Bitcoin sur le marché. Cette concentration est une caractéristique voulue, pas un défaut — elle garantit que l'indice reflète la véritable hiérarchie des capitalisations boursières des actifs crypto les plus liquides.

Comme le CD20, le CD5 suit le même calendrier de rééquilibrage trimestriel, mais utilise une **règle tampon 4/6** plus simple : les 4 premiers actifs par capitalisation boursière du CD20 sont automatiquement inclus, tandis que les constituants existants classés 5e ou 6e obtiennent la préférence pour rester. Ce processus simplifié rend le CD5 particulièrement adapté à une mise en œuvre sous forme d'ETF, car il réduit la complexité tout en maintenant des standards institutionnels rigoureux.

<figure class="article__figure" data-controller="pie-chart" data-pie-chart-data-value="#F7931A,BTC,Bitcoin,79.35
#7349A4,ETH,Ethereum,10.63
#2F2C56,XRP,Ripple,5.78
#00FFA3,SOL,Solana,3.09
#0045D0,ADA,Cardano,1.14">
<div class="pie-chart-wrapper">
<svg data-pie-chart-target="svg" width="300" height="300" class="pie-chart"></svg>
<div data-pie-chart-target="legend" class="pie-legend"></div>
</div>
<figcaption class="article__figure__caption">Répartition de l'indice CoinDesk 5 (CD5)</figcaption>
</figure>

:::

### Récapitulatif de la structure de l'indice

Pour résumer la méthodologie :

**Index Universe** — établit les critères d'éligibilité de base, filtre environ 50 actifs (?).  
**CD20** — applique des principes de gestion de portefeuille, dont la pondération par capitalisation boursière avec plafonds, le criblage par volume de négociation et le rééquilibrage trimestriel avec règles tampons.  
**CD5** — sélectionne les 5 premiers actifs du CD20 par capitalisation boursière, supprime les plafonds et utilise des règles tampons simplifiées, optimisées pour l'investissement institutionnel.

## La prophétie autoréalisatrice

S'il est clair que les investisseurs institutionnels s'intéressent au marché crypto au sens large, seuls quelques actifs numériques répondent jusqu'à présent aux critères stricts de liquidité et de réglementation exigés pour être intégrés à un ETF.

En examinant de plus près la structure des indices, on obtient des indices sur la direction que prendront les grands capitaux dans un proche avenir. La méthodologie à quatre niveaux ne relève pas seulement de la gestion du risque — c'est une feuille de route pour l'allocation des capitaux institutionnels.

C'est important, car beaucoup reprochent aux indices de devenir des prophéties autoréalisatrices qui conduisent à une concentration accrue des capitaux. Lorsque des flux massifs d'ETF poursuivent le même ensemble limité d'actifs, les prix s'envolent indépendamment des fondamentaux.

Michael Burry a soutenu, dans une analyse restée célèbre, que l'investissement passif, comme les ETF sur le S&P 500, gonfle le prix des actions par des afflux massifs de capitaux sans analyse fondamentale — à l'image d'un système de Ponzi qui repose sur l'arrivée de nouveaux investisseurs. Il a averti que cela pourrait provoquer une crise de liquidité lorsque surviennent les sorties de capitaux, car la « porte de sortie » du marché est étroite.

En revanche, depuis sa dernière position short, l'indice a progressé. En ira-t-il de même pour le marché des cryptomonnaies ?

L'idée de trade est ici toute simple : **investir dans ce qui compose l'ETF**. Si les capitaux institutionnels affluent vers les constituants du CD5, leurs prix devraient profiter de cette demande structurelle — que vous croyiez ou non à la technologie sous-jacente.

### L'effet d'entraînement ?

Le président de l'ETF Store, [Nate Geraci, y voit des implications plus larges](https://twitter.com/NateGeraci/status/1939454629915619403), suggérant que cette approbation pourrait ouvrir la voie à des ETF au comptant individuels pour des actifs comme XRP, Solana et Litecoin. Cela permettrait aux investisseurs d'obtenir une exposition ciblée à des cryptomonnaies spécifiques via des comptes d'investissement traditionnels.

<blockquote class="twitter-tweet">
<p lang="en" dir="ltr">Final SEC deadline this week on Grayscale Digital Large Cap ETF (GDLC)…<br><br>Holds btc, eth, xrp, sol, &amp; ada.<br><br>Think *high likelihood* this is approved.<br><br>Would then be followed later by approval for individual spot ETFs on xrp, sol, ada, etc.</p>&mdash; Nate Geraci (@NateGeraci) <a href="https://twitter.com/NateGeraci/status/1939454629915619403?ref_src=twsrc%5Etfw">June 29, 2025</a>
</blockquote>

## Perspectives

Chaque jalon réglementaire signale la maturation continue du marché crypto. L'approbation par la SEC d'ETF crypto diversifiés ouvre l'ère des indices crypto.

Comme nous le savons des marchés traditionnels, les indices sous forme d'ETF et de fonds communs de placement constituent le principal moyen par lequel les gens investissent sur le marché. Jusqu'à présent, le marché des cryptomonnaies était dépourvu de cette approche pourtant la plus évidente.

Toutefois, le lancement de l'ETF GDLC crée un écart d'opportunité — alors que les investisseurs institutionnels accèdent à une indexation crypto professionnelle via des ETF réglementés, les investisseurs particuliers se heurtent à des barrières exigeant le statut d'investisseur professionnel et d'autres démarches supplémentaires. Pour la plupart des lecteurs, le GDLC restera probablement hors de portée.

### Notre mission

C'est précisément là, sur cet écart d'accessibilité, que Deltabadger intervient. Notre mission est de rendre les stratégies d'indexation accessibles à tous, avec des avantages clés :

Premièrement, les particuliers ne sont pas contraints par les exigences de liquidité comme le sont les ETF. Cela nous donne davantage de flexibilité dans la construction et la mise en œuvre des indices. Investir en indice sur des tendances émergentes comme les memecoins tout en conservant une approche professionnelle et passive est à notre portée.

Deuxièmement, nous construisons un moteur d'indexation puissant (lancement plus tard cette année) qui offrira aux utilisateurs un contrôle sans précédent. Avec l'accès à plus de 500 indices issus de CoinGecko et des pondérations personnalisables, vous pourrez construire des portefeuilles qui correspondent précisément à votre stratégie.

Cette approche automatisée élimine le besoin de gestion manuelle et de décisions arbitraires. Tout comme l'investissement en indice via des ETF et des fonds communs de placement est devenu la norme sur les marchés traditionnels, nous pensons que l'indexation automatisée deviendra la solution par défaut pour l'investissement crypto de long terme.

Le plus grand atout des indices, c'est qu'ils assurent une gestion naturelle du risque — les projets qui échouent sortent automatiquement, à l'image des entreprises en faillite qui quittent le S&P 500. Et contrairement au rééquilibrage trimestriel de CoinDesk, les indices personnalisés peuvent s'adapter plus rapidement à l'évolution des conditions de marché.

-

*Quel est votre avis sur ces évolutions ? Investiriez-vous dans le CD5, le CD20, ou vous en tiendriez-vous simplement à Bitcoin ? ETF ou portefeuille d'indices personnalisé en auto-conservation ?*

<!-- /PAYWALL -->
