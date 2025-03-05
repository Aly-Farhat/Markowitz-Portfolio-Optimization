# Markowitz-Portfolio-Optimization

## Overview
This project implements **Markowitz Modern Portfolio Theory** using the **Gurobi Optimizer** to construct an optimal portfolio by balancing risk and return. The project also computes and visualizes the **Efficient Frontier**, helping investors make informed decisions.

## Features
1) **Data Collection & Preprocessing**  
- Fetches historical stock data using **Yahoo Finance (`yfinance`)**.
- Computes **daily returns** and **covariance matrix** for risk analysis.

2) **Portfolio Optimization with Gurobi**  
- Formulates the **Markowitz Portfolio Optimization Problem** as a **Quadratic Programming (QP) model**.
- Implements constraints such as **fully invested portfolio, minimum return threshold, and risk control**.
- Uses **Gurobi solver** to find the optimal asset allocation.

3) **Efficient Frontier Computation & Visualization**  
- Computes multiple portfolios with varying **risk-return trade-offs**.
- Plots the **Efficient Frontier** to visualize the best-performing portfolios.

## Installation
To run this project, install the required dependencies:
```bash
pip install numpy pandas matplotlib gurobipy yfinance
```

**Ensure Gurobi is installed and activated.** For academic licenses, refer to the official [Gurobi website](https://www.gurobi.com/).

## Usage
### **Step 1: Fetch Stock Data**
Modify `tickers` in `Markowitz Portfolio Optimization.ipynb` to select stocks:
```python
 tickers = ["AAPL", "GOOGL", "AMZN", "NFLX", "TSLA"]
 stock_data = fetch_stock_data(tickers, "2020-01-01", "2024-11-10")
```

### **Step 2: Compute Portfolio Optimization**
```python
mean_returns, cov_matrix = compute_returns_and_cov(stock_data)
result = optimize_portfolio(mean_returns, cov_matrix, target_return=0.12)
print("Optimal Weights:", result["weights"])
```

### **Step 3: Compute & Plot Efficient Frontier**
```python
target_returns, port_risks, _ = compute_efficient_frontier(mean_returns, cov_matrix)
plot_efficient_frontier(target_returns, port_risks)
```

