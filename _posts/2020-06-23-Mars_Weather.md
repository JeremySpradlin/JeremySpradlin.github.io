---
layout: post
title: Interplanetary Forecasts
subtitle: Detecting Seasonal Weather Patterns from Mars Curiosity
cover-img: /assets/img/mars.jpg
tags: [Mars, Nasa]
---

# The God of War - In Progress

For as long as humans have looked up and kept track of the moving heavens, the Red Planet has filled the human imagination with stories and myths. Some with their origins extending back into history farther than we can see, and many being more recent, as the eyes that we use to observe the sky and the other planets in our solar system have grown more and more advanced.  

The past few decades have even seen humanity landing machines on our distant neighbor with an array of cameras and other sensors, in order to collect information and beam it back to earth so that we can better get to know the God of War.  One of the most recent machines we've sent to Mars is the rover Curiosity.  Today, we're going to see if Curisoity can tell us any stories about what the weather patterns on Mars are like.

## One Giant Leap for Machine Kind

Curiosity is a car-sized rover designed to explore the Gale crater. Launched from Cape Canaveral in November of 2011, and landing on Mars almost 9 months later, Curiosity contains many different scientific instruments, with a focus on Martian climate and geology.  We will be looking at data from the REMS package for exploring seasonal changes in the local weather.  

The Rover Environmental Monitoring Station, or REMS for short, contains instruments designed to provide daily and seasonal reports on the meteorological conditions around the rover.  Over the course of 6 years, data was collected for the max and minimum temperatures, as well as air pressure.  In this article, we will look to see what sort of annual weather patterns we can detect, if any, from analyzing that data.  

## A Martian Year

When looking at annual weather patterns from our rover on the surface of Mars, it helps having a breif overview of the Martian year.  Here on Earth, our years are a little over 365 days long, divided into twelve months.  Mars also has 12 months, but each month is a little longer, as a Martian year is approximately 687 Terran days (24 hours).  The 12 months are taken by using a measurement, The Solar Longitude, or Mars-Sun angle, which is the angle of the sun to the planet as measured from the northern hemisphere.  This measurement is referred to as Ls.  

<p align="center">
  <img width="460" height="300" src='http://www-mars.lmd.jussieu.fr/mars/time/orbit.png'>
</p>

The Ls measurement is important to understand as we will be looking at Ls as an indicator of where in the annual cycle data was collected from, rather than earth date/times.  The Ls variable gives us a good starting position, `0`, and counts all the way up to `360` degrees to indicate where our red neighbor is located in their trip around the Sun.  As an example, in the graph below, we see over the course of 6 years, we see our Ls variable shift through it's 0 to 360 scale 3 times, which is what we would expect with an orbit of just under two of our years, over a period of about 6 years.

<p align="center">
  <img width="460" height="300" src='/assets/img/ls_measurements.png'>
</p>

<iframe style="border-width:0" src="https://charts.sharpdesigndigital.com/jeremy-avg_month_pressure.html" width="750" height="800"> </iframe>

As we can see above, over the course of almost 2000 sols, or almost 6 years, we see our Ls measurment cycle through all 360 degrees almost 3 full times.  This tells us that any annual weather patterns that we see in our data, should equate to about 3 full orbital periods around the sun.  

Let's look at some of our data and see what we have to analyze:

<p align="center">
  <img width="900" height="200" src='/assets/img/Mars_data.png'>
</p>

The first thing you might notice is that we are missing some wind speed data, and a deeper analysis showed that atmospheric opacity was pretty much all sunny, or did not contain any data.  This isn't unexpected, given that while Mars may have seasonal weather, it is not known for it's thunderstorms. (Sandstorms are a different matter, however). This leaves us with temperature and pressure data.  A quick glance at our maximum recorded temperature data shows the following:

<p align="center">
  <img width="460" height="300" src='/assets/max_temp_ls.png'>
</p>

