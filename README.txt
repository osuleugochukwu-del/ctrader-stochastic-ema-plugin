# Stochastic EMA Sequential Signal — cTrader Web Plugin

This is the first web-plugin build of the supplied C# indicator.

## Logic preserved

- K Period: 20
- K Slowing: 7
- D Period: 7
- Simple moving averages for stochastic smoothing
- Overbought: 80
- Oversold: 20
- Signal EMA: 10
- Trend Filter EMA: 300, enabled by default
- Maximum Bars For Sequence: 100
- Maximum Bars To EMA: 100
- Closed-candle-only behavior
- BUY: K and D first cross below oversold, then bullish K/D cross, then price crosses above Signal EMA while above Trend EMA.
- SELL: K and D first cross above overbought, then bearish K/D cross, then price crosses below Signal EMA while below Trend EMA.

## Important architecture note

A web-based cTrader plugin can access historical trendbars and live quote/event data through the cTrader Plugin SDK. This build therefore renders its own lightweight chart inside the plugin and draws the BUY/SELL arrows there. It does not inject Chart.DrawIcon into cTrader's native chart because Chart.DrawIcon is an Algo API indicator operation, not a web-plugin operation.

## Install

1. Host `index.html` on a HTTPS web host.
2. In cTrader Web, create a web-based plugin using the hosted URL.
3. Open the plugin.
4. Select the symbol and timeframe.
5. Adjust parameters if desired.

The page uses cTrader's official web Plugin SDK imports from esm.sh, so no npm build is required for this prototype.
