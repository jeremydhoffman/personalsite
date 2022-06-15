---
title: 'Data Visualization of the Week: the State of Abortion Services in the US'
author: admin
date: '2022-06-14'
slug: data-visualization-of-the-week-the-state-of-abortion-services-in-the-us
categories: []
tags: []
subtitle: ''
summary: ''
authors: []
lastmod: '2022-06-14T22:10:37-04:00'
featured: no
image:
  placement: 1
  caption: ''
  focal_point: ''
  preview_only: yes
projects: []
---
![abortion static](images/abortion_static.png)
This summer, I’ve decided to put my newly acquired data analysis and visualization skills to good use. Each week I’ll be producing a series of data visualizations covering noteworthy topics in the health policy space. 

For the first visualization in this series, I decided to focus on the issue of abortion services. With the Supreme Court’s decision in [Dobbs v. Jackson Women’s Health Organization](https://www.supremecourt.gov/search.aspx?filename=/docket/docketfiles/html/public/19-1392.html) expected imminently, now is a particularly opportune time to consider the current state of abortion services in the U.S.

The choropleth map shown above depicts the average travel distance (in miles) to the nearest abortion clinic in each county. The data represented here are from June 2021, although it is clear that average travel distances have increased in recent years. This can be seen in the animated choropleth map shown below.

![abortion animated](images/abortion_animated.gif)
In 2009, the average distance to the nearest abortion clinic (across all counties) was 74.1 miles. By 2021, it had increased 78 miles. This might sound like a small increase, but what these national averages mask is the fact that some women have been forced to travel substantially further to obtain medical care. Notice, for example, how the travel distances visibly increase in western Texas and New Mexico (as denoted by the orange and yellow coloring on the choropleth map). 

As of June 2021, the county with the highest average travel distance was Divide County, North Dakota, with an average travel distance of 383.57 miles, whereas the county with the lowest average travel distance was Essex County, New Jersey, with an average travel distance of 0.20 miles.

It remains to be seen what the exact effects will be if Roe v. Wade is overturned (as is widely anticipated), however, it is fair to assume that obtaining abortion services will become substantially more difficult for a large segment of the US population. Analysts at the Guttmacher Institute suggest that 22 states have laws or constitutional amendments already in place that make an attempt to ban abortion certain if Roe v. Wade no longer stands. They also estimate that a further four states are likely to ban abortion within the near future.[^1]

**Data source**: The data used in these analyses are sourced from the publicly available portion of the Myers' Abortion Facility Database, a comprehensive database of all facilities—including private physician offices, hospitals, and freestanding clinics—that publicly advertise the provision of abortion services or are otherwise likely to be identifiable to a large fraction of women seeking an abortion. The full dataset is available at: [https://osf.io/8dg7r/](https://osf.io/8dg7r/)

**Methods & Tools**: All data wrangling, analysis, and visualizations were conducted utilizing R. 

{{% callout note %}}
**Want to learn more about how travel distance affects abortions and births?**<br>
Check out the following paper written by Caitlin Myers, the academic who compiled the data on which this post is based. 

Caitlin Myers. 2021. "Measuring the burden: The effect of travel distance on abortions and births" IZA Discussion Paper No. 14556. Available at: [https://www.iza.org/publications/dp/14556](https://www.iza.org/publications/dp/14556)
{{% /callout %}}

[^1]: https://www.guttmacher.org/article/2021/10/26-states-are-certain-or-likely-ban-abortion-without-roe-heres-which-ones-and-why
