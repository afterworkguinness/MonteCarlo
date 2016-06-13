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
- Use SparkR to generate simulation inputs and to run the simulations across multiple machines 
- 
Steps:
------

Generate 1,000 (rows) x100(Cols)  matrix of standard random normals

Each row is a simulation thread

Each col represents an instrument 

For each correlation assumption, transform the matrix into one with correlated values (of the same size)

For each combination of correlation and default probability assumptions, create a matrix of default times - -> produces sets of 1,000x 100 matrices.  Each run of 1,000 simulation threads uses one of these matrices

In each simulation :

Count off the defaults that occur in the life of the security (using the appropriate default time matrix)  and use that to calculate credit losses.

