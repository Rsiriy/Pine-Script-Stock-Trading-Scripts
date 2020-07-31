## Candlestick Pattern Identifier 

The Candlestick Pattern Identifier is a technical indicator developed using Pine Script for TradingView. 

## Table of Contents
 
1. [Introduction](#introduction)
2. [How it Works](#how-it-works)
    1. [Criteria](#criteria)
    2. [Formulas](#formulas)
3. [Examples](#examples)
    1. [One Candle Pattern](#One-Candle-Pattern)
4. [Installation](#installation)

## Introduction 

In the investing world, my approach to stock trading would probably have me labeled as a "chartist" as I try to derive as much information I can from a 
stock chart as opposed to other resources like financial documents or news reports. This type of analysis is called "Technical Analysis" and is the core
aspect of my trading strategy. When I began to notice that I missed glaringly obvious signals which could've prevented failed trades, I realized that I 
could avoid this problem entirely by programming tools to automatically perform the analysis on my behalf. The Candlestick Pattern Identifier is 
one of these tools I programmed to asisst me with my stock trading. 

The Candlestick Pattern Identifier is a technical indicator I developed using research by Thomas Burkowski in his book "Encyclopedia of Candlestick Patterns".
In his research, Burkowski researched candlestick patterns based on their efficiency and frequency and created a comprehesnive list of top performing patterns 
across both upward and downward markets. When using Burkowski's research, I created my own set of parameters to look for patterns with high frequency and high percentage of success. 

## How it Works 

### Criteria 

The indicator holds formulas I created for 25 candlestick patterns and outputs them onto a chart in TradingView for any stock across any timeframe.
All candlestick patterns were selected from Encyclopedia of Candlestick Patterns based on the criteria below 

- Probability of success: 66% or higher in up or down markets (Ensures 2/3 trades made on pattern have a chance of success)
- Frequency: 10 or higher (Avoids rare patterns with small sample size)
- Simplicity: 4 candles or less (Formulas with increased complexity will create less signals)

### Formulas

I created formulas using comparison operators on the "open", "close", "high", and "low" properties of a candlestick. 

For instance, the formula "green_candle = (open < close)" would flag candles that look like the below. 

![Alt text](/images/greencandle.png) 

Likewise, the formula "red_candle = (open > close)" would flag candles that look like the below. 

![Alt text](/images/redcandle.png)

*Note that the "High" and "Low", regardless of candle properties, are absolutes and will always be above or below the candle body*

## Examples 

The examples below are indicators I created for one candle, two candle, three candle, and four candle patterns. I included all relevant declarations 
in each example for easier readibility.  

### One Candle Pattern  

![Alt text](/images/RisingWindowCode.png) 

The first line designates the property of the candle being flagged. In this case I am looking for green candles (price going up) 

The second line defines that the entire candle from yesterday is smaller than the body of today's candle. This was done to strengthen the original 
definition of a rising window and producer stronger and more valid signals. 

The third line defines that the highest point from yesterday is less than the lowest point of today to establish a gap between the two candles.  

<img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/RisingWindowExample.png?raw=true" width="150" height="300">.           <img src="https://github.com/Rsiriy/Pine-Script-Stock-Trading-Scripts/blob/master/images/RisingWindowTR.png?raw=true" width="150" height="300">

## Installation 
