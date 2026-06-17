# Markowitz Portfolio Optimization with Python

## Overview

This project implements **Harry Markowitz's Mean-Variance Optimization** theory to construct an efficient portfolio from Indian financial assets. The analysis uses CVXPY for quadratic programming to identify optimal asset allocations and generates the efficient frontier through Monte Carlo simulations, demonstrating the trade-off between risk and expected returns.

## Project Description

### Objective
To develop a data-driven portfolio optimization framework that:
- Analyzes historical price data from Indian financial assets
- Calculates risk-return metrics using log returns and covariance matrices
- Identifies optimal portfolio weights that maximize expected returns
- Visualizes the efficient frontier and compares optimal vs. random portfolios

### Key Achievements

#### 1. **Mean-Variance Optimization**
- Formulated and solved a quadratic programming problem using CVXPY
- Portfolio of 10 Indian financial assets:
  - **6 Stocks**: Wipro, Tech Mahindra, Reliance, Tata Motors, Infosys, Hyundai
  - **4 ETFs**: HDFC, ICICI, Kotak, Motilal
- 3-month historical price data
- Estimated expected returns and covariance matrices from daily log returns
- Identified optimal portfolio weights through constrained optimization

#### 2. **Efficient Frontier Construction**
- Generated 1,000 random portfolio allocations via Monte Carlo simulations
- Calculated risk-return trade-offs for each allocation
- Built correlation and covariance matrices across all assets
- Visualized efficient frontier as scatter plot of risk vs. return

#### 3. **Comprehensive Data Analysis & Visualization**
- Daily log returns for all 10 assets (10 subplots)
- Comparative bar chart showing average returns per asset (0.06% – 0.51%)
- Efficient frontier scatter plot highlighting:
  - Random portfolio allocations
  - Optimal portfolio (red point)
  - Risk-return trade-off relationship

## Technical Implementation

### Libraries & Dependencies
```python
import pandas as pd          # Data manipulation
import numpy as np           # Numerical computations
import matplotlib.pyplot as plt  # Visualization
import cvxpy as cp          # Convex optimization
import random               # Monte Carlo simulations
```

### Methodology

#### Step 1: Data Preprocessing
- Load historical closing prices from CSV files
- Handle data alignment across different assets
- Remove incomplete data (e.g., latest ETF prices)

#### Step 2: Calculate Log Returns
```python
def calculate_log_returns(df):
    log_returns = np.log(df['Close'] / df['Close'].shift(1))
    return log_returns
```

#### Step 3: Build Covariance Matrix
- Compute correlation between each asset pair
- Construct covariance matrix: `Cov = Correlation × Std_Dev₁ × Std_Dev₂`

#### Step 4: Optimize Portfolio Weights
Solve the optimization problem:
```
Maximize: w^T μ (expected return)
Subject to:
  - Σ wᵢ = 1 (weights sum to 1)
  - wᵢ ≥ 0 (no short selling)
  - wᵢ ≤ 1 (individual constraints)
```

#### Step 5: Generate Efficient Frontier
- Create 1,000 random weight allocations
- Calculate risk and return for each allocation
- Plot to visualize efficient frontier

## Results

### Average Log Returns by Asset
| Asset | Average Return |
|-------|-----------------|
| Tata Motors (Stock) | 0.513% |
| Kotak (ETF) | 0.437% |
| ICICI (ETF) | 0.399% |
| Wipro (Stock) | 0.378% |
| Reliance (Stock) | 0.367% |
| Hyundai (Stock) | 0.347% |
| Infosys (Stock) | 0.313% |
| Motilal (ETF) | 0.303% |
| Tech Mahindra (Stock) | 0.264% |
| HDFC (ETF) | 0.065% |

### Optimal Portfolio Weights
The optimizer identified **Tata Motors** as the highest return asset (≈99.9% allocation), representing the maximum return solution under the given constraints.

### Efficient Frontier Insights
- **Frontier Shape**: Classic hyperbolic curve showing the risk-return trade-off
- **Diversification Effect**: Random portfolios cluster around the frontier
- **Optimal Point**: Highlighted in red on the scatter plot
- **Correlation Impact**: Covariance matrix reveals correlations between stocks and ETFs

## Visualizations

The notebook generates 5 key visualizations:

1. **Log Returns Over Time** (10 subplots)
   - Daily price movements for each asset
   - Shows volatility patterns and trends

2. **Average Returns Comparison** (Bar Chart)
   - Comparative performance across all assets
   - Easy identification of high/low performers

3. **Efficient Frontier** (Scatter Plot)
   - 1,000 random portfolio allocations (blue points)
   - Optimal portfolio allocation (red point)
   - Risk (x-axis) vs. Return (y-axis)

## Usage

### Running the Notebook
1. Open `ITFE_Project_2.ipynb` in Google Colab or Jupyter Notebook
2. Upload required CSV files with historical price data
3. Execute cells sequentially
4. Visualizations will display automatically

### Data Requirements
Prepare CSV files with the following structure:
```
Date,Close
2024-02-04,XXXX.XX
2024-02-03,XXXX.XX
...
```

### Customization
To use different assets or time periods:
- Replace CSV file paths in data import cells
- Adjust `calculate_log_returns()` function if needed
- Modify `points = 1000` to generate more/fewer frontier points

## Theoretical Background

### Markowitz Modern Portfolio Theory
- **Efficient Frontier**: Set of optimal portfolios offering maximum expected return for a given risk level
- **Mean-Variance Analysis**: Assumes investors prefer higher returns and lower volatility
- **Covariance Matters**: Portfolio risk depends on individual asset volatility AND correlations

### Key Assumptions
1. Returns follow a normal distribution
2. No transaction costs or taxes
3. No short selling allowed
4. Divisible assets with no minimum purchase
5. Risk measured by standard deviation/variance

## Files in This Repository

- `ITFE_Project_2.ipynb` - Main Jupyter notebook with all analysis
- `README.md` - This file

## Future Enhancements

- [ ] Add risk-free rate and Capital Market Line (CML)
- [ ] Implement Sharpe Ratio optimization
- [ ] Include transaction costs and constraints
- [ ] Enable short selling scenarios
- [ ] Add real-time data integration (yfinance API)
- [ ] Performance backtesting on out-of-sample data
- [ ] Interactive Plotly visualizations
- [ ] Monte Carlo simulations with 10,000+ portfolios

## Mathematical Formulation

### Covariance Matrix Calculation
```
C[i,j] = ρ(i,j) × σᵢ × σⱼ

where:
  ρ(i,j) = correlation between assets i and j
  σᵢ, σⱼ = standard deviations
```

### Portfolio Return
```
E[Rp] = Σ wᵢ × E[Rᵢ]

where:
  wᵢ = weight of asset i
  E[Rᵢ] = expected return of asset i
```

### Portfolio Risk
```
σp² = Σ Σ wᵢ × wⱼ × Cov(i,j)
```

## References

- Markowitz, H. (1952). "Portfolio Selection", The Journal of Finance
- CVXPY Documentation: https://www.cvxpy.org/
- Efficient Frontier Theory: https://www.investopedia.com/terms/e/efficientfrontier.asp

## Author

**Aditya2814**

## License

This project is open source and available for educational purposes.

## Disclaimer

This analysis is for educational purposes only. Past performance does not guarantee future results. Please consult with a financial advisor before making investment decisions. The portfolio allocations suggested here should not be considered as financial advice.

---

**Last Updated**: 2026  
**Data Period**: 3 months (November 2023 - February 2024)
