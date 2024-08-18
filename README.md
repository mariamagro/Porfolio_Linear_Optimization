# Portfolio Optimization Project

## Author: María Ángeles Magro Garrote

### Overview

This project is focused on portfolio optimization, a critical task in finance where the goal is to allocate resources among different companies to maximize the overall return while adhering to specific constraints such as budget limits and sector-specific investment guidelines.

### A) Problem Formulation

#### 1. Model Sets
- **model.i**: Represents the set of companies in the portfolio. Each company is identified by an index "i".

#### 2. Parameters
- **model.r**: Expected return for each company, calculated as the mean return from previous months' stock data.
- **model.var**: Variances of companies' returns based on previous stock prices.
- **model.sector**: The sector each company belongs to.
- **model.budget**: Total budget available for investment.
- **model.max_asset**: Maximum percentage of the budget that can be invested in a single asset.
- **model.max_sector**: Maximum percentage of the budget that can be invested in a single sector.
- **model.max_var**: Maximum variance allowed, expressed as a percentage of the highest variance in the dataset.

#### 3. Decision Variable
- **model.x**: Represents the amount of money invested in each asset.

#### 4. Objective Function
The objective function maximizes the total expected return, which is the sum of the expected returns weighted by the proportion of the budget invested in each asset.

#### 5. Constraints
1. **Total Budget Lower Bound**: Ensures at least 50% of the budget is invested.
2. **Total Budget Upper Bound**: Ensures that the total investment does not exceed the budget.
3. **Non-Negative Weights**: Ensures no negative investments.
4. **Maximum Asset Weight**: Limits the percentage of the budget that can be invested in a single company.
5. **Sector Investment Constraint**: Limits the percentage of the budget that can be invested in any single sector.
6. **Maximum Variance Constraint**: Limits the variance of the companies selected.

### B) Data Creation

The stock prices and sectors of the companies are generated randomly. The data is then used to calculate expected returns and variances, and to assign sectors to companies.

#### Libraries Used
- `random`: For data generation.
- `pyomo.environ`: For model creation and solving.
- `numpy`, `matplotlib`, `seaborn`: For calculations and visualization.

### C) Implementation in Pyomo

The model is implemented using Pyomo with the following key components:

#### Model Parameters
- **model.i, model.r, model.var, model.sector, model.budget, model.max_asset, model.max_sector, model.max_var**: As defined earlier.

#### Decision Variable
- **model.x**: Non-negative investment weights.

#### Objective Function
The objective function maximizes the expected return based on the decision variable.

#### Constraints
Includes budget constraints, non-negativity constraints, asset weight constraints, sector constraints, and variance constraints.

#### Solver
The GLPK solver is used to solve the optimization problem.

### D) Constraints Sensitivities and Dual Values

The dual values of the constraints are analyzed to understand the marginal effects on the objective function. This analysis helps in understanding how changes in constraints impact the investment decisions.

### E) New Model Adjustments for a binary model

Incorporation of new parameters and constraints:
- **model.cost**: Cost of investing in each company.
- **model.dividends**: Binary parameter indicating if a company gives out dividends.
- **model.sentiment**: Binary parameter indicating recent news sentiment.
- **model.max_assets**: Maximum number of assets that can be selected.
- **model.min_assets**: Minimum number of assets that must be selected.

#### New Decision Variables
- **model.y**: Binary variable indicating if an asset is selected for investment.

#### New Objective Function
The objective now also accounts for the fixed costs associated with selecting assets.

#### Additional Constraints
- **Binary Selection**: Ensures correct assignment of binary variables.
- **Minimum Number of Assets**: Ensures a minimum number of assets are selected.

### Conclusion

This project provides a comprehensive approach to portfolio optimization, integrating various financial constraints and allowing for flexibility in investment strategy. The code is implemented in Python using Pyomo, making it adaptable and extendable for different scenarios.
