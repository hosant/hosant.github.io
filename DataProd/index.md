---
title       : A Mileage Prediction Application
subtitle    : Simple Shiny App. Example
author      : Santiago Hernandez
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, bootstrap]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Power vs Milleage.  
  
An important factor when choosing a vehicle is **power**. A low power car will often struggle
with high loads and difficult terrain. It can be said that power correlates with the *usefulness*
of a car.  

However, power is hardly free. **Mileage**, defined as *distance* (measured in miles) travelled per *unit of combustible*, 
is also widely considered as one of the most important topics when choosing a car as it 
correlates directly with the cost of use. Higher power often means higher energy consumption, 
which is quantified as lower Mileage.  

### But by how much can we *expect* power to impact fuel consumption?  
  
> Balancing power and mileage is of paramount importance when choosing and designing a vehicle.
* Higher power often means higher fuel consumption.
* We would like to quantify how is mileage expected to change in function of power.

--- .class #id 

## A Simple Mileage Prediction Algorithm.

In order to solve this question I propose as a first approximation to use a linear model fitting
a data set with the two variables.  

The data used is the *mtcars* data set found at the *datasets* packages of base
**R**. This data was "*extracted from the 1974 Motor Trend US magazine, and comprises fuel 
consumption and 10 aspects of automobile design and performance for 32 automobiles (1973–74 models)*".
The units used are **Miles per Gallon** and **HP (Horse Power)**.  

> We compute the model using a least squares approximation to the data by calling the following **R** script:
> 
> ```r
> modFit <- lm(mpg~hp, data = mtcars)
> ```

> And we show it's parameter with the following code:
> 
> ```r
> summary.lm(modFit)
> ```

---

## Fitness of the Model.




```
## 
## Call:
## lm(formula = mpg ~ hp, data = mtcars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -5.7121 -2.1122 -0.8854  1.5819  8.2360 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept) 30.09886    1.63392  18.421  < 2e-16 ***
## hp          -0.06823    0.01012  -6.742 1.79e-07 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 3.863 on 30 degrees of freedom
## Multiple R-squared:  0.6024,	Adjusted R-squared:  0.5892 
## F-statistic: 45.46 on 1 and 30 DF,  p-value: 1.788e-07
```

---

## The Application.

The prediction uses a least squares linear model fitting the *mtcars* dataset. As the summary shows 
in the previous slide shows, the percentage of 
explained variation by this model is 60.2%, with a P-value close to 0.  

From the model we infer that we **expect a decrease on mileage of -0.068** per unit of power.

A convenient way to consult the computed model is the associated Shiny Application that can be found at: 
  
https://hosant.shinyapps.io/DataProdAss

Instructions can be found on the page.
