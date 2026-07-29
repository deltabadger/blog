---
title: Descifrando el ETF multicripto de Grayscale
subtitle: "Index Universe, CD20, CD5: los índices de CoinDesk moldean el mercado en silencio"
description: "El nuevo ETF de Grayscale replica el índice CoinDesk 5, que no es simplemente el top 5 de criptos por capitalización de mercado, sino un complejo filtro institucional. Del Index Universe al CD5, esta metodología de cuatro niveles revela hacia dónde fluirá a continuación el dinero institucional."
thumbnail: grayscale-crypto-etf
date: 2025-07-10
published: true
---

## Comienza la era de los índices cripto

El 1 de julio de 2025, la SEC [abrió un nuevo capítulo para la inversión en cripto](https://cointelegraph.com/news/sec-conversion-grayscale-large-cap-crypto-fund-etf) al aprobar la transformación del Grayscale Digital Large Cap Fund (GDLC) en un ETF (fondo cotizado en bolsa) al contado, que cotizará en el NYSE Arca con 775 millones de dólares en activos bajo gestión.

Para Grayscale, esto supone un cambio importante respecto a la estructura de fondo cerrado que hasta ahora limitaba el acceso de los inversores. Ahora, tanto los inversores institucionales como los minoristas pueden obtener exposición a las criptomonedas a través de un vehículo regulado y familiar, sin necesidad de gestionar monederos ni claves privadas.

Por desgracia, como ocurre con otros ETF estadounidenses, los inversores de la UE tendrán un acceso limitado, que por lo general exige la condición de inversor profesional o el uso de un bróker fuera de la zona de la UE.

Lo que llama la atención no es solo el tamaño, sino la composición:


## Del Index Universe al CoinDesk 5

El ETF ofrece una exposición diversificada a las principales criptomonedas, con **Bitcoin dominando con ~80 %** de la cartera, complementado por **Ethereum, XRP, Solana y Cardano**.

Aunque la mayoría da por hecho que el ETF simplemente replica las cinco mayores criptomonedas por capitalización de mercado, en realidad sigue el **índice CoinDesk 5 (CD5)**: una metodología compleja diseñada para inversores institucionales que ofrece pistas sutiles sobre hacia dónde podría fluir a continuación el dinero institucional, lo que hace que merezca la pena mirarla de cerca.

El CD5 se sitúa en la cúspide de una **metodología de cuatro niveles** desarrollada por [CoinDesk Indices](https://indices.coindesk.com). A diferencia de las populares clasificaciones por capitalización de mercado de sitios como CoinGecko o CoinPaprika, el CD5 se creó específicamente para inversores institucionales. Esto significa que su compleja metodología puede sorprender a los entusiastas de las criptomonedas: es mucho más selectiva que limitarse a elegir las monedas más grandes por capitalización de mercado.

<figure class="article__figure">
<img src="/research/coindesk-methodology.svg" alt="Los cuatro niveles de la metodología de CoinDesk">
<figcaption class="article__figure__caption">Los cuatro niveles de la metodología de CoinDesk</figcaption>
</figure>

### Index Universe

Todo comienza con el **Index Universe**: la metodología de base de CoinDesk para determinar qué criptomonedas merecen siquiera ser tenidas en cuenta para la inversión institucional.

El Index Universe parte de las **250 mayores criptomonedas por capitalización de mercado** y a continuación aplica una serie de estrictos filtros de calidad:

**Lo que se elimina de inmediato:**

❌ **Stablecoins** (USDT, USDC): están pensadas para mantenerse estables, no para crecer  
❌ **Memecoins** (sí, aunque valgan miles de millones): demasiado volátiles y especulativas  
❌ **Tokens envueltos (wrapped) o en staking**: son derivados, no los activos subyacentes  
❌ **Monedas de privacidad**: las preocupaciones regulatorias las convierten en un rotundo no para las instituciones  
❌ **Valores (securities)**: cualquier cosa que pudiera clasificarse como valor según la legislación estadounidense  

**Lo que sobrevive debe demostrar liquidez:**

✅ Cotizar en al menos 3 exchanges importantes con pares USD/USDC  
✅ Al menos uno de esos listados debe tener más de 90 días de antigüedad (nada de tokens recién salidos)  
✅ Negociación activa en los últimos 30 días en varios exchanges  
✅ Estar disponible para clientes estadounidenses en al menos un exchange  
✅ Un volumen diario de negociación mediano suficiente (el punto medio de la actividad diaria de negociación a lo largo de 90 días)  

Este proceso de filtrado da lugar al Index Universe: una lista depurada de criptomonedas que cumplen los estándares de la inversión institucional. Aunque CoinDesk no publica el número exacto de criptomonedas que superan estos filtros, es probable que ronden las 50 monedas; lo único que sabemos con certeza es que son más de 20 pero menos de 250.

Esta falta de transparencia sobre el tamaño real del Index Universe es una de las limitaciones actuales, junto con la documentación aún incipiente del CD5. Una mayor claridad sobre estas cifras ayudaría a los inversores a entender mejor la naturaleza del índice.

:::playbook

Los índices de CoinDesk ofrecen una forma sencilla de seguir los flujos de dinero institucional. Veamos los dos índices más importantes: el CD20 y el CD5 (que es el que sigue el GDLC):

### CoinDesk 20

El [índice CoinDesk 20 (CD20)](https://indices.coindesk.com/coindesk20) toma este universo ya depurado y le añade una capa adicional de gestión de carteras. Es, además, la parte de la oferta mejor documentada en internet.

**Ponderación por capitalización con topes de seguridad**: la ponderación por capitalización de mercado del índice, que los usuarios de Deltabadger conocen del [bot de DCA con reajuste](https://deltabadger.com/academy/rebalanced-dca), se ajusta añadiendo topes (30 % como máximo para el mayor, 20 % para los demás). No queda del todo claro por qué se ha añadido el tope, y la documentación oficial de CoinDesk no lo explica.

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
<figcaption class="article__figure__caption">Asignación del índice CoinDesk 20 (CD20)</figcaption>
</figure>

**Reajuste trimestral**: cada tres meses, toda la cartera se recalibra en función de las condiciones actuales del mercado, con «reglas de amortiguación» para evitar una rotación excesiva.

Las reglas están diseñadas para evitar una rotación excesiva, dando preferencia a los componentes actuales del índice para permanecer en él aunque hayan bajado ligeramente en la clasificación.

El CD20 utiliza un **sistema de amortiguación**:

**Criterios de entrada**:
1. Un activo debe situarse entre los **40** primeros por volumen de negociación para ser tenido en cuenta  
2. **Los 15 primeros puestos**:  
- Van a los mayores activos por capitalización de mercado (con independencia de su estatus actual)  
3. **Los 5 puestos restantes**:  
- Tienen preferencia los componentes actuales clasificados entre el 16 y el 25 por capitalización de mercado  
- Si no hay suficientes componentes actuales que cumplan los requisitos, los nuevos activos mejor clasificados ocupan los puestos restantes  

**Criterios de salida**: un activo existente pierde su puesto si:  
1. Cae por debajo del puesto **50** en volumen de negociación (fallo de liquidez), O BIEN  
2. Cae por debajo del puesto **25** en capitalización de mercado (fallo de tamaño)  

Sin reglas de amortiguación, los activos que orbitan en torno a la línea de corte se añadirían y eliminarían constantemente cada trimestre, generando costes de transacción e inestabilidad innecesarios.

### CoinDesk 5

Sin embargo, el que se utiliza para el primer ETF multicripto no es el CD20, sino su hermano menor:

El **CD5** representa los 5 mayores activos del CD20, seleccionados por **capitalización de mercado** entre los componentes ya depurados del CD20. Dado que el CD20 ya aplica estrictos filtros de liquidez (incluido el cribado por volumen de negociación), el CD5 hereda estos estándares de calidad centrándose en los activos más grandes y líquidos.

El índice es mucho más reciente y todavía no cuenta con la misma cobertura en internet, pero, al estudiar su construcción, queda claro que se concibió para ser utilizado por las instituciones.

La diferencia clave con el CD20 es que **se eliminan los topes**. Mientras que el CD20 limita el mayor componente al 30 % y el resto al 20 %, el CD5 emplea una ponderación pura por capitalización de mercado. El resultado es que Bitcoin alcanza actualmente más del 80 % de la asignación: un baño de realidad que refleja la posición dominante de Bitcoin en el mercado y su perfil de liquidez. Esta concentración es una característica, no un defecto: garantiza que el índice refleje la verdadera jerarquía de capitalización de mercado de los activos cripto más líquidos.

Al igual que el CD20, el CD5 sigue el mismo calendario de reajuste trimestral, pero utiliza una **regla de amortiguación 4/6** más sencilla: los 4 mayores activos por capitalización de mercado del CD20 se incluyen automáticamente, mientras que los componentes existentes clasificados en el 5.º o 6.º puesto tienen preferencia para permanecer. Este proceso simplificado hace que el CD5 resulte especialmente idóneo para su implementación como ETF, ya que reduce la complejidad manteniendo unos rigurosos estándares institucionales.

<figure class="article__figure" data-controller="pie-chart" data-pie-chart-data-value="#F7931A,BTC,Bitcoin,79.35
#7349A4,ETH,Ethereum,10.63
#2F2C56,XRP,Ripple,5.78
#00FFA3,SOL,Solana,3.09
#0045D0,ADA,Cardano,1.14">
<div class="pie-chart-wrapper">
<svg data-pie-chart-target="svg" width="300" height="300" class="pie-chart"></svg>
<div data-pie-chart-target="legend" class="pie-legend"></div>
</div>
<figcaption class="article__figure__caption">Asignación del índice CoinDesk 5 (CD5)</figcaption>
</figure>

:::

### Resumen de la estructura del índice

Para resumir la metodología:

**Index Universe**: establece los criterios básicos de elegibilidad y filtra alrededor de 50 activos (?).  
**CD20**: aplica principios de gestión de carteras, entre ellos la ponderación por capitalización con topes, el cribado por volumen de negociación y el reajuste trimestral con reglas de amortiguación.  
**CD5**: selecciona los 5 mayores activos del CD20 por capitalización de mercado, elimina los topes y utiliza reglas de amortiguación simplificadas y optimizadas para la inversión institucional.

## La profecía autocumplida

Aunque está claro que los inversores institucionales se interesan por el conjunto del mercado cripto, hasta ahora solo unos pocos activos digitales cumplen los estrictos criterios de liquidez y regulación exigidos para su inclusión en un ETF.

Si observamos más de cerca la estructura de los índices, obtenemos pistas sobre hacia dónde fluirá el gran capital en un futuro próximo. La metodología de cuatro niveles no es solo una cuestión de gestión de riesgos: es una hoja de ruta para la asignación de capital institucional.

Esto es importante porque muchos critican que los índices se conviertan en profecías autocumplidas que conducen a una mayor concentración de capital. Cuando entradas masivas de dinero en los ETF persiguen el mismo y limitado conjunto de activos, los precios se inflan al margen de los fundamentales.

Michael Burry sostuvo, en una tesis muy célebre, que la inversión pasiva, como la de los ETF sobre el S&P 500, infla los precios de las acciones mediante entradas masivas de capital sin análisis fundamental, algo parecido a la dependencia de un esquema Ponzi de nuevos inversores. Advirtió de que esto podría desembocar en una crisis de liquidez cuando se produjeran las salidas, ya que la «puerta de salida» del mercado es estrecha.

Por otro lado, desde su última posición corta, el índice ha subido. ¿Ocurrirá lo mismo con el mercado de las criptomonedas?

La idea de inversión aquí es sencilla: **invertir en lo que está dentro del ETF**. Si el capital institucional fluye hacia los componentes del CD5, sus precios deberían beneficiarse de esta demanda estructural, con independencia de que uno crea o no en la tecnología subyacente.

### ¿El efecto dominó?

Nate Geraci, presidente de ETF Store, [ve implicaciones más amplias](https://twitter.com/NateGeraci/status/1939454629915619403) y sugiere que esta aprobación podría allanar el camino a ETF al contado individuales para activos como XRP, Solana y Litecoin. Esto permitiría a los inversores obtener una exposición selectiva a criptomonedas concretas a través de cuentas de inversión tradicionales.

<blockquote class="twitter-tweet">
<p lang="es" dir="ltr">Esta semana vence el plazo final de la SEC para el Grayscale Digital Large Cap ETF (GDLC)…<br><br>Contiene btc, eth, xrp, sol y ada.<br><br>Creo que hay *muchas probabilidades* de que se apruebe.<br><br>A ello le seguiría después la aprobación de ETF al contado individuales sobre xrp, sol, ada, etc.</p>&mdash; Nate Geraci (@NateGeraci) <a href="https://twitter.com/NateGeraci/status/1939454629915619403?ref_src=twsrc%5Etfw">29 de junio de 2025</a>
</blockquote>

## Mirando hacia el futuro

Cada hito regulatorio es una señal de la continua maduración del mercado cripto. La aprobación por parte de la SEC de ETF cripto diversificados inaugura la era de los índices cripto.

Como sabemos por los mercados tradicionales, los índices en forma de ETF y fondos de inversión son la principal vía por la que la gente invierte en el mercado. Hasta ahora, al mercado de las criptomonedas le faltaba este enfoque, el más evidente de todos.

Sin embargo, el lanzamiento del ETF GDLC crea una brecha de oportunidad: mientras que los inversores institucionales obtienen acceso a la indexación cripto profesional a través de ETF regulados, los inversores particulares se topan con barreras que exigen la condición de inversor profesional y otros trámites adicionales. Para la mayoría de los lectores, el GDLC seguirá estando probablemente fuera de su alcance.

### Nuestra misión

Esta brecha de accesibilidad es donde entra Deltabadger. Nuestra misión es hacer que las estrategias de indexación estén al alcance de todo el mundo, con ventajas clave:

En primer lugar, los particulares no están sujetos a los requisitos de liquidez como lo están los ETF. Esto nos da más flexibilidad a la hora de construir e implementar el índice. Invertir de forma indexada en tendencias emergentes como las memecoins manteniendo un enfoque profesional y pasivo está al alcance de la mano.

En segundo lugar, estamos desarrollando un potente motor de indexación (que se lanzará a finales de este año) que dará a los usuarios un control sin precedentes. Con acceso a más de 500 índices de CoinGecko y ponderaciones personalizables, podrás construir carteras que se ajusten con precisión a tu estrategia.

Este enfoque automatizado elimina la necesidad de una gestión manual y de decisiones arbitrarias. Del mismo modo que la inversión indexada a través de ETF y fondos de inversión se ha convertido en el estándar de los mercados tradicionales, creemos que la indexación automatizada será la opción por defecto para la inversión en cripto a largo plazo.

La mayor ventaja de los índices es que proporcionan una gestión del riesgo natural: los proyectos fallidos quedan fuera automáticamente, igual que las empresas en quiebra salen del S&P 500. Y, a diferencia del reajuste trimestral de CoinDesk, los índices personalizados pueden adaptarse con mayor rapidez a medida que cambian las condiciones del mercado.

-

*¿Qué opinas de estos avances? ¿Invertirías en el CD5, el CD20 o te quedarías simplemente con Bitcoin? ¿ETF o una cartera de índice personalizada en autocustodia?*

