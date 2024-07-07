---
layout: post
title: Check, pull, store
permalink: /check-pull-store/
---

A common gesture we need to perform is to check some resource against criteria, pull it, and store it for later. I made some boilerplate [code](https://github.com/zripka/check-pull-store) to fork for the next time I need to do this kind of thing, based on a placeholder weather API.

![Phoenix, Arizona](/assets/2024-07-07-weather.png)
A photo of some weather

## Approach

`curl "http://api.weatherapi.com/v1/current.json?key=$(cat .config)&q=toronto&aqi=no"`

Every time I run the script, the program checks if the data has changed since last time based on the `last_updated` field in the response. If so, the database stores it as a new row.

![a screenshot of python code](/assets/2024-07-07-python.png)

To get a consistent record of the weather in my city, the only next step required is to run it regularly, say every ten minutes as a cron job.

![a screenshot of a data table](/assets/2024-07-07-sql-result.png)

This is boilerplate code and not useful on its own; obviously the history of weather in Toronto is well-documented and easy to access. I can think of possible applications for future projects though, like tracking scraped web data over time or archiving web content before we [lose](https://www.fastcompany.com/90666430/parts-of-the-web-are-disappearing-every-day-heres-how-to-save-internet-history) it.
