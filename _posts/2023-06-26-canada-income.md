---
layout: post
title: "Household income distribution in Canada"
permalink: /national-income-distribution/
---

At the national level, what is Canada's income distribution?


In 2021, there were 14,978,950 households in Canada. The median income of households was $84,000.


| household income     | number of households | percentage | rolling sum | rolling percentage |
|----------------------|----------------------|------------|-------------|--------------------|
| Under $5,000         | 165,180              | 1.1%       | 165,180     | 1.1%               |
| $5,000 to $9,999     | 91,750               | 0.6%       | 256,930     | 1.7%               |
| $10,000 to $14,999   | 178,475              | 1.2%       | 435,405     | 2.9%               |
| $15,000 to $19,999   | 274,145              | 1.8%       | 709,550     | 4.7%               |
| $20,000 to $24,999   | 637,695              | 4.3%       | 1,347,245   | 9.0%               |
| $25,000 to $29,999   | 505,875              | 3.4%       | 1,853,120   | 12.4%              |
| $30,000 to $34,999   | 488,735              | 3.3%       | 2,341,855   | 15.6%              |
| $35,000 to $39,999   | 560,950              | 3.7%       | 2,902,805   | 19.4%              |
| $40,000 to $44,999   | 572,650              | 3.8%       | 3,475,455   | 23.2%              |
| $45,000 to $49,999   | 559,150              | 3.7%       | 4,034,605   | 26.9%              |
| $50,000 to $59,999   | 1,093,190            | 7.3%       | 5,127,795   | 34.2%              |
| $60,000 to $69,999   | 1,044,715            | 7.0%       | 6,172,510   | 41.2%              |
| $70,000 to $79,999   | 986,460              | 6.6%       | 7,158,970   | 47.8%              |
| $80,000 to $89,999   | 921,205              | 6.1%       | 8,080,175   | 53.9%              |
| $90,000 to $99,999   | 844,835              | 5.6%       | 8,925,010   | 59.6%              |
| $100,000 to $124,999 | 1,753,480            | 11.7%      | 10,678,490  | 71.3%              |
| $125,000 to $149,999 | 1,283,445            | 8.6%       | 11,961,935  | 79.9%              |
| $150,000 to $199,999 | 1,545,940            | 10.3%      | 13,507,875  | 90.2%              |
| $200,000 and over    | 1,471,075            | 9.8%       | 14,978,950  | 100.0%             |

## How do we know?
The data comes from the 2021 Canadian census, [Table 98-10-0055-01](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=9810005501).
- Default download settings
- Download options > CSV Download selected data (for database loading)
- download link [here](https://www150.statcan.gc.ca/t1/tbl1/en/dtl!downloadDbLoadingData-nonTraduit.action?pid=9810005501&latestN=0&startDate=20210101&endDate=20210101&csvLocale=en&selectedMembers=%5B%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B%5D%2C%5B%5D%5D&checkedLevels=5D1%2C5D2%2C5D3%2C6D1)

`#! /bin/bash`

`country_total_income_file="ctry_tot_income.csv"`

`if [ ! -f "$country_total_income_file" ]; then`  
        `curl -o 9810005501_databaseLoadingData.csv -kL "https://www150.statcan.gc.ca/t1/tbl1/en/dtl!downloadDbLoadingData-nonTraduit.action?pid=9810005501&latestN=0&startDate=20210101&endDate=20210101&csvLocale=en&selectedMembers=%5B%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B1%5D%2C%5B%5D%2C%5B%5D%5D&checkedLevels=5D1%2C5D2%2C5D3%2C6D1"`  
       `mv 9810005501_databaseLoadingData.csv $country_total_income_file`  
`fi`

`# Note that all records have reference date 2021, GEO=Canada, DGUID for Canada identical across all records.`  
`xsv select 8,9,16 $country_total_income_file | xsv search --select 2 2020 | xsv select 1,3 | header -r income_bin,number_of_households | csvlook`

| income_bin                           | number_of_households |
| ------------------------------------ | -------------------- |
| Total - Total income of households   |           14,978,940 |
| Under $5,000                         |              165,180 |
| $5,000 to $9,999                     |               91,750 |
| $10,000 to $14,999                   |              178,475 |
| $15,000 to $19,999                   |              274,145 |
| $20,000 to $24,999                   |              637,695 |
| $25,000 to $29,999                   |              505,875 |
| $30,000 to $34,999                   |              488,735 |
| $35,000 to $39,999                   |              560,950 |
| $40,000 to $44,999                   |              572,650 |
| $45,000 to $49,999                   |              559,150 |
| $50,000 to $59,999                   |            1,093,190 |
| $60,000 to $69,999                   |            1,044,715 |
| $70,000 to $79,999                   |              986,460 |
| $80,000 to $89,999                   |              921,205 |
| $90,000 to $99,999                   |              844,835 |
| $100,000 and over                    |            6,053,945 |
| $100,000 to $124,999                 |            1,753,480 |
| $125,000 to $149,999                 |            1,283,445 |
| $150,000 to $199,999                 |            1,545,940 |
| $200,000 and over                    |            1,471,075 |
| Median total income of household ($) |               84,000 |

`xsv select 8,9,16 $country_total_income_file | xsv search --select 2 2020 | xsv select 1,3 | header -r income_bin,number_of_households > result.csv`
