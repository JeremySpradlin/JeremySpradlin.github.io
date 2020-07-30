---
layout: post
title: Sunspotting
subtitle: Predicting Sun Spot Activity Via Upper Atmosphere Radiowave Fluctuations
cover-img: /assets/img/sun.jpg
tags: [Sun, Nasa]
---

# The Star of the Show

For thousands of years humans have had at least some significtant portion of our collective attention pointed towards the large, bright, and very hot disk
that would traverse the sky from one side to the other.  Indeed, many religions, both old and modern, hold the Sun as an object of worship.  The first recorded
observations of the sun date back to China, circa 2300 BC.  These were mostly just obserations for tracking seasons, until about a thousand years later when the 
Egyptions invented the Sun Dial, allowing us to utilize the sun for keeping track of time in a more precise manner throughout each day.  For millenia after this, 
not much changed.  Records were kept of it's movement through the sky, it's eclipses and other phenonemna as our limited ability to observe allowed, but it was 
not until 1610 when, using a telescope, the first detailed obserations of sunspots were recorded by Galileo.  

It was a centuries later, around the middle of the 19th century, that scientists began to recognize patterns in how the number of sunspots changed on the sun, 
and only in the last 100 years or so that we've really started to observe exactly how changes in the solar weather can have environmental effects here on Earth.

# Solar Weather

Today, most people are aware that what happens on the sun has an effect to at least some degree on what happens here on Earth.  It's fairly well known that Aurora 
Borealis, the Northern Lights, are the result of solar winds passing over our Magnetic Field.  Movies and other stories in popular culture have often referenced the 
potential dangers of solar flares, and more recently, you may have even seen articles recently discussing about how our Sun is entering into a "Solar Minimum", a 
period in the 11 year solar cycle where solar activity is at it's lowest, and there are few if any sun spots on the Sun.  We can acctually see this in our data:

INSERT SOLAR CYCLE GRAPH HERE

The relationship between solar weather, sunspot activity in particular, and electromagnetic intereference here on earth is a well established and documented 
phenomena, if not as well publicly known.  If you've ever had days where wireless communications may not have worked as well, cellular calls dropped more often, etc, 
this may have been due to a day where solar activity was high, and conditions allowed for increased interference.  We will be looking at whether or not we can predict
the number of sunspots on the sun at any given time, based on fluctuations in the electromagnetic spectrum here on Earth.  

# The Data

To accomplish this, I needed to join two different datasets; One containing daily sun spot totals, and one containing radio fluctuations in the relevant frequencies.  
I was able to find datasets for both of these on Kaggle, links to the sets are provided below.  After cleaning the datasets and normalizing dates to join them on, 
to ensure that we maintain the correct radio telescope readings with the correct number of sunspots, we are left with the following dataset containing both:

INSERT DF HEAD HERE

A first glance at this data set might be confusing with so many columns with names that might not make any sense to someone not trained in Radio Frequency Theory.  That's ok, all we really 
need to take away from this is that these different features represent different RF frequencies, and that we will be comparing power fluctuations at these 
frequencies to the number of sunspots, to see if we can determine the number of sunspots currently active by monitoring these frequencies.  

In order to validate and test our data, we split the data into Training, Validation, and Testing sets.

# Our Model

Every good prediction requires a good model, and so to make sure that we are using a model that will best predict our sunspots based on these fluctuations, I tried 
two different models, Linear Regression, and Random Forests.  Of course, to make sure that our model is actually predicting well, we need to establish a good baseline.  
Since this is a regression problem, all of our data is numeric in nature, we will look at Mean Absolute Error.  For our baseline prediction, we calculated MAE, 
assuming we predicted the average number of sunspots for each prediction.  This gives us an MAE of **67.69**.

So with our baseline in hand, let's start looking at models!

### Linear Regression

Being a regression problem, linear regression is definitely our first go to.  After fitting our data we ran our test metrics and got the following results:
- Training Accuracy:  0.9276294474130982
- Validation Accuracy:  0.9350867465372686

