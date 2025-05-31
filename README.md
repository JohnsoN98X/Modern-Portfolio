# 📊 Modern Portfolio Theory – Practical Implementation

This project provides a practical implementation of **Modern Portfolio Theory**, combining theoretical rigor with numerical tools that are applicable in real-world portfolio construction and financial analysis.

> ⚠️ **Note:** This project does **not** aim to present any scientific innovation or empirical analysis of portfolio results.  
> Its sole purpose is to offer a practical, modular framework for applying classical portfolio theory, along with examples of how to use it effectively.

---

## 📦 Project Structure

The project currently includes four core classes:

### 1. `MeanVarianceOpt`
Performs **Mean-Variance Optimization** as defined in modern finance literature.  
While most academic references focus on analytical solutions, these are often impractical. This class performs **convex numerical optimization** using the `cvxpy` library.

### 2. `CAPM`
A lightweight, high-level utility class for quick analysis based on the **Capital Asset Pricing Model (CAPM)**.  
It provides easy access to key financial ratios (Beta, Sharpe, Treynor) and generates intuitive visualizations to compare asset performance.

### 3. `ModernPortfolio`
An **abstract base class** designed to encapsulate shared attributes and methods.  
This class is **not intended to be used directly**, but serves as the foundation for the two classes above.

### 4. `FactorsModelOLS` 🆕
A custom-built implementation of **Ordinary Least Squares (OLS)** regression, designed to support factor-based asset return modeling.  
This class does not rely on external modeling libraries such as `sklearn` or `statsmodels`, and instead computes all regression outputs (coefficients, residuals, standard errors, t-statistics, p-values) from scratch.  
Useful both as a learning tool and as a modular analytical component for multi-factor models or predictive pipelines.

---

## 🚀 Getting Started
### 🧰 Requirements

| Purpose               | Libraries Needed                                                                 |
|------------------------|----------------------------------------------------------------------------------|
| Running the classes   | `pandas`, `numpy`, `cvxpy`, `scipy` *(for t-distribution in FactorsModelOLS)*     |
| Running the notebooks | `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`              |

---

## ⚙️ Data Input Requirements

- All inputs must be `pandas.Series` or `pandas.DataFrame` depending on the class:
  - `MeanVarianceOpt` expects a DataFrame of asset returns.
  - `CAPM` expects a DataFrame of assets and a separate Series for market returns.
  - `FactorsModelOLS` expects a DataFrame (or array) of features and a 1D Series/array of target values.
- The index must represent dates. If not explicitly a `DatetimeIndex`, the class will attempt to convert it using `pd.to_datetime()`.
- Inputs must contain **daily log-returns**, or stationary features depending on the context.
- Outputs (e.g., coefficients, statistical significance) are provided in clean tabular form.

---

## 📡 Data Source & Usage

The dataset used for testing was retrieved using the `ib_insync` library connected to Interactive Brokers (IB).  
Due to IB’s licensing policy, **raw market data is excluded** from this repository.

---

## ⚠️ Disclaimer

All tools and methods in this project are provided **strictly for educational and research purposes**.  
They do not constitute investment advice or financial recommendations.  
The author assumes no liability for any actions taken based on this code or its output.
