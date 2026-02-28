# TradingView Volume Profile Indicator

A Pine Script v6 volume profile indicator that displays horizontal volume bars at price levels, colored green (buying/support) and red (selling/resistance), with POC line and Value Area highlighting.

## Screenshot

<!-- Add a screenshot of the indicator on a chart here -->

## Features

- **Stacked volume bars** — green (buy) and red (sell) side-by-side at each price level
- **Point of Control (POC)** — dashed line at the highest-volume price level
- **Value Area** — shaded region covering 70% of total volume (configurable)
- **Rolling lookback** — analyzes the last N bars (default 200)
- **Candle direction classification** — close > open = buy volume, close ≤ open = sell volume
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

## License

MIT
