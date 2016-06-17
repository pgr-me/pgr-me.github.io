---
layout: post
title: Marijuana through the lens of the New York Times
published: true
---

The legality of and public's view towards marijuana is rapidly [changing](http://www.pewresearch.org/fact-tank/2015/04/14/6-facts-about-marijuana/) as more states decriminalize and legalize the drug. As such, how have the words associated with marijuana in news articles changed over time?

## Methodology

I developed a two-step approach to to try to answer this question. First, I wanted to identify distinct eras characterized by the use of key words associated with marijuana. Second, I aimed to assess whether words in each era represented larger themes regarding the public's view toards marijuana and the the drug's legality. I summarize the methodology I used below.

![Summary of methodology]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-methodology.png){: .center-image }

## Analysis

I performed [TF-IDF](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) on articles grouped into 5-year chunks of text in order to identify the most important words in each 5-year chunk. The resulting feature set was 1.1 million n-grams, or 1.1 million dimensions(!). To avoid the [curse of dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality) that occurs when one attempts to cluster higher dimensional datasets, I conducted a [principal component analysis (PCA)](https://en.wikipedia.org/wiki/Principal_component_analysis) to reduce the dimensionality of the feature set. 

The PCA results are shown below as a chart showing the number of components versus explained variance. Because there was more than one elbow (as shown in the figure), I decided to compute the cosine similarities at each elbow to see which set of components yielded the best, most intelligible clusters.

![PCA results]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-pca.png){: .center-image }

I visualized clusters using color-coded cosine similarity matrices provided below. The color of each square represents the relatedness between two five-year text chunks. As you can see, two components resulted in over-clustering while clusters did not really form using twelve components. Nine components yielded the most intelligible clusters.

![Cosine similarity matrices]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-cosine.png){: .center-image }

Next, I wanted to overlay the top twenty words from each cluster and public sentiment regarding legalizing marijuana. The first cluster ranged from 1965 to the late 1970s, a time when awareness and use of marijuana rapidly increased. Key words from this period were related to crime and enforcement of marijuana laws. The second cluster overlapped with the Reagan administration, and included new terms such as cocaine, a drug that became more popular in the 1980s. The third cluster more or less spanned the George HW Bush and Clinton administrations, and was the first time that medical popped into a cluster's top twenty list. During this time, California, Oregon, Main, Nevada, and Colorado legalized medical marijuana. The fourth cluster occurred around 2005, and included words that don't seem related to marijuana, including 'theater' and 'art'. The fifth cluster ranged from the late 2000s to the present, and included key terms like recreational marijuana. During this time, multiple states have decided to decriminalize and legalize recreational marijuana consumption as Americans have become more supportive of legalizing recreational use of the drug. 

![Key words and sentiment on legalization]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-sentiment.png){: .center-image }

## Conclusions

In sum, the pre-processing and clustering approach I used succeeded in identifying two intelligible clusters. For the latter half of the 20th century, words associated with marijuana tended to relate to crime, enforcement, and prevention. In the 90s and 2000s, stories on marijuana shifted toward decriminalization, legalization, and recreational marijuana use as public support for legalization increased. Check out my code on [Github](https://github.com/pgr-me/metis_projects/tree/master/04-marijuana) to see the full analysis!