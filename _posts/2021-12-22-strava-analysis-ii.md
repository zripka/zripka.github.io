---
layout: post
title:  "Analyzing Strava data in R (part 2)"
date: 2021-12-22 -0400
---
I still haven't settled on a great answer to the question "What format do I follow in these posts?" It's part report, part lab notes, and part tutorial and I think for now that's the way to go for me. I used this [book](https://r4ds.had.co.nz/) a lot to learn this stuff.

|Questions I want to answer|
|--------------------------|
|When did I start running after COVID hit in Montreal? When did I stop?|
|How far did I run?|
|How far did I run on average per run? Per week? Per month?|
|What does the distribution of my per-run distance look like?|
|On which days of the week did I run most frequently? Least frequently?|
|What did the temporal distribution of my running look like?|

# Setup
I started a new project in RStudio and started a git repository I pushed to GitHub.

# The dataset
There are a _ton_ of variables in the activities.csv file, like 83 of them. I picked ID, date, name, type, description, elapsed time, distance, relative effort, commute, moving time, max speed, average speed, elevation gain, elevation loss, elevation low, elevation high, number of runs, uphill time, downhill time, other time, perceived exertion, and total weight lifted. 

Why is there multiple "elapsed time" and "distance" variables? Do I care about the "elevation low" and "elevation high" variables? What does "Number of Runs" mean? What does "Other Time" mean? What's the difference between "Relative Effort" and "Perceived Exertion"?

|Questions I came up with as I wrote this post|
|---------------------------------------------|
|How did my max and average speeds change over time?|

