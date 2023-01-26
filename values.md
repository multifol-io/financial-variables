## List of Proposed Values to Collect and Share

### IRS Tax Rates -- PUBLISHED

- Annual Exclusion for Gifts
- Standard Deduction
- Tax Rate Tables

See [data file: irs.tax-rates.2023.json](data/usa/irs/irs.tax-rates.2023.json)

### IRS IRMAA Rates -- PUBLISHED

- Base Amounts
- Adjustment Tables

See [data file: irs.irmaa-rates.2023.json](data/usa/irs/irs.irmaa-rates.2023.json)

### IRS Retirement -- PUBLISHED

- HSA
- IRA
- Roth IRA
- Employer 401K

See [data file: irs.retirement.2023.json](data/usa/irs/irs.retirement.2023.json)
See [data file: irs.retirement.2022.json](data/usa/irs/irs.retirement.2022.json)


### CPI-U - DO NOT BELIEVE ANYTHING IS NEEDED

BLS publishes a comprehensive amount of data here: https://www.bls.gov/cpi/tables/supplemental-files/home.htm

However, this is probably the best view: https://data.bls.gov/timeseries/CUUR0000SA0?years_option=all_years

(There is a link to an XLSX file there. The link has no simple URL, since it allows many configuration changes)

Also, seems like FRED API may make some CPI data available to developers: https://fred.stlouisfed.org/docs/api/fred/ (includes a tool that runs in GoogleSheets)

### Others Proposals to Investigate

- Vanguard/VT/USEquitiesPercentage


[bogleheads/cjg requested](https://www.bogleheads.org/forum/viewtopic.php?p=6929156#p6929156):
- metrics around market weights in my spreadsheet (how much SP500 vs Extended Market to get total stock, US vs Ex-US to get total world)

They later pointed to: https://www.bogleheads.org/wiki/Approximating_total_stock_market

Which appears to be an occasionally updated list...the core "morningstar style box" comes from https://www.morningstar.com/funds/xnas/vtsax/portfolio (choose stock style: weight)

Looking at Morningstar's APIs, you could automate grabbing the style box info from their [securities API](https://developer.morningstar.com/apis/investment-analysis/securities-us/overview) using `equityStyleBox` and related data points.

Users pay $20 per month to get morningstar membership. So it likely isn't ok to store and share that data. Probably not something for financial-figures github and related sites to do without permissions from morningstar.
