---
layout: post
title: "Household after-tax income distribution in Canada"
permalink: /after-tax-national-income/
---

At the national level, what is Canada's income distribution using after-tax income figures?

In 2020, there were 14,978,945 households in Canada<sup>1</sup>. The median after-tax income of households was $73,000.

| household income     | number of households | percentage | rolling sum | rolling percentage |
| -------------------- | -------------------- | ---------- | ----------- | ------------------ |
| Under $5,000         | 186,735              | 1.2%       | 186,735     | 1.2%               |
| $5,000 to $9,999     | 95,195               | 0.6%       | 281,930     | 1.9%               |
| $10,000 to $14,999   | 183,430              | 1.2%       | 465,360     | 3.1%               |
| $15,000 to $19,999   | 289,545              | 1.9%       | 754,905     | 5.0%               |
| $20,000 to $24,999   | 681,895              | 4.6%       | 1,436,800   | 9.6%               |
| $25,000 to $29,999   | 589,110              | 3.9%       | 2,025,910   | 13.5%              |
| $30,000 to $34,999   | 582,280              | 3.9%       | 2,608,190   | 17.4%              |
| $35,000 to $39,999   | 666,670              | 4.5%       | 3,274,860   | 21.9%              |
| $40,000 to $44,999   | 676,990              | 4.5%       | 3,951,850   | 26.4%              |
| $45,000 to $49,999   | 655,100              | 4.4%       | 4,606,950   | 30.8%              |
| $50,000 to $59,999   | 1,285,425            | 8.6%       | 5,892,375   | 39.3%              |
| $60,000 to $69,999   | 1,223,835            | 8.2%       | 7,116,210   | 47.5%              |
| $70,000 to $79,999   | 1,137,845            | 7.6%       | 8,254,055   | 55.1%              |
| $80,000 to $89,999   | 1,039,375            | 6.9%       | 9,293,430   | 62.0%              |
| $90,000 to $99,999   | 911,515              | 6.1%       | 10,204,945  | 68.1%              |
| $100,000 to $124,999 | 1,757,040            | 11.7%      | 11,961,985  | 79.9%              |
| $125,000 to $149,999 | 1,152,860            | 7.7%       | 13,114,845  | 87.6%              |
| $150,000 to $199,999 | 1,139,770            | 7.6%       | 14,254,615  | 95.2%              |
| $200,000 and over    | 724,330              | 4.8%       | 14,978,945  | 100.0%             |

This table reflects "after-tax income," a household's total income minus income tax. See Statistics Canada for [more](https://www12.statcan.gc.ca/census-recensement/2021/ref/dict/az/Definition-eng.cfm?ID=pop004).

## How do we know?
The data comes from the 2021 Canadian census, [Table 98-10-0056-01](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=9810005601).
- Default download settings
- Download options > CSV Download selected data (for database loading)
- download link [here](https://www150.statcan.gc.ca/t1/tbl1/en/dtl!downloadDbLoadingData-nonTraduit.action?pid=9810005601&latestN=0&startDate=20210101&endDate=20210101&csvLocale=en&selectedMembers=%5B%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%2C2%2C3%2C4%2C5%2C6%2C7%2C8%2C9%2C10%2C11%2C12%2C13%2C14%2C15%2C16%2C17%2C18%2C19%2C20%2C21%2C22%5D%2C%5B1%2C2%5D%5D&checkedLevels=)

`#! /bin/bash`

`file_name=country_after_tax_income.csv`

`if [ ! -f $file_name ];`  
`then`  
`        curl -o $file_name -kL "https://www150.statcan.gc.ca/t1/tbl1/en/dtl!downloadDbLoadingData-nonTraduit.action?pid=9810005601&latestN=0&startDate=20210101&endDate=20210101&csvLocale=en&selectedMembers=%5B%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%2C2%2C3%2C4%2C5%2C6%2C7%2C8%2C9%2C10%2C11%2C12%2C13%2C14%2C15%2C16%2C17%2C18%2C19%2C20%2C21%2C22%5D%2C%5B1%2C2%5D%5D&checkedLevels="`  
`fi`

`xsv select 8,9,16 $file_name | xsv search --select 2 2020 | xsv select 1,3 | csvlook -I | trim`

| Household after-tax income groups (22)   | VALUE    |
| ---------------------------------------- | -------- |
| Total - After-tax income of household    | 14978940 |
| Under $5,000                             | 186735   |
| $5,000 to $9,999                         | 95195    |
| $10,000 to $14,999                       | 183430   |
| $15,000 to $19,999                       | 289545   |
| $20,000 to $24,999                       | 681895   |
| $25,000 to $29,999                       | 589110   |
| $30,000 to $34,999                       | 582280   |  

… with 14 more lines

`xsv select 8,9,16 $file_name |`  
`xsv search --select 2 2020 |`  
`xsv select 1,3 |`  
`LC_ALL=en_US.UTF-8 awk -v FS='",' -v OFS='|' '{`  
`if(NR == 18) next`  
`if(NR ==1) print "","household income", "number of households","percentage","rolling sum", "rolling percentage","\n|---|---|---|---|---|"`  
`if(NR == 2 || NR == 23) next`  
`if(NR > 2 && NR < 23) sum+=$2`  
`if(NR > 2 && NR < 23) printf "|%s|%\047d|%.1f%|%\047d|%.1f%|\n",substr($1,2),$2,$2/14978945*100"%",sum,sum/14978945*100"%"`  
`}'`

<sup>1</sup> The number is off by five compared to the total income dataset (see [here]({% post_url 2023-06-26-canada-income %})). I took the sum of all the values, excluding the $100,000 and over category, and it turns out that number is also off by a few households. I am not sure what explains that discrepancy, minor as it is.
