# An Example Scenario

A tool-writer builds a tool for users to more easily model their financial sitution to follow the Prioritizing Investments bogleheads wiki: https://bogle.tools/saving

They publish their source code: https://github.com/rrelyea/bogle.tools-saving

Initially, they hard code many of the tax constants:

- IRA Allowed Contribution of $6,000 and catch-up amount of $1,000: https://github.com/rrelyea/bogle.tools-saving/blob/main/src/Shared/IRA.cs#L15

However, each year this will need to be updated.

## How it could work

The tool-writer defines a set of constants they need.

- USA/IRS/IRA/ContributionLimit
- USA/IRS/401k/ContributionLimit
- USA/IRS/401k/CatchUpContribtionLimit
- USA/IRS/TaxBrackets/Single
- USA/IRS/TaxBrackets/MarriedFilingJointly

At runtime, or periodically, they would update the numbers their tool used by fetching those values (perhaps grabbing data from one or more files, perhaps calling an API):

- USA/IRS/IRA/ContributionLimit: $6,500 for TaxYear 2023
- USA/IRS/401k/ContributionLimit: $22,500 for TaxYear 2023
- USA/IRS/401k/CatchUpContribtionLimit: $7,500 for TaxYear 2023
- USA/IRS/TaxBrackets/Single: 
```
35% for incomes over $231,250
32% for incomes over $182,100
24% for incomes over $95,375
22% for incomes over $44,725
12% for incomes over $11,000
```
- USA/IRS/TaxBrackets/MarriedFilingJointly: 
```
35% for incomes over $462,500
32% for incomes over $364,200
24% for incomes over $190,750
22% for incomes over $89,450
12% for incomes over $22,000 
```

### Requirement: Naming of Values

Names of values would include a set of scopes.

### Requirement: Results for simple values

Results for simple values would include a value and a time range.

### Requirement: Results for complex values

Results for complex values would include more...such as a % tax rate over a certain dollar amount of income.

### Requirement: Fetching latest or specific years

I'd imagine there is a way you could lookup the latest values, as well as a specific years.
