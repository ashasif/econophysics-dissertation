# A Statistical Mechanics Approach to Stock Market Dynamics

## Modelling Price Fluctuations, Volatility and Entropy

This repository contains the dissertation and Python implementation for the MSc research project:

**A Statistical Mechanics Approach to Stock Market Dynamics: Modeling Price Fluctuations and Volatility**

**Author:** Md Ashraful Alam Gazi  
**Programme:** MSc Data Science and its Applications  
**Institution:** University of Essex  
**Supervisor:** Dr. Alastair Litterick  
**Year:** 2025  

---

## Project Overview

Financial markets are traditionally modelled using approaches such as Geometric Brownian Motion and GARCH. Although these models are widely used, they do not always reproduce important characteristics of real financial markets, including heavy-tailed return distributions, volatility clustering, sudden price movements and extreme events.

This project investigates whether concepts from statistical mechanics can provide a more realistic description of financial-market behaviour.

The study compares traditional financial models with physics-inspired approaches across several major financial markets. It also examines whether entropy can provide additional information about market uncertainty and instability beyond conventional volatility measures.

The project combines financial econometrics, stochastic modelling, information theory, simulation and empirical data analysis within an econophysics framework.

---

## Research Objective

The main objective of the project is to compare traditional financial models with physics-inspired stochastic models and evaluate how effectively they reproduce real market behaviour.

The research focuses on the following questions:

- Can physics-inspired models reproduce empirical financial returns more accurately than traditional models?
- How well do different models capture heavy tails and non-Gaussian return distributions?
- Can GARCH reproduce volatility clustering more effectively than constant-volatility models?
- Can Langevin dynamics represent financial markets through the interaction of deterministic forces and random shocks?
- Can the Ornstein–Uhlenbeck process capture mean-reverting behaviour?
- Can the Fokker–Planck framework model the evolution of financial return distributions?
- Can Shannon and Tsallis entropy provide useful indicators of market uncertainty and instability?

---

## Financial Markets Analysed

The analysis uses daily financial data from 1992 to 2025, subject to the available history of each asset.

The markets included are:

| Market | Description |
|---|---|
| S&P 500 | Broad measure of the United States equity market |
| QQQ | Exchange-traded fund tracking the Nasdaq-100 |
| FTSE 100 | Major United Kingdom equity index |
| Nikkei 225 | Major Japanese equity index |
| Bitcoin | Decentralised cryptocurrency and high-volatility digital asset |

These assets were selected to represent different countries, market structures and volatility conditions.

Bitcoin provides an additional stress test because its return distribution and extreme price movements differ substantially from those of traditional equity indices.

---

## Models Implemented

### Geometric Brownian Motion

Geometric Brownian Motion is used as the classical baseline model.

It assumes that prices evolve through a constant drift and constant volatility process. The model is mathematically simple and widely used in finance, but its Gaussian assumptions make it difficult to reproduce heavy tails, volatility clustering and unusually frequent extreme events.

### GARCH(1,1)

The project includes two GARCH specifications:

- Zero-mean GARCH(1,1)
- GARCH(1,1) with drift

GARCH allows volatility to change over time. It is designed to capture volatility clustering, where periods of large price movements are followed by further turbulent periods and calm periods tend to occur together.

### Langevin Model

The Langevin model represents financial returns through two components:

- A deterministic component representing systematic market forces
- A stochastic component representing random shocks

This provides a direct connection between financial-market behaviour and stochastic processes used in physics.

### Ornstein–Uhlenbeck Process

The Ornstein–Uhlenbeck process introduces mean reversion.

Unlike Geometric Brownian Motion, which allows a variable to drift without a restoring force, the OU process pulls the variable towards a long-run level. In this project, the process is estimated using an AR(1) representation of log prices.

### Fokker–Planck–Kramers–Moyal Model

The Fokker–Planck framework models the evolution of an entire probability distribution rather than focusing only on individual simulated price paths.

The drift and diffusion functions are estimated empirically using Kramers–Moyal coefficients. The resulting FP–KM model uses state-dependent drift and diffusion to represent the distributional behaviour of financial returns.

Its main purpose is to reproduce:

- Non-Gaussian distributions
- Heavy tails
- State-dependent fluctuations
- Volatility bursts
- The evolution of return probabilities

---

## Entropy-Based Diagnostics

The project uses Shannon and Tsallis entropy to measure uncertainty and disorder in financial returns.

### Shannon Entropy

Shannon entropy measures uncertainty within a probability distribution. Higher values generally indicate greater disorder or unpredictability in market returns.

### Tsallis Entropy

Tsallis entropy generalises Shannon entropy and is useful for systems containing heavy-tailed distributions and non-standard statistical behaviour.

The study uses a Tsallis parameter of:

`q = 1.5`

Both entropy measures are calculated through rolling windows and compared with rolling market volatility.