So for a first run, and no hyperparameter tuning, these are not bad results.  Our validation accuracy is actually slightly higher than our Training accuracy,
so it doesn't appear we have any issues with overfitting.  But what does this number mean exactly?  When we test with a linear regression model, the scoring metric
we get is our coefficent of determination, or our R^2 score.  In other words, this is telling us how well our model replicates our observations that we put into it.
But our baseline was Mean Absolute Error.  When we calculate our MAE for our trained model, we get **15.78**.  That's not bad, considering a baseline of almost 70.

### Random Forests

However, in data science, "not bad" usually isn't good enough, so I also fitted a Random Forest Regressor model to our data and got the following scoring metrics:
- Training Accuracy:  0.9954101921440627
- Validation Accuracy:  0.9707435623549717

Now these are some nice numbers. It looks like there might be a tad amount of overfitting with our training accuracy being so close to 1, however with a validation 
accuracy (R^2 score) of .97, any overfitting is minimal.  Let's look at our scores from our testing dataset and our MAE:
- Testing Accuracy:  0.9710094368330254
- Mean Absolute Error:  7.61

So this looks pretty good.  We get an R^2 score just above 0.97 and our MAE is quite low, even compared to our initial Linear Regression model.  Now that we've
got a model with our testing metrics looking pretty good, let's drive into the model and look at which features are giving us such good results:

INSERT FEATURE IMPORTANCE IMAGE

Unexpectedly, it looks as if the vast majority of our importance is distributed across a few features, with the remaining small amount of importance distributed 
across all the other features.  So what are these features? 

The top two features are 'f10.7' and 'f10.7_c'.  Yea don't worry, I have 2 decades of experience in wireless technology and even I was not familiar with these terms
at first.  f10.7 is the frequency name, specifically, the frequency where the wavelength is 10.7 centimeters in length.  So what f10.7 and f10.7_c are is the 
power measurements at 2800 MHZ across two different phases, or axies.  

# Results

INSERT SS OVER TIME GRAPH HERE

The plot above gives us the number of sunspots over a 70 year period and is colored by the amount of flux read at the f10.7 frequency.  We can see that as the number
of sunspots rise, so does the reading on that particular frequency.  As previously stated, there is a well known and documented relationship between this frequency and solar activity.  f10.7
is actually a commonly used index for monitoring solar activity, and after this exploration into predicting sun spots, I think it's quite evident why.  We can see similar
realtionships with solar activity and other bands, but the fluctuations are not as large as they are at the f10.70 band, and this is probably why we don't see those features
having as high an importance in our analysis.  

INSERT F15 over F30 GRAPH

In the graph above we see that readings in the f15 band go up to around 300, and up to around 200 for the f30 band.  

# Conclusion

Electromagnetic fluctuations within our own atmosphere can be higly dependent on how active the sun is, thought this dependence varies across different frequencies.  The relationship between fluctuations within the electromagnetic
spectrum and the number of active sunspots is quite clear from the above visualizations.  Being able to predict solar activity via radio wave can be highly advantageous 
for the future design of long term spacecraft as they can, with a high degree of accuracy, determine the number of active sunspots on the sun without using visual
detection technology.  This allows simple rf based sensors to be utilized for determining current activity levels, assuming such readings would be useful, without needing
additional expensive, and likely heavy technology on the vehicle.  

How useful this information might be is something that might be up for debate, as the data shows, the activity may fluctuate from day to day to some degree, but largely 
follows a much larger and longer pattern.  An 11 year cycle actually, so we should not expect massive changes in sunspot activity from one day to the next.  But if there
were to be massive changes on a day to day basis for whatever reason, we would be able to detect them through reading fluctuations in the electromagnetic spectrum 
here on earth without ever turning an eye to the sun.  



_____
#### Datasources:
Sunspots:  [Kaggle Sunspots](https://www.kaggle.com/abhinand05/daily-sun-spot-data-1818-to-2019)

Radio Flux:  [Kaggle Radio Flux](https://www.kaggle.com/davidjackson0513/radio-flux-1951-2019)
