---
title: 'Data Visualization of the Week: Drug Overdose Epidemic'
author: admin
date: '2022-07-08'
slug: data-visualization-of-the-week-drug-overdose-epidemic
categories: []
tags:
  - Health Policy
  - Data Visualization
  - Drug Overdose
  - Substance Use
subtitle: ''
summary: ''
authors: []
lastmod:
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
  placement: 2
projects: []
---
According to the CDC, since 1999, more than 932,000 people have died from a drug overdose in the United States.[^1] During this same period, the number of annual drug overdose deaths has quadrupled.[^2] More recent (provisional) data also suggest that overdose mortality rates reached record levels during the pandemic.[^3] It is thus clear that the U.S. is currently facing a drug overdose epidemic. 

This week, I decided to explore these trends by examining the geographic variation in drug overdose deaths over time. The figure above depicts county-level estimated crude overdose mortality rates from 2004-2020. 

At the beginning of this period, we see that overdose mortality rates remained fairly low across the board, with the vast majority of counties experiencing between 1.29 - 9.85 drug overdose deaths per 100,000 people. The distribution of overdose mortality rates among U.S. counties in 2004 is shown in Figure 2. 

![histogram_2004](images/histogram_2004.jpg)
*Figure 2. Distribution of Estimated Crude Drug Overdose Mortality Rates: US Counties, 2004*

{{% callout note %}}
For the purpose of these analyses, drug overdose mortality rates were binned using Jenks (natural) breaks in order to optimize the goodness of variance fit and to better visualize the epidemiological trends, hence the reason for the irregular class intervals shown in the histograms above and below. 
{{% /callout %}}

Notable exceptions to this trend include a large cluster of counties within the Appalachian region, as well as a handful of other counties located in a small number of states, which include California, New Mexico, and Louisiana (see Figure 1 at the top of this post). 

By the end of the study period, however, the distribution of overdose mortality rates among U.S. counties had shifted dramatically (see Figure 3).

![histogram_2020](images/histogram_2020.jpg)
*Figure 3. Distribution of Estimated Crude Drug Overdose Mortality Rates: US Counties, 2020*

Rather than the highly skewed distribution shown in Figure 2, estimated crude overdose mortality rates in 2020 appear to be more normally distributed. Moreover, over the 16 year study period, all U.S. counties saw an increase in overdose mortality rates compared to 2004 baseline levels. The 10 counties/county equivalent geographic areas that witnessed the largest increases in mortality rates (in absolute terms) are listed in Table 1 below. 

**Table 1. U.S. Counties/County Equivalents Experiencing the Largest Change in Estimated Crude Overdose Mortality Rates 2004-2020**

| County                   	| State                         	| Change in Estimated <br>Crude Overdose Mortality <br>Rate (2004-2020) 	| Relative Change<br>(in Percentage <br>Terms)              	|
|--------------------------	|-------------------------------	|-----------------------------------------------------------------------	|-----------------------------------------------------------	|
| McDowell County          	| West Virginia                 	| + 108.88                                                              	| + 245.80%                                                   	|
| Scioto County            	| Ohio                          	| + 107.12                                                              	| + 492.26%                                                   	|
| Cabell County            	| West Virginia                 	| + 103.72                                                              	| + 413.77%                                                   	|
| Baltimore City           	| Maryland                      	| + 103.68                                                              	| + 281.08%                                                   	|
| Raleigh County           	| West Virginia                 	| + 100.19                                                              	| + 366.85%                                                   	|
| Logan County             	| West Virginia                 	| + 98.25                                                               	| + 265.31%                                                   	|
| Wayne County             	| West Virginia                 	| + 89.08                                                               	| + 417.92%                                                   	|
| St Louis City            	| Missouri                      	| + 81.06                                                               	| + 495.53%                                                   	|
| Kanawha County           	| West Virginia                 	| + 81.01                                                               	| + 441.40%                                                   	|
| Knott County             	| Kentucky                      	| + 76.03                                                               	| + 289.11%                                                   	|                                            	|

## Mapping the Most Recent Overdose Mortality Rates

The following interactive choropleth map provides a snapshot of estimated crude overdose mortality rates for 2020, i.e., the most recent estimates from the NCHS dataset. You can check out the estimated number of drug overdose deaths in your area by hovering over the relevant county.

{{% staticref "/leaflet/od_rates_2020_map.html" "newtab" %}}Click to view the interactive map in full-screen mode{{% /staticref %}}

<iframe seamless = "" width = "100%", height = "500" class = "shortcode-iframe" src="/leaflet/od_rates_2020_map.html"></iframe>