Lead–lag relationships are also examined to determine whether changes in entropy occur before, during or after changes in volatility.

---

## Data Collection and Preprocessing

Historical market data were collected through the Yahoo Finance API using the `yfinance` Python library.

The preprocessing workflow includes:

1. Downloading daily market data
2. Sorting observations chronologically
3. Cleaning missing or invalid observations
4. Aligning datasets for cross-market comparison
5. Calculating daily logarithmic returns
6. Producing descriptive statistics
7. Measuring skewness and kurtosis
8. Testing normality and stationarity
9. Calculating rolling volatility
10. Calculating rolling Shannon and Tsallis entropy
11. Preparing data for model calibration and simulation

Parameters are estimated separately for each market so that every model reflects the characteristics of the relevant asset.

---

## Simulation Framework

The models are calibrated and simulated under a consistent experimental framework.

The main procedure includes:

- Using the same historical data for model calibration
- Starting simulations from a common initial price
- Applying fixed random seeds for reproducibility
- Generating 500 full-horizon simulation paths for each model and asset
- Simulating GBM, GARCH, Langevin and OU price or return paths
- Simulating the FP–KM model using state-dependent coefficients
- Applying the Euler–Maruyama numerical method where required
- Comparing simulated results with empirical market data
- Measuring model performance using several evaluation criteria

Using consistent conditions helps ensure that performance differences arise from the structures of the models rather than from different simulation settings.

---

## Statistical Analysis

The notebook includes the following analysis:

- Historical price visualisation
- Log-price analysis
- Daily log-return calculation
- Descriptive statistics
- Correlation matrices
- Skewness and kurtosis
- Jarque–Bera normality tests
- Augmented Dickey–Fuller stationarity tests
- ARCH-effect tests
- Rolling annualised volatility
- Empirical return distributions
- Empirical cumulative distribution functions
- Shannon entropy
- Tsallis entropy
- Entropy and volatility comparisons
- Lead–lag correlation analysis
- Model parameter calibration
- Monte Carlo simulations
- Model ranking and comparison

---

## Model Evaluation

No single metric can fully describe the quality of a financial model. The project therefore uses a multi-criteria evaluation framework.

### Root Mean Squared Error

RMSE measures how closely simulated price paths follow historical prices.

A lower RMSE indicates better price-path accuracy.

### Akaike Information Criterion

AIC evaluates statistical fit while penalising unnecessary model complexity.

Lower values indicate a better balance between fit and complexity.

### Bayesian Information Criterion

BIC also evaluates model fit and complexity but applies a stronger penalty for additional parameters.

Lower values are preferred.

### Kolmogorov–Smirnov Statistic

The KS statistic compares the empirical and simulated cumulative return distributions.

A lower value indicates greater distributional similarity.

### Wasserstein Distance

The Wasserstein distance measures how far the simulated return distribution is from the empirical distribution.

Lower values indicate a closer distributional match.

### Entropy Comparison

Simulated Shannon and Tsallis entropy values are compared with the entropy observed in real market returns.

This evaluates whether a model reproduces the changing level of uncertainty within the market.

---

## Main Findings

### Financial returns are strongly non-Gaussian

The empirical return distributions contain heavy tails, volatility clustering, skewness and extreme observations that are not adequately represented by a normal distribution.

Bitcoin displays the most extreme return behaviour and is the most difficult asset for all models to reproduce.

### Geometric Brownian Motion provides a useful baseline but performs poorly overall

GBM is simple and interpretable, but its constant-volatility and Gaussian assumptions produce overly smooth price behaviour.

It underestimates heavy tails, volatility clustering and extreme market movements.

### GARCH captures volatility clustering effectively

The GARCH models improve substantially on GBM when modelling changing volatility.

GARCH performs particularly well in representing conditional heteroskedasticity and provides a strong balance between statistical fit and model complexity.

However, its simulated return distributions remain less realistic than those produced by the strongest physics-inspired models.

### Physics-inspired models improve distributional realism

The Langevin, Ornstein–Uhlenbeck and Fokker–Planck approaches generally reproduce empirical return distributions more closely than GBM.

They provide useful representations of random shocks, restoring forces, mean reversion and state-dependent market behaviour.

### FP–KM provides the strongest distributional fit

The Fokker–Planck–Kramers–Moyal model generally achieves the closest alignment with empirical return distributions.

It performs strongly according to the Kolmogorov–Smirnov and Wasserstein measures because its drift and diffusion functions are estimated directly from market data.

Its main strength is modelling return distributions rather than forecasting exact future prices.

### No single model dominates every evaluation metric

The results reveal clear trade-offs:

- GBM offers simplicity but limited realism.
- GARCH captures volatility clustering and performs well statistically.
- Langevin provides an interpretable force-and-noise framework.
- OU introduces mean-reverting behaviour.
- FP–KM provides the strongest distributional similarity.
- Entropy measures provide additional information about changing market uncertainty.

