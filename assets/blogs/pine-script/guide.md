![Sheen Banner](https://raw.githubusercontent.com/74Thirsty/74Thirsty/main/assets/pine-script.png)

---

# **Pine Script on TradingView: A Comprehensive Guide**

### **Introduction**

In the world of modern trading, automation, technical analysis, and custom indicators are increasingly essential for traders who want to gain an edge in the markets. TradingView, a widely-used web-based charting platform, provides a unique solution in this space: Pine Script. Pine Script is a domain-specific language (DSL) designed for writing custom technical indicators, alerts, and automated trading strategies directly on TradingView charts.

Pine Script allows traders and developers to create their own indicators and strategies without relying on third-party software or complex integrations. Its simplicity and integration into TradingView make it particularly appealing for both beginners and advanced traders.

---

### **History of Pine Script**

Pine Script was first introduced in 2012 by TradingView to provide a lightweight scripting language tailored to traders’ needs. Unlike general-purpose programming languages like Python or C++, Pine Script focuses solely on financial data analysis and charting. Over the years, TradingView has iteratively improved Pine Script, with **version 5 (Pine v5)** being the most current as of 2025. Each version brought enhancements in performance, usability, and available functions.

Originally, Pine Script had limitations such as no support for custom functions or user-defined types. With Pine v4 and v5, these limitations were addressed by allowing more complex data structures, better error handling, and integration with alerts and strategy testing features.

---

### **Why Pine Script?**

There are several reasons why traders use Pine Script:

1. **Native Integration:** Pine Script is built into TradingView, which eliminates the need for external platforms or APIs. Scripts run directly on charts and update in real-time as price data changes.

2. **Ease of Use:** Pine Script is beginner-friendly. Its syntax is straightforward, resembling other scripting languages but with abstractions specifically designed for trading.

3. **Custom Indicators:** Traders can create indicators tailored to their strategy. From moving averages to complex multi-timeframe oscillators, Pine Script allows complete customization.

4. **Automated Alerts:** Scripts can generate alerts when conditions are met, which can be used for manual trading notifications or automated trading through third-party services.

5. **Strategy Backtesting:** Pine Script supports strategy testing, allowing traders to simulate how their indicators or strategies would have performed historically.

---

### **Basic Structure of Pine Script**

Pine Script is structured around a few fundamental concepts:

1. **Version Declaration:** Each script must begin by declaring the version.

   ```pinescript
   //@version=5
   ```

2. **Indicator or Strategy Declaration:**

   * **Indicator:** Used for plotting values on the chart.

     ```pinescript
     indicator("My Indicator", overlay=true)
     ```
   * **Strategy:** Used for backtesting buy/sell signals and simulating trades.

     ```pinescript
     strategy("My Strategy", overlay=true)
     ```

3. **Inputs:** Allows users to customize parameters.

   ```pinescript
   length = input.int(14, title="Length")
   ```

4. **Calculations:** The logic of the indicator or strategy.

   ```pinescript
   smaValue = ta.sma(close, length)
   ```

5. **Plotting:** Visual representation on the chart.

   ```pinescript
   plot(smaValue, color=color.blue)
   ```

6. **Alerts:** Define conditions that trigger notifications.

   ```pinescript
   alertcondition(crossover(close, smaValue), title="Buy Alert", message="Price crossed above SMA")
   ```

---

### **Core Features of Pine Script**

#### **1. Built-in Functions**

Pine Script comes with numerous built-in functions for technical analysis:

* **Moving Averages:** `ta.sma()`, `ta.ema()`, `ta.wma()`
* **Oscillators:** `ta.rsi()`, `ta.stoch()`, `ta.macd()`
* **Volatility:** `ta.atr()`, `ta.stdev()`
* **Trend:** `ta.trendline()`, `ta.linreg()`
* **Math/Logic:** `math.max()`, `math.min()`, `ta.crossover()`, `ta.crossunder()`

These functions enable traders to implement almost any classical technical analysis methodology directly within TradingView.

#### **2. Plotting and Visualization**

Pine Script supports a wide range of visual elements:

* **Plot Lines:** `plot()`
* **Shapes/Arrows:** `plotshape()`, `plotarrow()`
* **Filled Areas:** `fill()`
* **Bar Colors:** `barcolor()`
* **Background Colors:** `bgcolor()`

This makes it possible to create highly visual indicators, highlighting market conditions like breakouts, trends, and reversals.

#### **3. Alerts**

Alerts are crucial for automation:

* `alertcondition()` allows you to define custom triggers.
* Alerts can be set to pop up in TradingView, send emails, or send webhooks to third-party services.

For example:

```pinescript
alertcondition(crossover(fastEMA, slowEMA), "Bullish Crossover", "Fast EMA crossed above Slow EMA")
```

#### **4. Strategy Testing**

Pine Script allows backtesting with the `strategy()` function:

* **Entry/Exit Orders:** `strategy.entry()`, `strategy.close()`
* **Position Sizing:** `strategy.risk.allow_entry_in()`
* **Performance Metrics:** Pine Script tracks profit, drawdown, and more.

Example:

```pinescript
if crossover(fastEMA, slowEMA)
    strategy.entry("Buy", strategy.long)
```

#### **5. Multi-Timeframe Analysis**

Pine Script supports fetching data from different timeframes:

```pinescript
higherClose = request.security(syminfo.tickerid, "1H", close)
```

This enables traders to implement strategies that consider both short-term and long-term trends.

---

### **Pine Script Data Types**

Understanding data types in Pine Script is crucial:

* **Series:** A sequence of values over time (most variables, like `close`, are series).
* **Float/Integer:** Single values for calculations.
* **Bool:** True/False conditions for logic and alerts.
* **Color/String/Line:** Used for visualization and styling.

Example:

```pinescript
isBullish = close > open  // Boolean
plot(isBullish ? high : low)  // Conditional plotting
```

---

### **Popular Indicators in Pine Script**

Many popular indicators are implemented in Pine Script, either built-in or custom:

1. **Moving Averages:** SMA, EMA, WMA, VWAP
2. **Oscillators:** RSI, MACD, Stochastic, CCI
3. **Volatility:** Bollinger Bands, Keltner Channels, ATR
4. **Trend Detection:** Parabolic SAR, ADX
5. **Custom Signals:** EMA crossovers with arrows, squeeze breakout indicators, divergences

Custom implementations often combine multiple indicators into one script for advanced decision-making.

---

### **Advanced Pine Script Techniques**

1. **User-Defined Functions**

```pinescript
f_sma(src, length) =>
    ta.sma(src, length)
```

2. **Arrays and Loops**
   Pine v5 supports arrays for storing multiple values:

```pinescript
arr = array.new_float()
array.push(arr, close)
```

3. **Conditional Logic**

```pinescript
colorBar = close > open ? color.green : color.red
barcolor(colorBar)
```

4. **Plotting Shapes Based on Conditions**

```pinescript
plotshape(crossover(fastEMA, slowEMA), style=shape.triangleup, location=location.belowbar, color=color.green)
```

5. **Multi-Timeframe Strategies**

```pinescript
hourClose = request.security(syminfo.tickerid, "1H", close)
```

---

### **Limitations of Pine Script**

While powerful, Pine Script has some limitations:

1. **Memory Limits:** Scripts cannot store unlimited historical data.
2. **Execution Limit:** Heavy computation can slow down charts.
3. **No External API Access:** Scripts can only interact with TradingView’s internal data.
4. **Limited Object-Oriented Capabilities:** Pine is not a full-fledged programming language like Python.
5. **Order Execution Restrictions:** Pine Script strategies are limited to backtesting; live execution requires broker integration through TradingView.

---

### **Best Practices**

1. **Keep Scripts Efficient:** Use series and avoid loops where possible.
2. **Modularize with Functions:** Improves readability and debugging.
3. **Use Inputs for Customization:** Makes scripts user-friendly.
4. **Combine Alerts with Visual Signals:** Enhances usability.
5. **Test Thoroughly:** Use backtesting features to validate before live trading.

---

### **Community and Sharing**

TradingView has a strong Pine Script community. Traders can:

* Publish indicators publicly.
* Share strategies and scripts for educational purposes.
* Use community scripts as templates or inspiration.

The platform supports collaborative learning and innovation in technical analysis.

---

### **Conclusion**

Pine Script is a powerful, accessible, and highly specialized language for traders looking to implement custom indicators, alerts, and strategies. Its seamless integration with TradingView charts, combined with extensive built-in technical analysis functions, allows traders to build complex systems with relatively minimal programming knowledge.

From simple moving average crossovers to advanced multi-timeframe strategies, Pine Script enables users to visualize, test, and automate trading ideas efficiently. Despite some limitations in terms of memory and external integration, its advantages make it an indispensable tool in the modern trader’s toolkit.

Whether you are a beginner looking to automate simple alerts or an advanced trader developing multi-layered strategies with custom signals, Pine Script offers the flexibility and capability to enhance trading analysis in a powerful, visual, and interactive environment.

---

# Indicators:

---

```pine
//@version=6
indicator("Keltner Channel", overlay=true)

// Inputs
length   = input.int(20, minval=1, title="EMA Length")
atrLen   = input.int(10, minval=1, title="ATR Length")
mult     = input.float(2.0, minval=0.1, title="ATR Multiplier")

// Basis and bands
basis = ta.ema(close, length)
atr   = ta.atr(atrLen)

upper = basis + mult * atr
lower = basis - mult * atr

// Plot
plot(basis, color=color.orange, title="Middle (EMA)")
plot(upper, color=color.green, title="Upper Band")
plot(lower, color=color.red, title="Lower Band")

fill(plot(upper), plot(lower), color=color.new(color.blue, 90))
```
> Classic Keltner Channel (EMA + ATR)

---

```pine
//@version=6
indicator("Keltner Channel (Original)", overlay=true)

length = input.int(20)
mult   = input.float(2.0)

basis = ta.sma(close, length)
range = ta.sma(ta.tr, length)

upper = basis + mult * range
lower = basis - mult * range

plot(basis, color=color.orange)
plot(upper, color=color.green)
plot(lower, color=color.red)
```

> Alternative (Original Keltner style – SMA + True Range)

---

```pine
//@version=6
indicator("MACD", overlay=false)

// Inputs
fastLen   = input.int(12, minval=1, title="Fast Length")
slowLen   = input.int(26, minval=1, title="Slow Length")
signalLen = input.int(9,  minval=1, title="Signal Length")

// MACD calculation
fastMA = ta.ema(close, fastLen)
slowMA = ta.ema(close, slowLen)

macdLine   = fastMA - slowMA
signalLine = ta.ema(macdLine, signalLen)
histogram  = macdLine - signalLine

// Plot
plot(macdLine,   title="MACD Line",   color=color.blue)
plot(signalLine, title="Signal Line", color=color.orange)
plot(histogram,  title="Histogram",   style=plot.style_columns,
     color=histogram >= 0 ? color.green : color.red)

// Zero line
hline(0, "Zero Line", color=color.gray)
```

> MACD (12, 26, 9)

---

```pine
//@version=6
indicator("EMA Crossover Arrows", overlay=true)

// Inputs
fastLen = input.int(9, title="Fast EMA Length")
slowLen = input.int(21, title="Slow EMA Length")

// EMAs
fastEMA = ta.ema(close, fastLen)
slowEMA = ta.ema(close, slowLen)

// Crossover signals
bullish = ta.crossover(fastEMA, slowEMA)
bearish = ta.crossunder(fastEMA, slowEMA)

// Plot EMAs
plot(fastEMA, color=color.blue, title="Fast EMA")
plot(slowEMA, color=color.orange, title="Slow EMA")

// Plot arrows
plotshape(bullish, title="Buy Signal", style=shape.triangleup, location=location.belowbar, color=color.green, size=size.small)
plotshape(bearish, title="Sell Signal", style=shape.triangledown, location=location.abovebar, color=color.red, size=size.small)
```

> EMA crossover

---

```pine
//@version=6
indicator("Bollinger Bands", overlay=true)

// Inputs
length = input.int(20, minval=1, title="Length")
mult   = input.float(2.0, title="StdDev Multiplier")
src    = input.source(close, title="Source")

// Calculate
basis = ta.sma(src, length)
dev   = mult * ta.stdev(src, length)
upper = basis + dev
lower = basis - dev

// Plot
plot(basis, color=color.orange, title="Middle Band")
plot(upper, color=color.green, title="Upper Band")
plot(lower, color=color.red, title="Lower Band")
fill(plot(upper), plot(lower), color=color.new(color.blue, 90))
```

> standard Bollinger Bands indicator in Pine Script v5:

---

```pine
//@version=6
indicator("Parabolic SAR + CCI", overlay=true)

// === Inputs ===
sarStep = input.float(0.02, "SAR Step", step=0.01)
sarMax  = input.float(0.2, "SAR Max", step=0.01)
cciLen  = input.int(14, "CCI Length")
cciOB   = input.int(100, "CCI Overbought")
cciOS   = input.int(-100, "CCI Oversold")

// === Calculations ===
sar = ta.sar(sarStep, sarStep, sarMax)
cci = ta.cci(close, cciLen)

// === Signals ===
buySignal  = cci < cciOS and close > sar
sellSignal = cci > cciOB and close < sar

// === Plotting ===
plot(sar, color=color.orange, style=plot.style_circles, linewidth=2, title="Parabolic SAR")

plotshape(buySignal, title="Buy Signal", location=location.belowbar, 
          style=shape.triangleup, color=color.green, size=size.small)
plotshape(sellSignal, title="Sell Signal", location=location.abovebar, 
          style=shape.triangledown, color=color.red, size=size.small)

// Optional: CCI overlay in separate pane
plot(cci, title="CCI", color=color.blue)
hline(cciOB, "Overbought", color=color.red)
hline(cciOS, "Oversold", color=color.green)
hline(0, "Zero Line", color=color.gray)
```

> Parabolic SAR + CCI indicator in Pine Script

---


