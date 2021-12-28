---
layout: post
title: Analyzing Strava data in R (part 3)
permalink: /strava-analysis-3/
---
[<- part 2](/strava-analysis-2)

|Questions I want to answer|
|--------------------------|
|When did I start running after COVID hit in Montreal? When did I stop?|
|How far did I run?|
|How far did I run on average per run? Per week? Per month?|
|What does the distribution of my per-run distance look like?|
|On which days of the week did I run most frequently? Least frequently?|
|What did the temporal distribution of my running look like?|
|How did my max and average speeds change over time?|

Wow, having the table in the last post of all the variables with short descriptions has made it _way_ easier to think about this data and the kinds of questions I can ask and answer. 

Some meta-questions I need to answer is just a lot of unit stuff, I'm not sure if Strava records distances in the units the user picks or if it records them in some default and then just does the conversion when it's time to display them to the user. 

Even if I can't find that documented anywhere, I guess I could just compare the .csv values to those displayed in the GUI on my account and if it matches up, whether 1:1 or in the km:miles ratio that will give me the answer. Same thing for elevation, though it will be an issue if it's not straightforwardly meters or feet above sea level.



|Questions I came up with as I wrote this post|
|---------------------------------------------|
|What were the weather conditions like as I ran? Average? Coldest? Hottest?|
|What other activities did I do? Mostly biking I think, what did that look like?|
|In the period over which I recorded my biking as commutes, what did that look like as a daily distance figure?|
|Did I ever commute by running?|
|What was the pattern with respect to the relationship between elapsed time and moving time? In other words, did I stop a lot while running?|
|Who did I run with? How often?|
|What is the relationship between my distance and average speed?|
|How many different songs did I name in my activity metadata? What were they?|
