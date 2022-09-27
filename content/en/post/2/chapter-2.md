---
date: 2021-12-25T10:58:08-04:00
description: "Performing Explanatory Data Analysis on the massive Companies House dataset containing 5M rows and 50+ columns. How many companies incorporated during lockdowns? Are there any particular industries? "
featured_image: "/images/open.jpeg"
title: "Business foundational patterns during pandemic in the UK" 
---
• How many companies were incorporated during the pandemic? Did the number fall? How did the number change month by month? How was it in comparison to a previous couple of years? How did this trend differ across industries?

• Considering London as the centre of economic activity with the most significant number of companies registrations, did the pandemic affect the location of companies’ birth?

• How did the number differ across all possible SIC codes?

# Here we go 🚀

## 1. Geo-spacial animation
{{< figure src="/images/Chart3_FCP.gif" >}}

## 2. Interrupted time-series chart
{{< figure src="/images/chart_1.png" >}}

## 3. Interactive slope chart using Bokeh
[Dowload(Save as)](https://raw.githubusercontent.com/sinkov/companies_COVID/main/Final%20Course%20Project/Chart2_FCP.html) and open it in your browser. 

P.S. Apologies for extra steps to open the html file... I have not find a way yet to add html frame is this constructor...
Here is a screenshot 🙈 {{< figure src="/images/bokeh.png" >}} 

The codes for each chart can be found [here](https://github.com/sinkov/companies_COVID/tree/main/Final%20Course%20Project) (if anyone ever opens it 😬).
## Aim and context

The attention revolves on the effects of the Covid-19 pandemic on businesses.
You're a data scientist with a taste for data visualization who wants to
publish a [Towards Data Science](https://towardsdatascience.com/) blog post
showing the impact of the pandemic on business foundation patterns. 

## Dataset

The data repository of Companies House provides a [series of compressed 
folders](http://download.companieshouse.gov.uk/en_output.html) comprising 
firm-level attributes you may find useful. If you need more granular data
please refer to [monthly files](http://download.companieshouse.gov.uk/en_monthlyaccountsdata.html).