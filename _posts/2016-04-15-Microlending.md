---
layout: post
title: Loan activity among microlenders
published: true
---
## Microlending as a service for the unbanked

There are an estimated [2 billion](http://www.cgap.org/about/faq/who-are-2-billion-unbanked-adults-globally) unbanked adults who lack access to traditional financial services, including credit. Microloans are small loans that provide credit to these lower-income, typically unbanked borrowers. Using platforms like Kiva, individuals can become microlenders and connect to borrowers in other parts of the world. Since Kiva was founded in 2005, 1.4 million lenders have issued $840 million in loans across [84 different countries](https://www.kiva.org/about). Other companies and non-profits have taken notice, and are moving into the microlending space. 

One of these organizations – [Seeds](http://playseeds.com) – asked me to investigate the following question: who are microlenders?

## Methodology

Kiva helpfully provides lender, loan, and borrower data through [its API](https://build.kiva.org). From the API, I downloaded a data snapshot of json files, and sampled this data to see if demographic data provided in the sample data was related to the average number of loans that Kiva users make per year. Below is a depiction of the methodology an workflow that I employed to complete this analysis. 

![Summary of methodology]({{site.baseurl}}/pgr-me.github.io/images/001_microlending_methods.png)

I downloaded 1,860 json files, each containing 1,000 lender records. each record included name, occupation, location, reason for lending, number of loans, and Kiva join date. IAfter training my model on various trial feature sets, I decided to include the following in my final feature set: gender, region, tech involvement, and lending. I deduced gender from name data and aggregated location into two categories: 1) United States & Canada and 2) the rest of the world. I derived tech involvement from occupation, and took the string length of lending reason as a gauge to test a given lender's enthusiasm. 

## Analysis

A histogram of loans per year indicates that loans per year may be distributed exponentially.
![Distribution of lender loan activity]({{site.baseurl}}/pgr-me.github.io/images/001_microlending_hist.png)
