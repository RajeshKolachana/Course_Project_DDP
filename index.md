---
title       : Course Project- Shiny Application and Reproducible Pitch
subtitle    : Using Slidify
author      : Rajesh Kolachana
job         : Data analyst
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Overview
This presentation is developed as part of the Course project for Developing Data Products course. This course is part of the Data Science specialization in Coursera.

The course project contains two parts.
* Create and deploy a **Shiny** Application.
* Develop a Reproducible pitch in **Slidify**/ R studio Presenter for the application.


A shiny application which verifies the Central Limit theorem is deployed in the shinyApps.io website [here](https://rajeshkolachana.shinyapps.io/Course_Project_Shiny_Application_and_Reproducible_Pitch/)

--- .class #id 

## ui.R - Design layout

**fluid page**

* Side bar panel
  + helpText widget- To add help text
  + sliderInput widget- To choose "lambda"
  + numericInput widget- To choose "Number of iid Random variables"
  + checkboxGroupInput widget- To choose "Number of simulations"
  + submitButton widget- To submit

* Main panel
  + tabsetPanel widget
     - Plot tabPanel- To summarize the output
     - Documentation tabPanel- To help novice users get started

--- .class #id 

## server.R

* Operations on the ui input in sever.R are shown below.

```
output$plot <- renderPlot({
    set.seed(24)
    simulated_means = numeric(length = input$nsim)
    for (i in 1:input$nsim) {
      simulated_means[i] = mean(rexp(n = input$nrv,rate = input$lambda))
    }
    ...
    theoretical_mean <- 1/input$lambda
    ...
    })
```

* Reactive output displayed as a result of server calculations are made sure by using

```
shinyServer(function(input, output) {
   ...
   }))
   
```


--- .class #id 

## Summary

* The aim of this application is to verify the Central limit theorem using the exponential distribution. 
* In this project, the exponential distribution is obtained by averaging a few exponential random variables as inputted   in the side bar panel. 
* The distribution is standardised(centered and scaled) to investigate the Central limit theorem. 
* The iid random variables are drawn from a exponential distribution  with the rate lambda. 
* According to the Central limit theorem, the distribution of the averages of iid variables(properly standardised)       becomes that of a standard normal as the sample size increases. 


--- .class #id 

## Example

![](example1.png)

