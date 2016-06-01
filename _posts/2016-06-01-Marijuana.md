---
layout: post
title: Loan activity among microlenders
published: true
---

The legality of and public's view towards marijuana is rapidly [changing](http://www.pewresearch.org/fact-tank/2015/04/14/6-facts-about-marijuana/) as more states decriminalize and legalize the drug. As such, how have the words associated with marijuana in news articles changed over time?

## Methodology

I developed a two-step approach to to try to answer this question. First, I wanted to identify distinct eras characterized by the use of key words associated with marijuana. Second, I aimed to assess whether words in each era represented larger themes regarding the public's view toards marijuana and the the drug's legality.

![Summary of methodology]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-methodology.png)

I downloaded 1,860 json files, each containing 1,000 lender records. each record included name, occupation, location, reason for lending, number of loans, and Kiva join date. After training my model on various trial feature sets, I decided to include the following in my final feature set: gender, region, tech involvement, reason for lending, and invites sent to other users. I deduced gender from name data and aggregated location into two categories: 1) United States & Canada and 2) the rest of the world. I derived tech involvement from occupation, and took the string length of lending reason as a gauge to test a given lender's enthusiasm. 

## Analysis

A histogram of loans per year indicates that loans per year may be distributed exponentially, with most lenders making just a few loans  in a typical year. Within the sample, the mean loans per year was about 4 per year with a standard deviation of 12.

![Distribution of lender loan activity]({{site.baseurl}}/pgr-me.github.io/images/001-microlending-hist.png)

The chart below shows that Kiva users tend to be based in the US and male. Additionaly, almost 20% of the sample is involved in the tech industry or sciences.

![Segment Splits]({{site.baseurl}}/pgr-me.github.io/images/001-microlending-splits.png)

I wanted to get an idea of the sample distribution by category, and so I created the chart below using [Seaborn](https://stanford.edu/~mwaskom/software/seaborn/). We can see that the distribution of people from the US and Canada seems to be more concentrated at the lower end of loans per year axis than those in the rest of the world. In addition, high loans per year outliers are primarily male.

![Categorical Scatter Plot]({{site.baseurl}}/pgr-me.github.io/images/001-microlending-scatter.png)

The statistical results are shown below. The R-squared value is low, and so the model's predictive power is nil. However, p values for the gender, region, invites per year, and lending reason features are low enough that we can reject the null hypothesis that these features have no impact on lending activity.

![Regression Statistics]({{site.baseurl}}/pgr-me.github.io/images/001-microlending-regstats.png)

## Conclusions and Next Steps

This is a preliminary analysis, and more insights could be gleaned from the Kiva data. Even so, we can draw the following conclusions from this analysis:

- Microlending activity across microlenders seems to be exponentially distributed;
- While the model developed for this analysis is not predictive, it does explain a subset of the types of people that tends to make more microloans;
- Within the sample data, males and people living outside the US and Canada tend to be more active microlenders; and,
- More analysis is needed before we can say the same for people involved in tech and the sciences.

Further analysis may show that the selected features for this model should be refined, removed, or added. With a more predictive model, I could move on to test the training data with test data to see if model is over or under fitted. Check out my [code](https://github.com/pgr-me/metis_projects/tree/master/microlending) on Github.
