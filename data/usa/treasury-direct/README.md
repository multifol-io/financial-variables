Initial post about this process on financial variables at bogleheads.org: https://www.bogleheads.org/forum/viewtopic.php?p=7641269#p7641269

1. Twice a year (November 1st and May 1st) download [i-bond-rate-chart.pdf from treasurydirect.gov](https://www.treasurydirect.gov/files/savings-bonds/i-bond-rate-chart.pdf)
1. Convert to Excel via Adobe's online converter: https://www.adobe.com/acrobat/online/pdf-to-excel.html
1. Open in Excel, save as: i-bond-rate-chart.csv
1. Look at diff of CSV files...and ensure that the changes are minimal...to avoid formatting changes from breaking the CSV parsing that programs may do. (header and footer likely need tweaks)
1. Upload pdf, xlsx, and csv version of that file to https://github.com/bogle-tools/financial-variables/tree/main/data/usa/treasury-direct