We can also see that same 3 year pattern in the maximum temperature graph above.  This graph is colored by our Ls measurement so that we can see where Mars is in it's orbit compared to the temperature readings.  You may recall that a Martian year is about 687 days, which is roughly the the amount of the number of Sols we see between the peaks on our graph, as well as the time between shifts in the Ls measurements.  

We can see already that there are seasonal fluctuations in temperature data, at least at the Gale Crater where Curisoity is taking it's readings.  But the above graphic can be difficult to predict what temperatures are like in a particular month in any given year.  Below we will look at averaged temperatures for each of the 12 months, to give us an idea of what temperatures we might expect were we to visit Curiosity, no matter the month of our arrival.

<p align="center">
  <img width="460" height="300" src='/assets/img/avg_month_temps.png'>
</p>

As we can see, temperature fluctuations are almost what we would expect in any given year here on Earth, at least in our northern hemisphere, with the coldest months being the first few months of the Martian year, or after the Northward Equinox, and the warmest months being in the Southward equinox period.  Months can be difficult ot work with as a measurement of time with Mars, as the months there can very in length much greater than they do here.  The shortest month is about 46 Sols, while the longest is about 67.  It was mentioned that Curiosity landed in the Gale Crater, which is located on Mar's equator, so we can expect that these temperatures are much warmer than they would be at lattitudes further north or south. <mark>Below we can see temperature ranges as they appear throughout an average year.</mark>

### Insert Annual Average Temp Range Graph (If completed on time)

## Pressure So Low You Can Feel It

If the cold termperatures on Mars aren't enough to keep tourists away, the extremely low air pressure should do it.  Average air pressure on Earth is a little over a 1,000 milibars, while the average air pressure on Mars is about 6-7 milibars.  That's below 1% of our own pressure, which means any organic visitors will need to come prepared, as exposure to such pressures would be... unpleasant.  

The REMS package on Curisoity has been measuring the air pressure in pascals, and some interesting things stand out when we look at the pressure plotted out over the duration of Curiosity's stay:

<p align="center">
  <img width="460" height="300" src='/assets/img/pressure_sol.png'>
</p>

What's really interesting about this is that we can see our 3 Martian year pattern show up in our pressure data.  That is remarkable in that there is no seasonal variation of air pressure on Earth.  What's occuring on Mars is that, as the weather gets colder, it's cold enough for CO2 to actually freeze out of the air, causing air pressure to drop by as much as 30% around the planet!

You might be noticing the double-peaked portion of the graph, where the air pressure starts to drop, only to rise again, before dropping all of the way.  While I was unable to verify this, looking at the Ls measurements at the time of these pressure drops, the eccentricity of Mars orbit being more oval than Earth's seems to cause this mini-seasonal variation.  

If we look at the average pressure for each month, we can see this in greater detail:

<p align="center">
  <img width="460" height="300" src='/assets/img/avg_month_pressure.png'>
</p>

If we compare this to the image at the top of the article displaying Mar's orbit, we can see that as the pressure drops in Month 2 of the year, Mars is making it's way towards the aphelion portion of it's orbit, or the position furthest from the sun, and the air pressure rises again as the planet moves around towards it's perihilion position, before continuing on to start the process all over again.  

## An Unhospitable Environment

After this brief glance at the weather data from the rover Curiosity, I think it is quite evident that there are seasonal variations in the weather on Mars. Just in the temperature fluctuations alone at the equator, where Curiosity is located, they go from freezing in the summer, to deadly in the winter.  

Cold temperatures aside, to every young dreamer's dissapointment, with the extremely low air pressure it is not a friendly environment to flesh and blood organisms.  With yearly highs just touching positive digits for temperatures, the extremely low air pressure means any visitors will have to wear a full protective suit, no matter how favorable the sunny skies might be that day.  

However, any system that is in motion is a system that can be modifed, and maybe one day, with enough ingenuity and advancements in terraforming, our human decscendants will walk freely under the Martian night sky, and look up and dream about the 3d rock from the sun.