The findings support using multiple complementary models rather than relying on one model for every financial application.

### Entropy complements conventional volatility analysis

Shannon and Tsallis entropy generally respond to periods of market stress and changing volatility.

In some cases, entropy changes occur before volatility increases, suggesting that entropy may contain useful early information about instability.

However, entropy is not treated as a guaranteed crash-prediction tool. It is better understood as a complementary market-monitoring and risk-diagnostic measure.

---

## Practical Applications

The methods explored in this project may support future work in:

- Market-risk monitoring
- Volatility analysis
- Tail-risk estimation
- Stress testing
- Market-regime detection
- Financial stability dashboards
- Portfolio-risk analysis
- Early-warning research
- Quantitative-finance modelling
- Cryptocurrency risk analysis

The project also demonstrates why financial risk should not be assessed using Gaussian assumptions alone.

---

## Repository Contents

### Dissertation PDF

Contains the complete written dissertation, including the literature review, methodology, results, discussion, limitations and conclusions.

### Dissertation_Code.ipynb

Contains the Python implementation for:

- Data collection
- Data preprocessing
- Exploratory analysis
- Statistical testing
- Model calibration
- Monte Carlo simulation
- Entropy analysis
- Model evaluation
- Visualisation

### README.md

Provides an overview of the research, methodology, results and repository structure.

### LICENSE

Contains the licence governing the use of the repository.

---

## Technologies Used

The project was developed using Python and Jupyter Notebook.

Main libraries include:

- pandas
- NumPy
- SciPy
- Matplotlib
- Seaborn
- Statsmodels
- arch
- scikit-learn
- yfinance

---

## Running the Project

Clone the repository:

```bash
git clone https://github.com/ashasif/econophysics-dissertation.git
cd econophysics-dissertation
```

Install the required libraries:

```bash
pip install pandas numpy scipy matplotlib seaborn statsmodels arch scikit-learn yfinance jupyter
```

Open the Jupyter Notebook:

```bash
jupyter notebook Dissertation_Code.ipynb
```

Run the notebook cells in order.

An internet connection is required when downloading market data through Yahoo Finance.

---

## Limitations

The project has several limitations:

- The analysis is restricted to five markets.
- Daily data may not capture high-frequency market behaviour.
- The models simplify real trading behaviour and market microstructure.
- Transaction costs, liquidity and order-book effects are not explicitly included.
- Langevin and OU simulations rely on Gaussian innovations.
- Entropy results depend on rolling-window and binning choices.
- AIC and BIC are not directly available for the non-parametric FP–KM model.
- AR(1) proxy likelihoods are used for Langevin and OU comparisons.
- Historical model performance does not guarantee future forecasting accuracy.
- No model fully reproduces Bitcoin’s most extreme movements.

The repository should therefore be viewed as an academic comparative-modelling project rather than a production trading system.

---

## Future Work

Possible extensions include:

- Applying the models to intraday or transaction-level data
- Testing commodities, currencies, bonds and individual equities
- Estimating models separately across bull, bear and crisis regimes
- Developing hybrid OU–GARCH or Langevin–GARCH models
- Using non-Gaussian noise processes
- Expanding state-dependent Fokker–Planck models
- Combining entropy with machine-learning methods
- Testing out-of-sample forecasting performance
- Studying market contagion and cross-market entropy
- Developing real-time financial-instability dashboards

---

## Academic Contribution

This project provides an interdisciplinary comparison of traditional financial modelling and statistical mechanics.

It combines:

- Financial econometrics
- Econophysics
- Stochastic differential equations
- Information theory
- Monte Carlo simulation
- Probability-distribution modelling
- Empirical financial analysis
- Data science

The central conclusion is that traditional and physics-inspired models capture different aspects of financial behaviour.

GARCH remains valuable for volatility modelling, while physics-inspired models provide improved descriptions of non-Gaussian return distributions. Shannon and Tsallis entropy offer an additional perspective on market uncertainty that complements conventional measures of volatility.

---

## Citation

Please cite this work as:

Gazi, M. A. A. (2025). *A Statistical Mechanics Approach to Stock Market Dynamics: Modeling Price Fluctuations and Volatility*. MSc Dissertation, University of Essex.

BibTeX:

```bibtex
@mastersthesis{gazi2025statistical,
  author = {Md Ashraful Alam Gazi},
  title = {A Statistical Mechanics Approach to Stock Market Dynamics: Modeling Price Fluctuations and Volatility},
  school = {University of Essex},
  year = {2025},
  type = {MSc Dissertation}
}
```

---

## Licence

This repository is distributed under the MIT Licence.

See the `LICENSE` file for further details.

---

## Disclaimer

This repository was created for academic and research purposes.

The models, simulations and results presented in this project do not constitute financial advice, an investment recommendation or a trading strategy. Financial markets involve substantial uncertainty, and historical results do not guarantee future performance.
