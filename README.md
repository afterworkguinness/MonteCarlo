# MonteCarlo
A Monte Carlo engine to calculate credit VaR on the tranches of a CDO.

Some initial thoughts:

Inputs:
-------
- Correlation and probability of default assumtions
- Equity tranche hurdle rate (for discounting future cash flows)
- Details of collaterals (unerlying assets) 
- Details of tranches 
 
Outputs:
-------
- For each combination of probability of default and correlation, generate the average losses for each tranche
- Credit VaR for each tranche

Implementation Details:
----------------------
- Use R to generate correlated randon normal vectors
- Use Apache Spark to run the simulations across multiple machines 
