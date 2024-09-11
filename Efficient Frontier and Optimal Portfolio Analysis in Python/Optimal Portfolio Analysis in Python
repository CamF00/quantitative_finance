"""
Introduction:
This project focuses on Optimal Portfolio Analysis using Python. The goal is to analyze different combinations of financial assets 
to identify the optimal portfolio that maximizes returns for a given level of risk or minimizes risk for a given level of return. 
The analysis incorporates risk-free lending and borrowing as well as the potential for short sales.

Analysis Overview:
The Python code performs the following tasks:

1. Optimal Portfolio Calculation.

  - Computed the weights of the optimal risky portfolios (market portfolios) for two combinations. 
      -> Combination 1: S&P Index and US Long-Term Bonds.
      -> Combination 2: S&P Index and Emerging Market Equity Index. 
  
  - Using these weights, I calculated the expected return and standard devision (risk) of each optimal portfolio.

  - Then I calculated the Sharpe Ratio for each optimal porfolio. 

Formulas Used:

1. Expected Return of a Portfolio:
For a portfolio consisting of two assets (A and B), the expected return R_P is given by:
R_P = w_A * R_A + w_B * R_B
where:
- w_A and w_B are the weights of assets A and B in the portfolio.
- R_A and R_B are the expected returns of assets A and B, respectively.

2. Standard Deviation of a Portfolio:
The standard deviation (risk) σ_P of a two-asset portfolio is calculated as:
σ_P = sqrt(w_A^2 * σ_A^2 + w_B^2 * σ_B^2 + 2 * w_A * w_B * σ_A * σ_B * ρ_{A,B})
where:
- σ_A and σ_B are the standard deviations of assets A and B.
- ρ_{A,B} is the correlation coefficient between the returns of assets A and B.

3. Sharpe Ratio:
The Sharpe Ratio measures the risk-adjusted return of a portfolio and is defined as:
Sharpe Ratio = (R_M - R_f) / σ_M
where:
- R_M is the expected return of the market portfolio.
- R_f is the risk-free rate.
- σ_M is the standard deviation of the market portfolio.
"""

import numpy as np

# Given data
R_sp = 15  # Expected return of S&P Index (%)
R_bond = 9  # Expected return of US Long-Term Bonds (%)
R_ef = 21  # Expected return of Emerging Market Equity Index (EF) (%)
Rf = 5  # Risk-free rate (%)

sigma_sp = 20  # Standard deviation of S&P Index (%)
sigma_bond = 12  # Standard deviation of US Long-Term Bonds (%)
sigma_ef = 25  # Standard deviation of Emerging Market Equity Index (EF) (%)

rho_sp_bond = 0.3  # Correlation between S&P Index and US Long-Term Bonds
rho_sp_ef = 0.2  # Correlation between S&P Index and Emerging Market Equity Index

# Calculate the weights of the optimal risky portfolios using the formulas:
# Weight of S&P in optimal portfolio for each combination

# Combination 1: S&P Index and US Long-Term Bonds
cov_sp_bond = rho_sp_bond * sigma_sp * sigma_bond
w_sp_bond = ((R_sp - Rf) * (sigma_bond ** 2) - (R_bond - Rf) * cov_sp_bond) / ((R_sp - Rf) * (sigma_bond ** 2) + (R_bond - Rf) * (sigma_sp ** 2) - (R_sp - Rf + R_bond - Rf) * cov_sp_bond)

# Combination 2: S&P Index and Emerging Market Equity Index (EF)
cov_sp_ef = rho_sp_ef * sigma_sp * sigma_ef
w_sp_ef = ((R_sp - Rf) * (sigma_ef ** 2) - (R_ef - Rf) * cov_sp_ef) / ((R_sp - Rf) * (sigma_ef ** 2) + (R_ef - Rf) * (sigma_sp ** 2) - (R_sp - Rf + R_ef - Rf) * cov_sp_ef)

# Calculate the expected returns and standard deviations of the optimal risky portfolios
# Combination 1: S&P Index and US Long-Term Bonds
R_m1 = w_sp_bond * R_sp + (1 - w_sp_bond) * R_bond
sigma_m1 = np.sqrt(w_sp_bond**2 * sigma_sp**2 + (1 - w_sp_bond)**2 * sigma_bond**2 + 2 * w_sp_bond * (1 - w_sp_bond) * cov_sp_bond)

# Combination 2: S&P Index and Emerging Market Equity Index (EF)
R_m2 = w_sp_ef * R_sp + (1 - w_sp_ef) * R_ef
sigma_m2 = np.sqrt(w_sp_ef**2 * sigma_sp**2 + (1 - w_sp_ef)**2 * sigma_ef**2 + 2 * w_sp_ef * (1 - w_sp_ef) * cov_sp_ef)

# Calculate the Sharpe Ratios for each combination
sharpe_ratio_m1 = (R_m1 - Rf) / sigma_m1
sharpe_ratio_m2 = (R_m2 - Rf) / sigma_m2

(R_m1, sigma_m1, sharpe_ratio_m1), (R_m2, sigma_m2, sharpe_ratio_m2)
