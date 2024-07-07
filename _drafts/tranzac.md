---
layout: post
title: Culture catalog
permalink: /culture-catalog-1/
---

# Culture catalog

As a kid my understanding of information about the world involved an idea of perfect knowledge, where everything was accessible if only I could find it and learn it. It always seemed to me as though there was a body somewhere that had everything one might be curious about meticulously labeled and preserved, just waiting for me to dig up in the library, city hall, ??? "Them," "scientists," "the government," well, it turns out that's kind of the case but usually we are out here on our own. Anyone working in this field has felt like my kingdom for a good, reliable, clean, accurate dataset. Our tools are set up for us to wrangle and crunch through those cleanly columns at blinding speed, but it is the before and after work that really takes time.

We lose so much information from the public sphere in the internet age. I do not have a sense of the magnitude of the issue empirically, but the technologies and relationships involved have made this inescapable. Articles, announcements, and advertisements are key means of communication that inaugurated modernity (not to mention prized sources for historians). Until recently, those were mainly printed on paper and handed out as newspapers, magazines, posters, and pamphlets. At their most ephemeral, they would be disseminated on the CRTC-regulated radio or TV channels, all by big-budget media organizations. The internet has now devolved that media- and message-making activity to a far greater number of people whose publication practices and technologies can be much more easily picked up and put down, forgotten about, left out of date, deleted, and crashed. A printing press back in the day was a pretty mean and serious investment. If my small newspaper made it into a hundred peoples' hands per issue, it only takes one of them to save and preserve it, put it in a box and forget about it, even drop it behind a couch and the content will survive. An expired credit card or forgotten password can lead to a downed site, with the content existing then only on some hobbyist or workers' hard drive. Printed materials last much longer than digitally saved data. 

There is a surprisingly ephemeral nature to the cultural milieu we exist in. I was going to say frighteningly ephemeral, but I do not know for sure if it is a bad thing. In our history so much of our culture and communication was oral and therefore really a one-time-only experience. I clutch my chest at the thought of my photos from the past decade being irretrievable, but should I mourn something that would have been anyways unavailable to almost all people ever? Regardless of the value judgement, it is true that the communications in which we are submerged via our phones and computers is paradoxically more voluminous and far more fragile than the same stuff of past decades and centuries. Articles that describe; essays that analyze; advertisements that announce; where we once had an object, a newspaper, a poster, we now have some data stored somewhere.

I built a database to catalogue some of that culture. The Tranzac is great, I go to see music there often. They publish their listings on their website in a calendar, and after some period of time the listings go away. As I write this in July 2024, the earliest posting on the website is from April 2023; the existence of the venue predates the internet by decades.

The project in its current form scrapes all the available performance data from the website using a bash script, then normalizes the data and stores it in a sqlite table. The data is not yet clean enough to do meaningful analyses using the artist names or the event descriptions, and the database will be most useful when I build the feature to do a daily check and update with any new or changed events from the site. As it is right now though, there is a normalized dataset that at least tells us what events took place on what day at what time at the Tranzac, which will not go away or change with time as the website has in the past.

## Approach
The bash script uses `curl` to fetch the source for all the months I manually verified currently have event data.

In Python, for each month, the script uses a `grep` search to locate the JSON event data in the website source. Looping through the resulting dictionary, the script then parses each event into the columns I describe below and commits them to the database.

The HTML source data has some stray apostrophes that jam up the SQLite insert statements since they act as rogue single quotes; I had to fix that with the Python String.replace() function to escape them. When events had nothing for certain fields, like location, the code would throw a `KeyError` exception and so for the time being I have replaced that very gracefully with the `NULL_REMARKABLE_PLACEHOLDER` value, a future to-do for sure. The degree of robustness to which I have built up the database insertion code is good enough to at least parse and commit all the current data into the database without hitting an exception and crashing. I assume that there will be new curveballs in the future once I get it set up to be checking for new data every day.

The database schema is a simple two tables: artist contains the artist name, and show contains the date, time, description, venue, image_url, and event_url. There is not much to remark on here, looking forward though there are a few things I want to implement:
- use the event_url to retrieve and store the full description data for each show (they all end in [...] as it stands)
- use the image_url to similarly store the actual photos themselves
- I need some way to tell whether an event was present in the database before the current day's scraping, or whether it is new. Has a future event been changed removed? Is that still significant in the same way as an event that was scheduled _and happened_?
- If I expand this beyond the Tranzac itself, then a separate normalized location table will be necessary.

![the entity-relationship diagram describing the database schema](/assets/2024-07-07-entity-relationship-diagram.png)

![Ruth Garbus](/assets/2024-07-07-ruth-garbus.png)
![Bernice](/assets/2024-07-07-bernice.png)
![Sun Milk](/assets/2024-07-07-sun-milk.png)
![Drones over Dufferin](/assets/2024-07-07-drones-over-dufferin.png)
