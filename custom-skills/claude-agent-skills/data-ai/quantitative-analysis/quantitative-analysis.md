---
name: quantitative-analysis
description: This skill provides expertise in quantitative finance and algorithmic trading. This skill should be used for financial modeling, trading strategy development, backtesting, risk analysis, or portfolio optimization. Uses pandas, numpy, and scipy with realistic market assumptions.
enforcement_level: HIGH
violation_consequence: Trading strategies may fail, risk may be miscalculated, or backtests may be unrealistic, leading to financial losses
---

# Quantitative Analysis

This skill provides comprehensive guidance for algorithmic trading and financial modeling. It emphasizes robust backtesting and risk-adjusted returns.

## Overview

Quantitative analysis involves developing trading strategies, analyzing risk, optimizing portfolios, and forecasting financial markets. This skill provides systematic approaches to quantitative finance.

## Focus Areas

### Trading Strategy Development

- Strategy design and implementation
- Backtesting frameworks
- Performance metrics
- Strategy optimization

### Risk Metrics

- VaR (Value at Risk)
- Sharpe ratio
- Maximum drawdown
- Risk-adjusted returns

### Portfolio Optimization

- Markowitz optimization
- Black-Litterman model
- Risk parity
- Asset allocation

### Time Series Analysis

- Forecasting techniques
- Trend analysis
- Seasonality detection
- ARIMA models

### Options Pricing

- Greeks calculation
- Option pricing models
- Volatility analysis
- Risk management

### Statistical Arbitrage

- Pairs trading
- Mean reversion strategies
- Cointegration analysis
- Spread trading

## Approach

1. Data quality first - clean and validate all inputs
2. Robust backtesting with transaction costs and slippage
3. Risk-adjusted returns over absolute returns
4. Out-of-sample testing to avoid overfitting
5. Clear separation of research and production code

## Output Format

Provide:
- Strategy implementation with vectorized operations
- Backtest results with performance metrics
- Risk analysis and exposure reports
- Data pipeline for market data ingestion
- Visualization of returns and key metrics
- Parameter sensitivity analysis

## Best Practices

- Use pandas, numpy, and scipy
- Include realistic assumptions about market microstructure
- Test strategies thoroughly before deployment
- Monitor performance continuously
- Document all assumptions

Use pandas, numpy, and scipy. Include realistic assumptions about market microstructure.

