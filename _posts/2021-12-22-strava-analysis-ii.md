---
layout: post
title:  "Analyzing Strava data in R (part 2)"
date: 2021-12-22 -0400
---
[<- part 1](/strava-analysis-1/)

### lab notes mood

Will there be a day that I write this up in an easy-to-digest way for the reader? Yes. Is today that day?

![bugs bunny no meme](/assets/21-12-22-bugs-bunny.jpg)

Love ya though if you're reading this <3 I used this [book](https://r4ds.had.co.nz/) to learn a lot of this stuff.

|Questions I want to answer|
|--------------------------|
|When did I start running after COVID hit in Montreal? When did I stop?|
|How far did I run?|
|How far did I run on average per run? Per week? Per month?|
|What does the distribution of my per-run distance look like?|
|On which days of the week did I run most frequently? Least frequently?|
|What did the temporal distribution of my running look like?|

# Setup
I started a new project in RStudio and started a git [repository](https://github.com/zripka/strava-analysis) I pushed to GitHub.

# The dataset
There are a _ton_ of variables in the activities.csv file, like 83 of them. I picked a few of them that seemed to make sense before diving into actually researching what they are (see the table below).

I couldn't find a definitive key to the activities dataset, and so I've been trying to sus out the precise meaning of each of these variables by looking through this [website](https://support.strava.com/hc/en-us/categories/202558427-Help-Support).

|Variable name|Description|
|-------------|-----------|
|Activity ID|A unique ID for each activity|
|Activity Date|The date (and start time, I think) of each activity|
|Activity Type|Run, bike, swim, and so on|
|Activity Description|I never used this, should drop this column|
|[Elapsed Time](https://support.strava.com/hc/en-us/articles/216917157-Strava-Training-Glossary-for-Running)|"Elapsed time measures the total elapsed time of the run, including stops and pauses"|
|[Distance](https://support.strava.com/hc/en-us/articles/216919487-How-Distance-is-Calculated)|So it seems like there are some complicated ways to think about this, but in my case it's likely just that this number is in metres or kilometres (or miles?) and Strava measures it by linking up disparate GPS points. Good enough!|
|Relative Effort|This is confusing and I don't think it's useful to me. I'm going to drop it, it seems like a highly constructed variable that's kinda specific to Strava|
|Commute|True/false value ie was this a commute?|
|Moving Time|It looks like moving time is auto-detected: if at any point my pace was less than 30 minutes per mile, the app dropped that segment of time|
|[Max Speed](https://support.strava.com/hc/en-us/articles/115001188684-Moving-Time-Speed-and-Pace-Calculations)|"the fastest speed recorded between any two GPS coordinates on your activity"|
|Average Speed|I don't have a source for this one but I guess it's distance over time|
|Elevation Gain|I'm not sure if my phone has an altimeter in it or not, either way I guess this is pretty self-explanatory. Did I run up or down and by how much?|
|Elevation Loss|ditto|
|Elevation Low|I'm guessing this is an absolute number? Maybe in metres above sea level|
|Elevation High|ditto|
|Number of Runs|this is a bit of a mystery. Anyway it's all blank, I can cut this one out|
|Uphill Time|ditto|
|Downhill Time|ditto|
|Other Time|ditto|
|Perceived Exertion|My own perceived exertion out of ten|
|Total Weight Lifted|all rows are blank|

Alright so I can definitely cut Activity Description, Relative Effort, Number of Runs, Uphill Time, Downhill Time, Other Time, and Total Weight Lifted.

Done. That brings me down from 83 to 22 down to 15.

Why is there multiple "elapsed time" and "distance" variables? Do I care about the "elevation low" and "elevation high" variables? ~~What does "Number of Runs" mean? What does "Other Time" mean? What's the difference between "Relative Effort" and "Perceived Exertion"?~~ Noting right now that I need to flag/remove/inspect the run from January 13th of 2021, the GPS points were totally screwy.

|Questions I came up with as I wrote this post|
|---------------------------------------------|
|How did my max and average speeds change over time?|

