# TradingView Volume Profile Indicator

A Pine Script v6 volume profile indicator that displays horizontal volume bars at price levels, colored green (buying/support) and red (selling/resistance), with POC line and Value Area highlighting.

## Screenshot

<!-- Add a screenshot of the indicator on a chart here -->

## Features

- **Stacked volume bars** — green (buy) and red (sell) side-by-side at each price level
- **Point of Control (POC)** — dashed line at the highest-volume price level
- **Value Area** — shaded region covering 70% of total volume (configurable)
- **VAH / VAL lines** — dashed lines marking Value Area High and Value Area Low
- **HVN / LVN labels** — flags high and low volume nodes on the profile
- **Rolling lookback** — analyzes the last N bars (default 200)
- **Buy/sell delta** — splits volume using high-low spread ratio (toggleable)
- **Fully configurable** — colors, row count, width, lookback, and value area percentage

## Installation

1. Open [TradingView](https://www.tradingview.com/) and navigate to any chart
2. Click **Pine Editor** at the bottom of the screen
3. Delete any existing code and paste the contents of `volume-profile.pine`
4. Click **Add to chart**

## Inputs

| Input | Default | Description |
|---|---|---|
| Lookback Period | 200 | Number of bars to analyze |
| Number of Rows | 24 | Price bins for the profile |
| Profile Width | 50 | Width of the profile in bars |
| Value Area % | 70 | Percentage of volume for Value Area |
| Show Buy/Sell Delta | true | Show stacked green/red bars per bin (off = single color) |
| Show Level Labels | true | Show POC, VAH, VAL labels on the profile |
| Show HVN/LVN | true | Show High/Low Volume Node labels |
| HVN Threshold % | 75 | Bins above this % of max volume are flagged HVN |
| LVN Threshold % | 25 | Bins below this % of max volume are flagged LVN |
| Buy Volume Color | Green (40% transparent) | Color for buying volume |
| Sell Volume Color | Red (40% transparent) | Color for selling volume |
| POC Line Color | Yellow | Color of the Point of Control line |
| Value Area Color | Blue (85% transparent) | Value Area background shading |

## How It Works

On the last bar of the chart, the indicator:
1. Finds the highest high and lowest low over the lookback period
2. Divides that range into equal price bins
3. Assigns each bar's volume to a bin based on its midpoint (HL/2), classified as buy or sell by candle direction
4. Draws proportionally-scaled green/red boxes at each price level
5. Marks the POC (highest-volume bin) with a dashed line
6. Shades the Value Area by expanding outward from the POC until the configured percentage of total volume is captured

## Key Levels Explained

| Level | Full Name | What It Means |
|---|---|---|
| **POC** | Point of Control | The price level with the most traded volume. This is where the market spent the most time and agreed on price — acts as a magnet that price tends to revisit. |
| **VAH** | Value Area High | The upper boundary of the Value Area. Price above VAH is considered expensive relative to recent trading — can act as resistance or signal a breakout if price holds above it. |
| **VAL** | Value Area Low | The lower boundary of the Value Area. Price below VAL is considered cheap — can act as support or signal a breakdown if price falls through it. |
| **HVN** | High Volume Node | A price bin with significantly more volume than average (default: above 75% of max). These are areas of high acceptance where the market consolidated — price tends to slow down or reverse at HVNs. |
| **LVN** | Low Volume Node | A price bin with significantly less volume than average (default: below 25% of max). These are areas the market moved through quickly — price tends to move fast through LVNs, making them potential breakout/breakdown zones. |

## License

MIT
