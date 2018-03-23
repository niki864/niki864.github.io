---
priority: 0.9
title: Boston Crime 
excerpt: Analysis and mapping of crime in the Boston area
categories: works
background-image: bostoncrimeds.png
tags:
  - RStudio
  - ggplot
  - ggmap
  - lubridate
  - dplyr
---

## Crime Statistics Description

<div style="text-align: justify">Analysed the crime data provided by [https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system) to visualise and identify crime hotspots.
I first generated a crime heatmap based on reported locations of crime. 
Then, I thought it would be interesting to see the change in crime over a period of two years. 
I analysed the crime data, grouped it by district to actually see pct change in crime across two years.</div>

The dataset for 2016-17 has 91561 variables. I'm using a February to February year cycle.

Likewise, the dataset 2017-18 has 92041 variables.

## Packages Required

plyr, ggmap, ggplot2, lubridate ; all downloadable from CRAN

### Prerequisites

R and R Studio

## Dataset Description

<div style="text-align: justify">Data is available from the city of Boston data repositories. Crime incident reports are provided by Boston Police Department (BPD) to document the initial details surrounding an incident to which BPD officers respond. This is a dataset containing records from the new crime incident report system, which includes a reduced set of fields focused on capturing the type of incident as well as when and where it occurred. Records in the new system begin in June of 2015.</div>

Last Update of Dataset 02/04/2018 

Data Provided under Open Data Commons Public Domain Dedication and License (PDDL).

Simple complete case matching is done to remove any empty variables. Data is split into two chunks 2016-17 and 2017-18.

## Crime Density Map

First I went about with the geospatial visualisation. I utilised the ggmap library to pull a roadmap from Google Maps. This was later overlaid with multiple grammar of graphics layers for density gradient and more. Here's a code snippet.

```r
interestedregion <- ggmap(bostonmap)+
  #Create the density plots for crime regions. Bin size is responsible for resolution
  stat_density2d(data = lastyear, aes(x=lastyear$Long,y=lastyear$Lat,alpha=..level..,fill=..level..), bins=15,geom='polygon')+
  #Crime Density scale in range of dark magenta to orange to denote intensity. Use any color combination that makes sense
  scale_fill_gradient('Crime\nDensity', low = 'darkmagenta', high = 'gold') +
  #Populate map with the density color scheme
  scale_alpha(range = c(.2, .3), guide = FALSE)+
  guides(fill = guide_colorbar(barwidth = 1.5, barheight = 10)) +
  #Remove the axes titles long and lat
  theme(axis.title.y = element_blank(), axis.title.x = element_blank()) +
  ggtitle("Boston Crime February 2017 - February 2018")
```

<img src="https://user-images.githubusercontent.com/10093954/36330214-d1dc9344-1336-11e8-9b17-cb1a66cdea23.jpeg" alt="Drawing" style="width:100%;"/>


This map shows the crime density in Boston for a period of one year from February 2017 to February 2018. 

## Crime Statistics Districtwise

Next, I tackled simple statistics on the crime data and utilised barplot modeling on the frequency of crimes committed districtwise.
A minimalisitic theme is applied to make the barplots look nice. Here's the function I wrote to extract barplots.
```r
plotter <- function(dataset, title){
  #Plot the Barplot for the table created.
  plotout <- ggplot(dataset, aes(x=District, y=dataset[2],fill=District)) +
    geom_bar(stat = "identity") +
    #applies a minimalistic theme
    theme_minimal() +
    ggtitle(title)
  return(plotout)
}
```
First we generate a plot for the 16-17 year

<img src="https://user-images.githubusercontent.com/10093954/36330202-c209c126-1336-11e8-81ac-41a0234bc28b.jpeg" alt="Drawing" style="width:100%;"/>


Then we do the same for the 17-18 year.

<img src="https://user-images.githubusercontent.com/10093954/36330213-d1d155a6-1336-11e8-8536-bf77e99450e5.jpeg" alt="Drawing" style="width:100%;"/>


Now we can compare the percentage change between the two years and find out how much incidents of crime have changed

<img src="https://user-images.githubusercontent.com/10093954/36330215-d1e90052-1336-11e8-8052-07571a413c82.jpeg" alt="Drawing" style="width:100%;"/>



## Future

Will be working on a neural network to predict hotspots for the upcoming months. Will be interesting to see if that actually happens IRL. Leave your comments or feel free to contact me with suggestions.

## Codebase and License

Here's the full github repo for [this project](https://github.com/niki864/BostonCrime). This project is licensed under the MIT License - see the *LICENSE.md* file located in my github repo for more details.

## Acknowledgments

*  R Core Team (2013). R: A language and environment for statistical
  computing. R Foundation for Statistical Computing, Vienna, Austria.
  URL http://www.R-project.org/.

* R Packages used : Plyr, ggmap, ggplot2, lubridate