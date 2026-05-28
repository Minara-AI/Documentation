# Trading Fees

Your total fee on each trade is the sum of two components: an exchange fee charged by the underlying perpetuals venue (Lighter or Hyperliquid), and a Minara fee charged by the platform. Fees vary by venue, asset class, and trading mode.

A maker order adds liquidity to the order book, typically a limit order that does not fill immediately. A taker order removes liquidity, such as a market order or a limit order that matches an existing order on entry.

## Hyperliquid

<table>
<thead>
  <tr>
    <th rowspan="2">Asset class</th>
    <th rowspan="2">Mode</th>
    <th colspan="3">Maker</th>
    <th colspan="3">Taker</th>
  </tr>
  <tr>
    <th>Hyperliquid</th><th>Minara</th><th>Total</th>
    <th>Hyperliquid</th><th>Minara</th><th>Total</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="2"><strong>Crypto</strong></td>
    <td>Autopilot</td>
    <td>0.015%</td><td>0.015%</td><td><strong>0.03%</strong></td>
    <td>0.045%</td><td>0.015%</td><td><strong>0.06%</strong></td>
  </tr>
  <tr>
    <td>Copilot</td>
    <td>0.015%</td><td>0.04%</td><td><strong>0.065%</strong></td>
    <td>0.045%</td><td>0.03%</td><td><strong>0.075%</strong></td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Commodities &amp; stocks</strong></td>
    <td>Autopilot</td>
    <td>0.003%</td><td>0.015%</td><td><strong>0.018%</strong></td>
    <td>0.009%</td><td>0.015%</td><td><strong>0.024%</strong></td>
  </tr>
  <tr>
    <td>Copilot</td>
    <td>0.003%</td><td>0.04%</td><td><strong>0.043%</strong></td>
    <td>0.009%</td><td>0.03%</td><td><strong>0.039%</strong></td>
  </tr>
  <tr>
    <td><strong>Prediction markets</strong></td>
    <td>Copilot</td>
    <td>0.04%</td><td>0.04%</td><td><strong>0.08%</strong></td>
    <td>0.056%</td><td>0.03%</td><td><strong>0.086%</strong></td>
  </tr>
</tbody>
</table>

Commodities and stocks share one fee tier and cover silver, crude oil, gold, and tokenized US equities. Prediction markets cover binary outcome contracts traded on Hyperliquid's Outcome market, powered by Outcomexyz.

## Lighter

Lighter uses a flat fee schedule across all supported assets; there is no per-asset-class differentiation.

<table>
<thead>
  <tr>
    <th rowspan="2">Mode</th>
    <th rowspan="2">Component</th>
    <th>Maker</th>
    <th>Taker</th>
  </tr>
  <tr></tr>
</thead>
<tbody>
  <tr>
    <td rowspan="3"><strong>Autopilot</strong></td>
    <td>Lighter fee</td>
    <td>0.005%</td>
    <td>0.005%</td>
  </tr>
  <tr>
    <td>Minara fee</td>
    <td>0.015%</td>
    <td>0.015%</td>
  </tr>
  <tr>
    <td>Total</td>
    <td><strong>0.020%</strong></td>
    <td><strong>0.020%</strong></td>
  </tr>
  <tr>
    <td rowspan="3"><strong>Copilot</strong></td>
    <td>Lighter fee</td>
    <td>0.005%</td>
    <td>0.005%</td>
  </tr>
  <tr>
    <td>Minara fee</td>
    <td>0.030%</td>
    <td>0.040%</td>
  </tr>
  <tr>
    <td>Total</td>
    <td><strong>0.035%</strong></td>
    <td><strong>0.045%</strong></td>
  </tr>
</tbody>
</table>
