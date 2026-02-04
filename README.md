# AGH Project: Quantitative Market Risk Measures Project (2025/2026)

This repository contains the final project for the **Quantitative Market Risk Measures** course at AGH University of Science and Technology. The project focuses on analyzing market risk for the **WIG20** index using historical simulation methods.

## Project Overview

The main objective of this project is to estimate and validate risk measures (**Value at Risk (VaR)** and **Expected Shortfall (ES)**) at a 99% confidence level. The analysis is based on daily logarithmic returns of the WIG20 index over an 8-year period.

### Key Features
- **Data Analysis:** Statistical description of WIG20 daily returns (2016–2024).
- **Normality Testing:** Verification of the normal distribution assumption using Jarque-Bera, Shapiro-Wilk, and Anderson-Darling tests.
- **Risk Estimation:** Calculation of 99% VaR and 99% ES using a **500-day moving window**.
  - **Method 1:** Simple Historical Simulation.
  - **Method 2:** Weighted Historical Simulation (Exponentially Weighted, lambda=0.99).
- **Backtesting:** Validation of the models over the last **250 trading days**:
  - **Traffic Light Test** (Basel Committee standards).
  - **Kupiec Test** (Unconditional Coverage).
  - **Christoffersen Test** (Conditional Coverage).

## Repository Structure

- `Projekt-zaliczeniowy-Ilościowe-miary-ryzyka-rynkowego` - Main project report (RMarkdown/HTML) containing code, analysis, and visualizations.
- `wig20_d.csv` - Raw dataset containing daily WIG20 quotations (Open, High, Low, Close, Volume).
- `README.md` - Project documentation.

## Methodology and Results Summary

### 1. Statistical Analysis
The analysis confirmed that WIG20 returns do not follow a normal distribution (presence of "fat tails" and high kurtosis). This justified the use of **Historical Simulation** methods over parametric ones.

### 2. Models Implemented
- **Simple Historical Method:** Treats all past 500 observations equally.
- **Weighted Historical Method:** Assigns exponentially decaying weights to past observations to react faster to recent market volatility.

### 3. Backtesting Results (Last 250 Days)
The models were validated by counting the number of exceptions (days where actual loss exceeded VaR).

| Method | Exceptions (N=250) | Traffic Light Zone | Conclusion |
| :--- | :---: | :---: | :--- |
| **Simple Historical** | **4** (1.6%) | **Green** | **Reliable**. The model correctly estimated the risk within the expected range. |
| **Weighted Historical** | **6** (2.4%) | **Yellow** | **Underestimated**. The model was too optimistic during calm periods and reacted too late to sudden shocks. |

## Technologies Used

- **Language:** R
- **Key Libraries:**
  - `tidyverse` (Data manipulation and visualization)
  - `moments` (Skewness and Kurtosis)
  - `tseries`, `nortest` (Statistical tests)
  - `rugarch` (VaR testing tools)
  - `knitr`, `gridExtra` (Reporting)

