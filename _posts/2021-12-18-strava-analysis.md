---
layout: post
permalink: /strava-analysis-1/
title:  "Analyzing Strava data in R (part 1)"
date: 2021-12-18 -0400
---
When COVID hit I was living in Montreal. Those early months stick out in my mind as a particularly moody time and I'm grateful we're past that, though obviously the pandemic is still with us (for [real](https://www.nbcnews.com/news/world/omicron-linked-global-vaccine-inequality-experts-rcna6916)).

![a bright daytime photo of a path on Mount Royal covered in snow with a blue sky](/assets/21-12-18-outremont-lookout-winter.png)
_Near the Outremont lookout on the mountain in Montreal, February 2021_

I found myself running more than I ever had before. I suppose this isn't really the place to get into it, but remembering those paths and some of the days I went up on the mountain or through the different neighbourhoods around my apartment, Outremont, Mile End, Rosemont if I went hard, the memories really bring something up for me now, like finding a letter from an old friend.

These days I get a serious amount of exercise every day for my job and so I'm not really running anymore, but I have fourteen months worth of my runs logged in Strava and I want to dig in to see what patterns come up.

Before I even download the data, here are some questions I'd like to answer:
- When did I start running after COVID hit in Montreal? When did I stop?
- How far did I run?
- How far did I run on average per run? Per week? Per month?
- What does the distribution of my per-run distance look like?
- On which days of the week did I run most frequently? Least frequently?
- I could likely do a lot of these over for elevation, though that depends on the dataset
- What did the temporal distribution of my running look like?

# Downloading the data
For anyone who uses Strava, it's pretty easy to download your account data. I logged in on Strava's website, hit Settings > My Account > Download or Delete Your Account, and clicked "Request Your Archive." That sends you an email with a download link. They say it could take several hours, but I got the link for mine in about two minutes.

Whoa, okay. I haven't done this before, this is super rich. I was expecting a .csv with like, date, distance, elevation probably. That's all there, but there's also like, _everything_. A bunch of stuff I've never used (like who registers their "components" on Strava), but there's every comment I've ever written in the app, a spreadsheet of every like I received, you name it. About forty .csv files all told.

Even better, there's an "activities" folder that's got a .gpx file associated with every run I did. I know with these things I need to take it in small steps but I have to be honest, the GIS rat in me definitely lit up seeing that folder. I'm looking forward to seeing what I can cook up.
