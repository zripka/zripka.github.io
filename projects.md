---
title: Projects
permalink: /projects/
---
# Mapping COVID-19 in Montreal
I made these two maps in spring 2021 for the Trottier Family Foundation. The purpose of the maps was to inform policy discussions, especially the placement of vaccine sites and vaccine equity.

![a map showing COVID-19 infection rates across the island of Montreal](/assets/21-05-20-case-map-02.png)
This map shows, at the neighbourhood level, the number of new COVID-19 cases per 100 000 people for the 4-week period leading up to May 10th, 2021. 


![a map showing COVID-19 vaccination rates across the island of Montreal](/assets/21-05-20-vaccine-map-01.png)
This map shows the percentage fully vaccinated residents, current to May 16th, 2021. The geographic unit is smaller than a neighbourhood, called the "territoire de voisinage de residence" and defined by Montreal public health (DRSP). It translates roughly to "neighbourhood residence zone."

# Optimizing housing placement
I produced this [report](/assets/21-11-13-geog-306-final-report.pdf) for a class while I was in school. We took several layers of geographic data, each one representing a factor that would influence how suitable a site would be to build a house. 

I chose to find a location with lots of space (low population density), proximity to natural areas, low flood risk, and south-facing aspect for good gardening conditions. I also included clean air and water, and so I included distance from NPRI-reporting pollution sites as a factor.

To find the best place to build a house based on my criteria, I normalized all of the factors to a comparable scale, created a simple weighting scheme, and ran the calculation in ArcGIS. My result is marked by the star symbol in the maps below.
&nbsp;

&nbsp;

![a map showing npri pollution sites near Bonnyville Alberta](/assets/21-11-13-npri-sites-map.png)
&nbsp;

&nbsp;

![a map showing land use near Bonnyville Alberta](/assets/21-11-13-land-use-map.png)
&nbsp;

&nbsp;

![a map showing aspect near Bonnyville Alberta](/assets/21-11-13-aspect-map.png)

# COVID-19 and poverty
Without a doubt, the risk of contracting COVID-19 throughout the pandemic is [associated](https://nancyrossresearchgroup.ca/2020/07/03/updated-scatterplots-highlight-link-between-income-and-covid-19-in-north-american-cities/) with poverty. When I was a research assistant in the [Geo-social Determinants of Health Research Group](https://nancyrossresearchgroup.ca/) at McGill University, my colleagues and I worked to effectively [visualize](https://nancyrossresearchgroup.ca/2020/11/16/new-interactive-map-shows-relationship-between-income-and-covid-19-in-montreal/) the relationship between income and infection rates.

[![a map showing the relationship between COVID-19 infection rates and neighbourhood income](/assets/21-11-10-covid-income-screenshot.png)](https://nancyrossresearchgroup.ca/2020/11/16/new-interactive-map-shows-relationship-between-income-and-covid-19-in-montreal/)

The darker the blue colour, the higher the neighbourhood's median income. The darker the red colour, the higher the COVID-19 infection rate. Dragging the toggle back and forth allows for easy comparison of the two variables, and shows a clear relationship: dark blue neighbourhoods tend to be light red, and vice versa, visually revealing the inverse relationship between income and COVID-19 infection rates.
