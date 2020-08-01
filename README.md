## Candlestick Pattern Identifier 

The Candlestick Pattern Identifier is a technical indicator developed using Pine Script for TradingView. 

## Table of Contents
 
1. [Introduction](#introduction)
2. [How it Works](#how-it-works)
    1. [Criteria](#criteria)
    2. [Formulas](#formulas)
3. [Examples](#examples)
    1. [One Candle Pattern](#One-Candle-Pattern)
    2. [Two Candle Pattern](#Two-Candle-Pattern)
    3. [Three Candle Pattern](#Three-Candle-Pattern)
    4. [Four Candle Pattern](#Four-Candle-Pattern)
4. [Installation](#installation)

## Introduction 

In the investing world, my approach to stock trading would probably have me labeled as a "chartist" as I try to derive as much information I can from a 
stock chart as opposed to other resources like financial documents or news reports. This type of analysis is called "Technical Analysis" and is the core
aspect of my trading strategy. When I began to notice that I missed glaringly obvious signals which could've prevented failed trades, I realized that I 
could avoid this problem entirely by programming tools to automatically perform the analysis on my behalf. The Candlestick Pattern Identifier is 
one of these tools I programmed to asisst me with my stock trading. 

The Candlestick Pattern Identifier is a technical indicator I developed using research by Thomas Bulkowski in his book "Encyclopedia of Candlestick Patterns".
In his research, Bulkowski researched candlestick patterns based on their efficiency and frequency and created a comprehesnive list of top performing patterns 
across both upward and downward markets. When using Bulkowski's research, I created my own set of parameters to look for patterns with high frequency and high percentage of success. 

## How it Works 

### Criteria 

The indicator holds formulas I created for 25 candlestick patterns and outputs them onto a chart in TradingView for any stock across any timeframe.
All candlestick patterns were selected from Encyclopedia of Candlestick Patterns based on the criteria below 

- Probability of success: 66% or higher in up or down markets **(Ensures 2/3 trades made on pattern have a chance of success)**
- Frequency: 10 or higher **(Avoids rare patterns with small sample size)**
- Simplicity: 4 candles or less **(Formulas with increased complexity will create less signals)**

### Formulas

I created formulas using comparison operators on the "open", "close", "high", and "low" properties of a candlestick.

For instance, the formula "green_candle = (open < close)" would flag candles that look like the below. Green candles signify a time period in which the price of a stock went higher. 

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/greencandle.png?raw=true" width="100" height="300"></p>

Likewise, the formula "red_candle = (open > close)" would flag candles that look like the below. Red candles signify a time period in which the price of a stock went lower. 

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/redcandle.png?raw=true" width="150" height="245"></p>

*Note that the "High" and "Low", regardless of candle properties, are absolutes and will always be above or below the candle body*

## Examples 

The examples below are indicators I created for one candle, two candle, three candle, and four candle patterns. I included all relevant declarations 
in the code each example for easier readibility. Patterns designated as "one candle", for example, are patterns that only require one candle to be detected. 

### One Candle Pattern - Rising Window   

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/RisingWindowExample.png?raw=true" width="150" height="300"></p>

The Rising window is a one candle pattern with 75% success in markets trending upward and 72% in markets trending downward as per Bulkowski. The defining characteristic of this pattern is that the second candle is significantly above the candle before it. 

##### Code for Rising Window 

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/RisingWindowCode.png?raw=true"></p>

The first line shows the declaration for the candle I am looking for, in this case I am looking for green candles (price going up).

The second line defines that the entire candle from yesterday is smaller than the body of today's candle. This was done to strengthen the original 
definition of a rising window and producer stronger and more valid signals. 

The third line defines that the highest point from yesterday is less than the lowest point of today, establishing a gap between the two candles.  

##### Example of Rising Window in Trading View 

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/RisingWindowTR.png?raw=true" width="150" height="300"></p>

The picture above shows an example of a Rising Window that my indicator caught in JP Morgan ($JPM) stock. JPM closed at $95.82 the day it was flagged and closed at $101.37 the next day, representing a 5.5% gain. A buy order placed at $95.82 would've made for profitable trade.  

### Two Candle Pattern - Bullish Belt Hold  

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/BullishBeltHoldExample.png?raw=true" width="150" height="300"></p>

The Bullish Belt Hold is a two candle pattern with 71% success in markets trending upward and downward. The "Bullish" in its name represents the sentiment behind this formation as Bullish markets are markets trending upward. The defining characteristics of this are: The current day candle must open below the preceeding day candle and close above the midpoint of the preceeding day candle. 

##### Code for Bullish Belt Hold 

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/BullishBeltHoldCode.png?raw=true"></p>

The first line shows the declarations for the candles I am looking for. In this case I'm looking for a red candle from yesterday and a green candle today.

The second line defines that today's close must be greater than or equal to the midpoint of the previous day candle. 

The third line defines that the close must be less than the yesterday's open. This, in combination with the line above, create the upper limit for today's candle as being in between the midpoint and the open of yesteradays candle. 

The fourth line defines that the open of today's candle must be lower than the lowest point of yesterdays candle which defines the lower limit for today's candle. 

##### Example of Bullish Belt Hold in Trading View 

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/BullishBeltHoldTR.png?raw=true" width="150" height="300"></p>

The example above is an example of a Bullish Belt Hold flagged by my indicator in RingCentral ($RNG) stock. RNG closed at $236.51 the day it was flagged and closed at $253.11 the next day, representing a gain of 7.02%. A buy order at $236.51 would've made for a profitable trade. 

### Three Candle Pattern - Deliberation

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/DeliberationExample.png?raw=true" width="150" height="300"></p>

The Deliberation pattern is commonly associated with indecision in the market and the possibility of a reversal, but Bulkowski's research highlights that 
a reversal seldom occurs and that this pattern instead acts as a continaution of the existing trend (77% in upward markets and 75% in downward markets). The defining characteristic of this pattern is progressively smaller and smaller candles. 

##### Code for Deliberation

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/DeliberationCode.png?raw=true"></p>

The first line shows the declaration for the candles I am looking for. In this case, I'm looking for green candles going back as far as two days ago. 

The second line defines that the body of the candle two days ago is larger than the one one day ago. The third line defines that the body of the candle one day
ago is larger than the candle today. Both of these lines establish the progression of smaller and smaller candles. 

The third and fourth line define that the high point of the preceeding day candle is lower than the low point of the candle after it. This is done from the candle two days ago to the candle today to establish the uptrend. 

##### Example of Deliberation in Trading View 

<p align="center"><img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/DeliberationTR.png?raw=true"></p>


## Installation 
