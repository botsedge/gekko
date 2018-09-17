# Tulip indicators

When writing [your own strategy](./creating_a_trading_method.md) you can use all indicators offered by [the Tulip Indicators library](https://tulipindicators.org/). Gekko will pass the correct market data to Tulip and you only have to provide the `optIn` configurable parameters.

## Install

### Bash on Windows, OSX or Linux

Open your terminal. Then:

```
cd ~/gekko
npm install tulind --no-save
```

## Example

If you want to use the MACD indicator from Tulip, you need to register it in your strategy like so:

    method.init = function() {
      var customMACDSettings = {
        optInFastPeriod: 10,
        optInSlowPeriod: 21,
        optInSignalPeriod: 9
      }

      // add the indicator to the strategy
      this.addTulipIndicator('mymacd', 'macd', customMACDSettings);
    }

    method.check = function() {
      // use indicator results
      var result = this.tulipIndicators.mymacd.result;
      var macddiff = result['macd'] - result['macdSignal'];

      // do something with macdiff
    }

## Tulip Indicators

Here is a list of all supported indicators, click on them to see the required parameters.

- [AD](#ad)
- [ADOSC](#adosc)
- [ADX](#adx)
- [ADXR](#adxr)
- [AO](#ao)
- [APO](#apo)
- [AROON](#aroon)
- [AROONOSC](#aroonosc)
- [ATR](#atr)
- [AVGPRICE](#avgprice)
- [BBANDS](#bbands)
- [BOP](#bop)
- [CCI](#cci)
- [CMO](#cmo)
- [CVI](#cvi)
- [DEMA](#dema)
- [DI](#di)
- [DM](#dm)
- [DPO](#dpo)
- [DX](#dx)
- [EMA](#ema)
- [EMV](#emv)
- [FISHER](#fisher)
- [FOSC](#fosc)
- [HMA](#hma)
- [KAMA](#kama)
- [KVO](#kvo)
- [LINREG](#linreg)
- [LINREGINTERCEPT](#linregintercept)
- [LINREGSLOPE](#linregslope)
- [MARKETFI](#marketfi)
- [MASS](#mass)
- [MEDPRICE](#medprice)
- [MFI](#mfi)
- [MSW](#msw)
- [NATR](#natr)
- [NVI](#nvi)
- [OBV](#obv)
- [PPO](#ppo)
- [PSAR](#psar)
- [PVI](#pvi)
- [QSTICK](#qstick)
- [ROC](#roc)
- [ROCR](#rocr)
- [RSI](#rsi)
- [SMA](#sma)
- [STOCH](#stoch)
- [SUM](#sum)
- [TEMA](#tema)
- [TR](#tr)
- [TRIMA](#trima)
- [TRIX](#trix)
- [TSF](#tsf)
- [TYPPRICE](#typprice)
- [ULTOSC](#ultosc)
- [VHF](#vhf)
- [VIDYA](#vidya)
- [VOLATILITY](#volatility)
- [VOSC](#vosc)
- [VWMA](#vwma)
- [WAD](#wad)
- [WCPRICE](#wcprice)
- [WILDERS](#wilders)
- [WILLR](#willr)
- [WMA](#wma)
- [ZLEMA](#zlema)

## API

### ad

This indicator does not require any parameters.

### adosc

Required parameters:

 - optInFastPeriod
 - optInSlowPeriod

### adx

More information on the [**Average Directonal Movement Index**](https://en.wikipedia.org/wiki/Average_directional_movement_index)

Required parameters:

 - optInTimePeriod

### adxr

The **Average Directional Movement Index Rating** is used as a risk indicator for a security in an [adx](#adx) system. It evaluates the risk (volatility) of a security by smoothing the amplitude readings of the trend function of the adx. It is calculated as follows

    ADX plus the ADX (n-time periods ago) divided by 2

Higher readings conform to lower risk and lower readings conform to higher risk.
A investor wanting to lower the portfolio risk will therefore use securities with higher adxr ratings.

Required parameters:

 - optInTimePeriod

### ao

More information about the [**Awesome Oscillator**](https://www.tradingview.com/wiki/Awesome_Oscillator_(AO))

This indicator does not require any parameters.

### apo

The **Absolute Price Oscillator** displays the difference between two exponential moving averages of a security's price and is expressed as an absolute value. It rates the trends strength in relation to the moving between the two moving averages with short-term momentum being the catalyst.

Required parameters:

 - optInFastPeriod
 - optInSlowPeriod

### aroon

More information about the [Aroon](https://www.tradingview.com/wiki/Aroon) Indicator.

Required parameters:

 - optInTimePeriod

### aroonosc

The Aroon Oscillator belongs to the group of trend-following indicators and uses parts of the Aroon Indicator (namely "Aroon Up" and "Aroon Down") to indicate the strength of a current trend and the likelihood that it will continue. The Aroon Oscillator is calculated by subtracting Aroon Up from Aroon Down. Readings above zero indicate that an uptrend is present, while readings below zero indicate that a downtrend is present.

Required parameters:

 - optInTimePeriod

### atr

More information about the [Average True Range](https://www.tradingview.com/wiki/Average_True_Range_(ATR))

Required parameters:

 - optInTimePeriod

### avgprice

The average price indicator calculates the mean of the open, high, low, and close of a bar

    open + high + low + close / 4

This indicator does not require any parameters.

### bbands

More information about [Bollinger Bands](https://www.tradingview.com/wiki/Bollinger_Bands_(BB))

Required parameters:

 - optInTimePeriod
 - optInNbStdDevs

### bop

The Balance of Power indicator measures the market strength of buyers against sellers by assessing the ability of each side to drive prices to an extreme level. The calculation is: 

    Balance of Power = (Close price – Open price) / (High price – Low price) 
    
   The resulting value can be smoothed by a moving average.

This indicator does not require any parameters.

### cci

More information about the [Commodity Channel Index](https://www.tradingview.com/wiki/Commodity_Channel_Index_(CCI))

Required parameters:

 - optInTimePeriod

### cmo

The Chande Momentum Oscillator is a technical momentum indicator. The indicator is created by calculating the difference between the sum of all recent higher closes and the sum of all recent lower closes and then dividing the result by the sum of all price movement over a given time period. The result is multiplied by 100 to give the -100 to +100 range. The defined time period is usually 20 periods.

    CMO = 100 * ((Sh - Sd)/ ( Sh + Sd ) )

Where:

Sh = Sum of the difference between the current close and previous close on up days for the specified period. Up days are days when the current close is greater than the previous close.

Sd = Sum of the absolute value of the difference between the current close and the previous close on down days for the specified period. Down days are days when the current close is less than the previous close.

Required parameters:

 - optInTimePeriod

### cvi

More information about the [Chaikin Volatility Index](https://www.tradingview.com/wiki/Chaikin_Oscillator) also called the Chaikin Oscillator

Required parameters:

 - optInTimePeriod

### dema

More information about the [DEMA](https://en.wikipedia.org/wiki/Double_exponential_moving_average)

Required parameters:

 - optInTimePeriod

### di

More information about the [Directional Indicator](https://en.wikipedia.org/wiki/Average_directional_movement_index)

Required parameters:

 - optInTimePeriod

### dm

More information about the [Directional Movement Index](https://en.wikipedia.org/wiki/Average_directional_movement_index)

Required parameters:

 - optInTimePeriod

### dpo

More information about the [Detrended Price Oscillator](https://en.wikipedia.org/wiki/Detrended_price_oscillator)

Required parameters:

 - optInTimePeriod

### dx

More information about the [Directional Movement Index](https://en.wikipedia.org/wiki/Average_directional_movement_index)

Required parameters:

 - optInTimePeriod

### ema

Exponential Moving Average (EMA) is similar to Simple Moving Average (SMA), measuring trend direction over a period of time. However, whereas SMA simply calculates an average of price data, EMA applies more weight to data that is more current. Because of its unique calculation, EMA will follow prices more closely than a corresponding SMA.

    EMA = (K x (C - P)) + P

Where: 
C = Current Price 
P = Previous periods EMA (A SMA is used for the first periods calculations) 
K = Exponential smoothing constant

Required parameters:

 - optInTimePeriod

### emv

More information about the [Ease of Movement](https://www.tradingview.com/wiki/Ease_of_Movement_(EOM))

This indicator does not require any parameters.

### fisher

The Fisher Transform is a technical indicator that converts prices into a Gaussian normal distribution. The indicator enables traders to create a nearly Gaussian probability density function by normalizing prices. That is, the transformation makes peak swings relatively rare events and unambiguously identifies price reversals on a chart. 

    Y = 0.5 * ln ((1+X)/(1-X)).
 
Where:

"ln" denotes the abbreviated form of the natural logarithm.

"X" denotes the transformation of price to a level between -1 and 1 for ease of calculation

Required parameters:

 - optInTimePeriod

### fosc

The forecast oscillator attempts to predict price action by comparing the results of a linear regression trendline to the actual price for that day. Positive values of the oscillator occur when the forecast price is above the actual price and negative values when the forecast price is below. If prices are consistently below the forecast, then a downturn in prices is likely. Conversely, if prices are consistently above the forecast then an upturn in prices is likely.

Required parameters:

 - optInTimePeriod

### hma

Basic forms of moving averages like the Simple Moving Average lag price. The Exponential and Weighted Moving Averages were developed to address this lag by placing more emphasis on more recent data. The Hull Moving Average in contrast is an extremely fast and smooth moving average, it almost eliminates lag altogether and manages to improve smoothing at the same time.

    HMA= WMA(2*WMA(n/2) − WMA(n)),sqrt(n))

Required parameters:

 - optInTimePeriod

### kama

The Kaufman adaptive moving average belongs to the group of "intelligent" indicators. It´s concept addresses the fact that noisy markets should have a lagging indicator and trending markets should have a leading indicator. So it adapts itself to lag in sideways markets and lead in trending markets.

    KAMA(t) = KAMA(t-1) + sc(t) x (Price-KAMA(t-1))

Where:
KAMA(t) is the new adaptive moving average value
KAMA(t-1) is the previous adaptive moving average value
Price is the current price
sc(t) is the smoothing constant

Required parameters:

 - optInTimePeriod

### kvo

The Klinger Volume Oscillator measures trends of money flows based upon volume. The KO is derived from three types of data: the high-low price range, volume, and accumulation/distribution. Price range is a measure of movement and the force behind that movement is volume. Accumulation is when the sum of today's [high]+[low]+[close] is greater than yesterday's. Distribution is when today's sum is less than the yesterday's. When the sums are equal, the existing trend is maintained.

Required parameters:

 - optInFastPeriod
 - optInSlowPeriod

### linreg

The Linear Regression is a smoothing functions that works by preforming linear least squares regression over a moving window. It then uses the linear model to predict the value for the current bar

Required parameters:

 - optInTimePeriod

### linregintercept

More information about the [Linear Regression Intercept](https://en.wikipedia.org/wiki/Simple_linear_regression)

Required parameters:

 - optInTimePeriod

### linregslope

More information about the [Linear Regression Intercept](https://en.wikipedia.org/wiki/Simple_linear_regression)

Required parameters:

 - optInTimePeriod

### macd

More information about the [MACD](https://www.tradingview.com/wiki/MACD_(Moving_Average_Convergence/Divergence))

Required parameters:

 - optInFastPeriod
 - optInSlowPeriod
 - optInSignalPeriod

### marketfi

The Market Facilitation Index indicator combines price and volume in the analysis to establish the effectiveness of price movement by computing the price movement per volume unit. To calculate the Market Facilitation Index indicator the difference between the low and the high price are taken and divided by the volume.

This indicator does not require any parameters.

### mass

Required parameters:

 - optInTimePeriod

### medprice

This indicator does not require any parameters.

### mfi

Required parameters:

 - optInTimePeriod

### msw

Required parameters:

 - optIn

### natr

Required parameters:

 - optInTimePeriod

### nvi

This indicator does not require any parameters.

### obv

This indicator does not require any parameters.

### ppo

Required parameters:

 - optInFastPeriod
 - optInSlowPeriod

### psar

Required parameters:

 - optInAcceleration
 - optInMaximum

### pvi

This indicator does not require any parameters.

### qstick

Required parameters:

 - optInTimePeriod

### roc

Required parameters:

 - optInTimePeriod

### rocr

Required parameters:

 - optInTimePeriod

### rsi

Required parameters:

 - optInTimePeriod

### sma

Required parameters:

 - optInTimePeriod

### stoch

Required parameters:

 - optInFastKPeriod
 - optInSlowKPeriod
 - optInSlowDPeriod

### sum

Required parameters:

 - optInTimePeriod

### tema

Required parameters:

 - optInTimePeriod

### tr

This indicator does not require any parameters.

### trima

Required parameters:

 - optInTimePeriod

### trix

Required parameters:

 - optInTimePeriod

### tsf

Required parameters:

 - optInTimePeriod

### tsf

Required parameters

 - optInTimePeriod

### typprice

This indicator does not require any parameters.

### ultosc

Required parameters:

 - optInTimePeriod1
 - optInTimePeriod2
 - optInTimePeriod3

### vhf

Required parameters

 - optInTimePeriod

### vidya

Required parameters

 - optInFastPeriod
 - optInSlowPeriod
 - optInAlpha

### volatility

Required parameters:

 - optInTimePeriod

### vosc

Required parameters

 - optInFastPeriod
 - optInSlowPeriod

### vwma

Required parameters:

 - optInTimePeriod

### wad

This indicator does not require any parameters.

### wcprice

This indicator does not require any parameters.

### wilders

Required parameters:

 - optInTimePeriod
 - 
### willr

Required parameters:

 - optInTimePeriod

### wma

Required parameters:

 - optInTimePeriod

### zlema

Required parameters:

 - optInTimePeriod
