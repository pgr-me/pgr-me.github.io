---
layout: post
title: Marijuana through the lens of the New York Times
published: true
---

The legality of and public's view towards marijuana is rapidly [changing](http://www.pewresearch.org/fact-tank/2015/04/14/6-facts-about-marijuana/) as more states decriminalize and legalize the drug. As such, how have the words associated with marijuana in news articles changed over time?

## Methodology

I developed a two-step approach to to try to answer this question. First, I wanted to identify distinct eras characterized by the use of key words associated with marijuana. Second, I aimed to assess whether words in each era represented larger themes regarding the public's view toards marijuana and the the drug's legality. I summarize the methodology I used below.

![Summary of methodology]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-methodology.png)

## Analysis

I performed [TF-IDF](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) on articles grouped into 5-year chunks of text in order to identify the most important words in each 5-year chunk. The resulting feature set was 1.1 million n-grams, or 1.1 million dimensions(!). To avoid the [curse of dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality) that occurs when one attempts to cluster higher dimensional datasets, I conducted a [principal component analysis (PCA)](https://en.wikipedia.org/wiki/Principal_component_analysis) to reduce the dimensionality of the feature set. The PCA results are below. I found that two components yielded the most intelligible clusters, and so used two dimensions to carry out the rest of the analysis.

![PCA results]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-pca.png)

The next step of the analysis was to use the top two PCA dimensions to perform the cluster analysis. I generated a cosine similarity matrix to map the relatedness of the terms within each 5-year text chunk to one another. From that, I was able to identify two intelligible clusters. 

The first intelligible cluster ranged from about 1970 to 1990. Key words included paraquat, a herbicide used to eradicate illicit marijuana crops, Noriega, a corrupt Panamanian general involved in the drug trade, and terms related to enforcement of marijuana laws. These terms make sense given the historical context, when the federal and state governments adopted increasingly strict enforcement policies to limit marijuana consumption and trafficking. Public sentiment on legalizing marijuana correlated with these policies, as the vast majority of Americans opposed legalization. 

The second intelligible cluster ranged from the late 2000s to the present, and included key terms like recreational marijuana. During this time, multiple states have decided to decriminalize and legalize recreational marijuana consumption as Americans have become more supportive of legalizing recreational use of the drug.

I was not able to identify any clusters from about 1990 up through the late 2000s, which was perhaps due to an issue with [stop words](https://en.wikipedia.org/wiki/Stop_words) that I did not catch earlier in the analysis.

The figure below overlays key words from the two clusters I identified and public sentiment on legalizing marijuana.

![Key words and sentiment on legalization]({{site.baseurl}}/pgr-me.github.io/images/004-marijuana-sentiment.png)

## Conclusions

In sum, the pre-processing and clustering approach I used succeeded in identifying two intelligible clusters. Words associated with marijuana from 1990 to 1970 were related to crime, enforcement, prevention. Then, stories on marijuana shifted toward decriminalization, legalization, and recreational marijuana use as public support for legalization increased. Check out my code on [Github](https://github.com/pgr-me/metis_projects/tree/master/fletcher) to see the full analysis!