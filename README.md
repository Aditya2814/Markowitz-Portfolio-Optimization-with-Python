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
