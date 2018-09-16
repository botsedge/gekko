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

More information on the [Average Directonal Movement Index](https://en.wikipedia.org/wiki/Average_directional_movement_index)

Required parameters:

 - optInTimePeriod

### adxr

The Average Directional Movement Index Rating is used as a risk indicator for a security in an [adx](#adx) system. It evaluates the risk (volatility) of a security by smoothing the amplitude readings of the trend function of the adx. It is calculated as follows

    ADX plus the ADX (n-time periods ago) divided by 2

Higher readings conform to lower risk and lower readings conform to higher risk.
A investor wanting to lower the portfolio risk will therefore use securities with higher adxr ratings.

Required parameters:

 - optInTimePeriod

### ao

More information about the [Awesome Oscillator](https://www.tradingview.com/wiki/Awesome_Oscillator_(AO))

This indicator does not require any parameters.

### apo

The Absolute Price Oscillator displays the difference between two exponential moving averages of a security's price and is expressed as an absolute value. It rates the trends strength in relation to the moving between the two moving averages with short-term momentum being the catalyst.

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

Required parameters:

 - optInTimePeriod

### cvi

Required parameters:

 - optInTimePeriod

### dema

Required parameters:

 - optInTimePeriod

### di

Required parameters:

 - optInTimePeriod

### dm

Required parameters:

 - optInTimePeriod

### dpo

Required parameters:

 - optInTimePeriod

### dx

Required parameters:

 - optInTimePeriod

### ema

Required parameters:

 - optInTimePeriod

### emv

This indicator does not require any parameters.

### fisher

Required parameters:

 - optInTimePeriod

### fosc

Required parameters:

 - optInTimePeriod

### hma

Required parameters:

 - optInTimePeriod

### kama

Required parameters:

 - optInTimePeriod

### kvo

Required parameters:

 - optInFastPeriod
 - optInSlowPeriod

### linreg

Required parameters:

 - optInTimePeriod

### linregintercept

Required parameters:

 - optInTimePeriod

### linregslope

Required parameters:

 - optInTimePeriod

### macd

Required parameters:

 - optInFastPeriod
 - optInSlowPeriod
 - optInSignalPeriod

### marketfi

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