{{% callout note %}}
Note: There are a small number of counties for which estimates are not available. These are shown as transparent tiles in the interactive choropleth map. 
{{% /callout %}}

## Policy Implications

Based upon current trends, it is evident that rising drug overdose mortality rates represent a serious and urgent public health crisis. Given the substantial geographic heterogeneity in overdose rates observed, it is also clear that some populations are more at risk than others.

While many U.S. states have recently implemented supply-side controls and harm-reduction policies aimed at reducing drug overdose mortality, they have so far failed to stem the rising tide of overdose deaths. In fact, a recent [study](https://doi.org/10.1001/jamanetworkopen.2020.36687) published by researchers at Indiana University suggests that some of these policies may in fact be counterproductive by motivating those with opioid use disorders to switch to alternative illicit substances, leading to higher overdose mortality.[^4] Policymakers must therefore continue to search for effective solutions for combating the drug overdose epidemic.

**Data Source & Notes**: The data used in these analyses were sourced directly from the National Center for Health Statistics (NCHS). The full dataset is available at: [https://www.cdc.gov/nchs/data-visualization/drug-poisoning-mortality/](https://www.cdc.gov/nchs/data-visualization/drug-poisoning-mortality/). 

These estimates were in turn based on the National Vital Statistics System (NVSS) multiple cause-of-death mortality files.[^5] Deaths were classified using the International Classification of Diseases, Tenth Revision (ICD-10). Drug overdose deaths were defined as having ICD-10 underlying cause-of-death codes X40-X44 (unintentional), X60-X64 (suicide), X85 (homicide), or Y10-Y14 (undetermined intent). Populations used for computing death rates for 2011-2018 were postcensal estimates based on the 2010 U.S. Census. Rates for census years were based on population estimates and may differ from rates previously published. 

County-level estimates were generated using Hierarchical Bayesian models with spatial and temporal random effects using the INLA package for R.[^6] 

Annual county-level drug overdose deaths were modeled as a function of: (1) an overall intercept; (2) a fixed effect for year; (3) spatial random effect, which accounts for clustering of drug overdose death rates; (4) a non-spatial random effect, which accounts for any residual county-level variation; (5) a temporal random effect, which accounts for non-linearities over time by allowing the value in a given year to depend on the value in a prior uear, plus an error term; and (6) a space-time interaction term (i.e., a county- and year-specific random effect), accounting for any residual spatiotemporal variation. 

Further techinical notes about the methods employed by NCHS are available at: [https://www.cdc.gov/nchs/data-visualization/drug-poisoning-mortality/](https://www.cdc.gov/nchs/data-visualization/drug-poisoning-mortality/).

**Methods & Tools**: All data wrangling, analysis, and visualizations were conducted utilizing R. Packages utilized included: tidyverse, tigris, ggthemes, RColorBrewer, XploreR, sf, leaflet, classInt, scales, htmltools, and htmlwidgets. 

[^1]: Centers for Disease Control and Prevention. Death Rate Maps & Graphs. https://www.cdc.gov/drugoverdose/deaths/index.html, citing Wide-ranging online data for epidemiologic research (WONDER). Atlanta, GA: CDC, National Center for Health Statistics; 2021. Available at http://wonder.cdc.gov
[^2]: Centers for Disease Control and Prevention. Death Rate Maps & Graphs. https://www.cdc.gov/drugoverdose/deaths/index.html, https://www.cdc.gov/drugoverdose/deaths/index.html
[^3]: National Vital Statistics System. Provisional Overdose Death County. Available from: https://www.cdc.gov/nchs/nvss/vsrr/drug-overdose-data.htm.
[^4]: Lee B. L., Wanying Z, Kai-Cheng Y, Yong-Yeol A, Brea L. P.Systematic Evaluation of State Policy Interventions Targeting the US Opioid Epidemic, 2007-2018. JAMA Netw Open. 2021;4(2):e2036687, https://doi.org/10.1001/jamanetworkopen.2020.36687
[^5]: National Center for Health Statistics. National Vital Statistics System: Mortality data. Available from: http://www.cdc.gov/nchs/deaths.htm.
[^6]: Khan D, Rossen LM, Hedegaard H, Warner M. A Bayesian spatial and temporal modeling approach to mapping geographic variation in mortality rates for subnational areas with R-INLA. J Data Sci. 2018;18: 147-182; Bivand RS, Rubio-Gomez V, Rue H. Spatial data analysis with R-INLA with some extensions. J Stat Softw. 2015;63(20); Rue H, Martino S, Chopin N. Approximate Bayesian inference for latent Gaussian models by using integrated nested Laplace approximations. J R Stat Soc Series B Stat Methodol. 2009;71:319-392.


