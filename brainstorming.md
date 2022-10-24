# An Example Scenario

A tool-writer builds a tool for users to more easily model their financial sitution to follow the Prioritizing Investments bogleheads wiki: https://bogle.tools/saving

They publish their source code: https://github.com/rrelyea/bogle.tools-saving

Initially, they hard code many of the tax constants:

- IRA Allowed Contribution of $6,000 and catch-up amount of $1,000: https://github.com/rrelyea/bogle.tools-saving/blob/main/src/Shared/IRA.cs#L15

However, each year this will need to be updated.

## How it could work

The tool-writer defines a set of constants they need.

- 2023/USA/IRS/IRA/ContributionLimit
- 2023/USA/IRS/401k/ContributionLimit
- 2023/USA/IRS/401k/CatchUpContribtionLimit
- 2023/USA/IRS/TaxBrackets/Single
- 2023/USA/IRS/TaxBrackets/MarriedFilingJointly


### Naming of Values

Names of values would include a set of scopes seperated by '/'.

### Results for simple values

`2023/USA/IRS/401k/ContributionLimit` would return a simple value: `$6,500`

### Results for complex values

`2023/USA/IRS/TaxBrackets/Single` would return a complex value:
```
35% for incomes over $231,250
32% for incomes over $182,100
24% for incomes over $95,375
22% for incomes over $44,725
12% for incomes over $11,000
```

### Results for multiple values

Tool-writers would often have a list of specific values they need, or a list of scopes that they wanted all values for.

#### Request for multiple values:
- 2023/USA/IRS/IRA/ContributionLimit
- 2023/USA/IRS/401k/ContributionLimit
- 2023/USA/IRS/401k/CatchUpContribtionLimit
- 2023/USA/IRS/TaxBrackets/Single
- 2023/USA/IRS/TaxBrackets/MarriedFilingJointly

#### Request for multiple scopes:
- 2023/USA/IRS/IRA
- 2023/USA/IRS/401k
- 2023/USA/IRS/TaxBrackets

### Tool-writers would update their values

#### Updating at Runtime:

Their code, on startup, would fetch relevant financial-figures and use them.

```
   onStartup() {
     ...
     program.financialFigures = fetchFinancialFigures();
     ...
   }

   fetchFinancialFigures() {
     var url = "https://<someUrl>/getFigures?q=2023_USA_IRS_IRA,2023_USA_IRS_401k&format=json"
     var json = fetch(url);
     return dataFromJson(json);
   }
```

#### Updating at Compile Time:

Periodidically, a data file or code file with the values embedded would be fetched.

```
    cd src\data\
    curl https://<someUrl>/getFigures?q=2023_USA_IRS_IRA,2023_USA_IRS_401k&format=json > financialFigures.json
    git add financialFigures.json
    git commit -m "updated financial figures on 1/24/2023"
    git push
```
### Github would have files for download, or webserver would have API to get content

Content could be retrieved as:
- JSON
- CSV
- Programming class with constants
- other?

Scenarios: 
- data for website (as data file or part of app)
- data for Single Page App website (located as part of compiled app)
- data for a spreadsheet (easy way to import a page with constants - perhaps CSV? - investigate)

### Some example value results (format independent)
- 2023/USA/IRS/IRA/ContributionLimit: $6,500
- 2023/USA/IRS/401k/ContributionLimit: $22,500
- 2023/USA/IRS/401k/CatchUpContribtionLimit: $7,500
- 2023/USA/IRS/TaxBrackets/Single: 
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
