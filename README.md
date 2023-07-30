# How much does it cost to survive?
## Exploring the prices of a basic food basket in Germany, Colombia and Peru
#### Project for Data Harvesting course for M. Computational Social Science at UC3M
- Authors: Jasmin Huynh, Carolina Cornejo, Juan D Mendez

## Project Description
- The average price index of the U.N. food agency reached an all-time high last year due to a significant increase in the cost of most food commodities. This surge was prompted by concerns of shortages caused by the disruption brought about by Russia's invasion of Ukraine. The Food and Agriculture Organization (FAO) reported that its food price index, which monitors the international prices of the most commonly traded food commodities, reached an average of 143.7 points in 2022. This figure represents a 14.3% increase from 2021 and is the highest recorded since 1990, according to the agency's records [(Reuters 2023)](https://www.reuters.com/markets/world-food-prices-hit-record-high-2022-despite-december-fall-2023-01-06/#:~:text=The%20Food%20and%20Agriculture%20Organization's,the%20agency%20said%20on%20Friday.).

- The project aim is to compare the prices of basic food products of different countries. We selected Germany, Colombia and Peru as these are our home countries. Furthermore, we want to examine the approximate percentage that a citizen spends for basic necessities in these countries compared to the minimum wage. For each country we use one online shop of a supermarket to scrape product prices from.

- Finding all the product prices from the three countries can be time-consuming, that's why a automated scraper -or three, one per country, can come in handy.
1. First the developed scraper creates URLs for the search sites that would be created when using the search bar of the online-shop to search for a specific product. For a list of 23 products 23 URLs are created for each country.
2. Then the results and corresponding product information (product names, prices and prices per kg/l) are extracted for each product using the URLs and XPath. The results are filtered and only the cheapest result is kept. In the end we get a table of 23 basic products and their corresponding prices for each country. For the webshop of the colombian supermarket RSelenium was required.
3. The total cost of a shopping cart of these products are calculated for each country. Then a dataframe is created containing the total sums and living wages of each country. 
4. Lastly we plot the results using ggplot.


## Requirements

The following R-packages are needed:

```
- xml2
- magrittr
- lubridate
- tidyverse
- httr
- rvest
- readr
- XML
- ggplot2
- RSelenium 
```

For RSelenium there were additional requirements to get it to work on Windows:
- we followed this [manual](https://cimentadaj.github.io/blog/2018-05-25-installing-rjava-on-windows-10/installing-rjava-on-windows-10/)
- Chrome Browser (updated)

- --> Still RSelenium still didn't work and the final solution was the following:
- deleting the license files in the binman directory of the chromedriver directories  (`C:\Users\name\AppData\Local\binman\binman_chromedriver\win32\111.0.5563.41`)
- there may be several chromedriver directories --> please delete the license files in each of them

- If that doesn't work, changing the 'chromver' (line 283 in the .Rmd) version according to installed chrome drivers version or browser driver version could help.

- To reproduce the scraper just run the R-chunks in the .Rmd.

> The rendered HTML file, showing the process, results and code, is also available.
