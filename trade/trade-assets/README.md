# Assets

Minara supports six categories of tradable assets: crypto perpetuals, tokenized stock perpetuals, commodity perpetuals, pre-IPO perpetuals, index perpetuals, and FX perpetuals. All are settled in USDC on Lighter's or Hyperliquid's on-chain order book depending on which wallet you trade from. Use the asset selector at the top of the trade screen to filter by category.

***

## Crypto perpetuals

Minara trades crypto perpetuals on Lighter and Hyperliquid, both high-performance on-chain order books. Perpetuals are futures contracts with no expiry date. You hold them as long as you want, and the contract price tracks the underlying asset via a funding rate mechanism.

<figure><img src="../../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>

**Supported assets**: the perpetuals listed on Lighter and Hyperliquid are available in Minara, including Bitcoin (BTC), Ethereum (ETH), Solana (SOL), and many others. Popular pairs include BTC/USDC, ETH/USDC, and SOL/USDC. You can also trade hundreds of altcoin perpetuals from the same interface. The full list appears in the asset selector at `/app/trade/perps`.

**No expiry**: unlike traditional futures, perpetuals don't settle on a fixed date. You open a position and hold it indefinitely, or until you close it or get liquidated.

**Funding rates**: to keep the perpetual price close to the spot price, a funding payment is exchanged between long and short holders periodically. When funding is positive, longs pay shorts; when negative, shorts pay longs. The current funding rate is shown in the trading interface.

**Leverage**: Minara supports up to 25x leverage on crypto perpetuals. Leverage multiplies both gains and losses. See [Margin and leverage](../../trading-reference/margin-and-leverage.md) for how margin requirements work.

The trading panel is on the right side of the screen. Two order types are available: **Market** (executes immediately at the best available price) and **Trigger** (executes when the asset reaches a price you specify). Both Autopilot and Copilot use this same underlying interface.

{% hint style="info" %}
Minara routes orders through Lighter's or Hyperliquid's on-chain order book, depending on the wallet selected. Execution is non-custodial: your funds stay in your exchange account, not held by Minara.
{% endhint %}

***

## Stocks

{% hint style="danger" %}
**Stock perpetuals are not actual shares.** You do not receive dividends, voting rights, or any equity ownership. You are taking a leveraged position on price movement only. Positions can be liquidated. Closing a position ends your exposure; there is no settlement or delivery.
{% endhint %}

Minara gives you access to tokenized stocks as perpetual contracts on the supported perps exchanges. You can trade Apple (AAPL), Tesla (TSLA), NVIDIA (NVDA), Amazon (AMZN), Microsoft (MSFT), and other major equities using the same USDC-based interface as crypto. Availability varies by exchange; check the asset selector for the active wallet.&#x20;

<figure><img src="../../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

These are perpetual contracts whose price tracks the underlying stock. Trading is available 24/7, including outside traditional market hours, though liquidity and spreads may vary when the underlying exchange is closed.

The trading mechanics are identical to crypto perpetuals: positions are denominated in USDC, funding rates apply, leverage is available (at lower maximums than crypto perps), and orders can be placed as market or trigger orders. Filter by **Stocks** in the asset selector to see all available instruments.

***

## Commodities

Minara supports trading commodity perpetuals including precious metals, energy, and industrial metals where the active exchange lists them.

* **Gold (GOLD)**: gold perpetual priced in USDC, 24/7 without a brokerage account.
* **Silver (SILVER)**: silver perpetual, priced in USDC.
* **Crude oil (CL)**: WTI crude oil perpetual.
* **Brent oil (BRENTOIL)**: Brent crude perpetual.
* **Copper (COPPER)**: copper perpetual.
* **Natural gas (NATGAS)**: natural gas perpetual.

<figure><img src="../../.gitbook/assets/image (162).png" alt=""><figcaption></figcaption></figure>

More commodities may be added as exchange listings expand. Filter by **Commodities** in the asset selector to see the current list.

Commodity perpetuals work the same way as crypto perpetuals: no expiry, funding rates, and leverage available. Commodities are available 24/7, though liquidity varies by session.

{% hint style="info" %}
Commodity perpetuals track the underlying commodity price via oracle feeds. You are not taking delivery of physical goods.
{% endhint %}

***

## Pre-IPO

{% hint style="warning" %}
Pre-IPO perpetuals track a synthetic valuation of a private company, not tradable equity. There are no shares, no ownership, and no claim on the company. You are taking a leveraged position on price movement only, and positions can be liquidated.
{% endhint %}

Minara lists pre-IPO perpetuals that track the estimated valuation of private companies before they go public. You trade them in USDC with the same interface as every other perpetual. Available symbols include SPCX-USDC, CBRS-USDC, and QNT-USDC, with leverage up to 20x. Filter by **Pre-IPO** in the asset selector to see the current list.

<figure><img src="../../.gitbook/assets/trade-assets-pre-ipo.png" alt="Pre-IPO perpetuals in the asset selector"><figcaption></figcaption></figure>

Because there is no public market for these companies, prices reference off-market valuation data via oracle feeds. Liquidity can be thinner than in crypto or stock perpetuals.

***

## Indices

Minara lists perpetuals that track major equity indices, priced in USDC and available 24/7. Supported symbols include:

* **SP500-USDC**: S&P 500 index perpetual, up to 50x leverage.
* **XYZ100-USDC**: Nasdaq-100 style tech index perpetual, up to 30x leverage.
* **JP225-USDC**: Nikkei 225 (Japan) index perpetual, up to 20x leverage.
* **KR200-USDC**: KOSPI 200 (Korea) index perpetual, up to 20x leverage.

<figure><img src="../../.gitbook/assets/trade-assets-indices.png" alt="Index perpetuals in the asset selector"><figcaption></figcaption></figure>

Index perpetuals work the same way as other perpetuals: no expiry, funding rates, and market or trigger orders. Filter by **Indices** in the asset selector to see the current list.

***

## FX

Minara lists foreign-exchange perpetuals that track major currency pairs against the US dollar, priced in USDC with leverage up to 50x. Supported symbols include:

* **JPY-USDC**: Japanese yen perpetual.
* **EUR-USDC**: euro perpetual.

<figure><img src="../../.gitbook/assets/trade-assets-fx.png" alt="FX perpetuals in the asset selector"><figcaption></figcaption></figure>

FX perpetuals trade 24/7 and use the same funding-rate mechanism as other perpetuals. Filter by **FX** in the asset selector to see the current list.

***

## Fees

Trading fees apply to all perpetual trades and vary by asset class. See [Trading fees](../trading-fees.md) for the current rate schedule.
