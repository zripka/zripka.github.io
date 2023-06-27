---
layout: post
title: "Splitwise copycat (part 1): Docker"
permalink: /splitwise-copycat-1/
---
The financials get hazy. You're getting beers with your friends, going hiking, making dinner for as many people as you can cram in the living room.

![The sky in Three Hills in the winter](/assets/21-12-31-three-hills-sky.PNG)
_Three Hills, Alberta (December 2021)_

Road trips, in the summer to the mountains and in the winter to visit friends in other cities. Someone drives and buys all the gas, you cover groceries, someone else pays for the gear rental and then it starts getting hard to tell who owes who how much.

Historically speaking there's an astonishingly [diverse](https://en.wikipedia.org/wiki/Debt:_The_First_5000_Years) set of ways to handle these kinds of situations, but in my circles a lot of people use something like Splitwise or Tricount. I've been shopping toy project ideas and I decided to build one of these settling-up calculators for a bit of Python practice.

# First up: Docker
It brings me no pleasure to announce that I just burned another hour of my life wrangling Python dependencies, but I can finally run pip and python properly again (please clap). My vision with this app is to run the back end, front end, and database services in different Docker containers to emulate a real-life architecture, and so that I can learn to use Docker.

I don't know, is that the whole post? Here:
- a front end running that lets a user log in, put their expenses in + who owes them for what
- a database that persistently stores the user data
- a back end service that mediates between the front end and the database and does some processing (ie reconciling the users' debts to one another)

(uhhhh is this going to mean I need to learn double-entry accounting)
