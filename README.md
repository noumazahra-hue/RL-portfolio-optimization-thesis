# RL-portfolio-optimization-thesis
Master’s thesis on reinforcement learning for dynamic portfolio optimization using financial market data.
<div align="center">
  <img src="https://via.placeholder.com/1200x400/1e3a8a/ffffff?text=Reinforcement+Learning+for+Dynamic+Portfolio+Optimization" 
       alt="Thesis Banner" width="100%"/>
  
  <h1>Reinforcement Learning for Dynamic Portfolio Optimization in Volatile Markets</h1>
  
  <p>
    <strong>Master's Thesis •IHEC SFAX • 2025</strong><br>
    Author: Zahra Nouma<br>
  
  </p>

  <p>

    <a href="https://github.com/noumazahra-hue/rl-portfolio-optimization">
      <img src="https://img.shields.io/badge/GitHub-Repo-blue?style=flat&logo=github" alt="GitHub">
    </a>
    <img src="https://img.shields.io/badge/Python-3.8%2B-blue?style=flat&logo=python" alt="Python">
    <img src="https://img.shields.io/badge/RLlib-2.0+-orange?style=flat" alt="RLlib">
    <img src="https://img.shields.io/badge/Performance-%2B45%25%20vs%20S%26P%20500-success?style=flat" alt="Performance">
  </p>
</div>


# Abstract

This thesis proposes a **reinforcement learning (RL)** framework to dynamically optimize long-only portfolios in volatile markets.  
Portfolio allocation is framed as a Markov Decision Process and agents are trained using **PPO** and **DDPG** with a rich state space (prices, volatility, macro, FinBERT sentiment, correlations, technicals) and a multi-objective reward (Sharpe – drawdown penalty – turnover penalty).

**Key empirical results** (2010–2023 backtest, strict out-of-sample 2020–2023):
- Cumulative return: **671.7%** vs S&P 500 **462.1%** (+45% edge)
- Sharpe ratio: **1.24** vs S&P 0.78
- Max drawdown March 2020: **–13.4%** vs S&P **–33.9%**
- 2022 bear market: drawdown halved through autonomous sector rotation
- Diebold-Mariano test: p < 0.001 vs all benchmarks

The PPO agent demonstrates **crisis alpha**, **negative beta during crashes**, and **autonomous regime adaptation**, making it a production-ready alternative to classical mean-variance optimization.

# Repository Structure

rl-portfolio-optimization/
├── data/ # Raw & processed market data (not committed)
├── notebooks/ # Exploratory analysis & ablation studies
├── src/
│ ├── environment.py # Custom Gym-like trading environment
│ ├── state.py # State space construction
│ ├── reward.py # Sharpe + drawdown + turnover reward
│ ├── agents/ # PPO & DDPG training scripts (RLlib)
│ └── backtest.py # Walk-forward backtesting & metrics
├── results/ # Precomputed plots: equity curves, drawdowns, beta, heatmaps
├── docs/ # Thesis PDF, slides, appendix
├── requirements.txt
└── README.md


# Key Contributions

- Rich multimodal state space with **FinBERT sentiment**, **VIX/OVX**, **FRED macros**, dynamic correlations  
- Multi-objective reward explicitly penalizing drawdowns and turnover  
- Strict crisis-period out-of-sample testing (2020–2023)  
- Autonomous regime adaptation (negative beta, sector rotation)  
- Statistically significant outperformance (DM test p < 0.001)  

# Main Results Summary

| Metric                        | PPO Agent     | S&P 500      | 60/40        | Improvement          |
|-------------------------------|---------------|--------------|--------------|--------------------|
| Cumulative Return (2010–2023) | 671.7%        | 462.1%       | ~300%        | +45%               |
| Sharpe Ratio                  | 1.24          | 0.78         | 0.91         | +59% vs S&P        |
| Max Drawdown (Mar 2020)       | –13.4%        | –33.9%       | –22.4%       | >60% reduction     |
| Max Drawdown (2022)           | –12.8%        | –25.4%       | —            | ~50% reduction     |
| Post-2020 Recovery            | +112%         | +81%         | —            | +31% faster        |

> **Note:** All results are precomputed. The `results/` folder contains equity curves, drawdowns, and analytical plots. Full code for training and backtesting is in 'Thesis2.ipynb'.
> # Project 2 — Momentum + Trend-Following Trading System *(Work in Progress)*

# Strategy Objective
Build a **systematic long-only momentum + trend-following trading system** that:  

- Captures medium-term trends in high-quality stocks and Bitcoin  
- Avoids major drawdowns during crashes and bear markets  
- Maintains reasonable volatility and strong risk-adjusted returns  

# Target Markets
- Large-cap US technology & growth stocks: **AAPL, MSFT, AMZN, NVDA, META**  
- **Bitcoin (BTC-USD)** as a high-volatility diversifier  

# Trading Frequency
- Daily signals and position updates (low turnover expected)  
- Rebalance / check every trading day (close of day)  

# Core Idea / Edge
- Trend filter: **MA50 > MA200**  
- Momentum confirmation: positive **20-day return**  
- Avoid buying weakening trends or after big run-ups  
- **Inverse volatility weighting** to reduce exposure to most volatile assets  

>  *Code, backtests, and results will be added once the strategy is fully implemented.*
