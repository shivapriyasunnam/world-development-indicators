> 1\. Abstract

This report analyzes 30 years of economic development in 30 influential
countries using a World Bank dataset with 25 indicators. Rigorous
preprocessing includes attribute renaming, handling missing values, and
normalization using the Standard Scaler. A similarity matrix reveals
intriguing relationships, and Principal Component Analysis reduces
dimensionality. Novel indices---Social Development, Financial
Development, and Environmental Friendly---are introduced, providing
nuanced insights.

Graphs visually depict the new indices, and k-Means clustering
identifies optimal clusters. Hierarchical clustering refines groupings
using Ward and Weighted methods. The study compares continents and
aligns findings with major real-world events, such as China\'s economic
rise and Brexit. The implications of the results emphasize the role of
data analysis in predicting trends and guiding policy decisions. The
report aims to assist policymakers, researchers, and analysts in
navigating the complex landscape of economic trends over the past three
decades.

> 2\. Introduction

This report shows how different countries have been doing economically
for the past 30 years. We cleaned up the data, compared different
things, and made some new measures to understand development better. We
also used a special method to group countries based on how they\'re
growing. To make it more interesting, we looked at big events like China
geting powerful, the Great Recession, Brexit, and the pandemic to see
how our data matches up with real-world happenings. The goal is to help
everyone understand what\'s going on with countries and their
development.

> 3\. Dataset

The dataset is obtained from world bank where we selected top 30
countries which are influential and in the news during recent years.
Then, we selected 25 world development indicators which belong to
categories such as "Education", "Agriculture and Rural Development",
"Economy and Growth", etc, where 30 years for data is taken into
consideration. The type of dataset is panel data where it is
cross-sectional data.

> 4\. Data Preprocessing

![](./ahmz4zws.png){width="2.7869444444444444in"
height="0.40069444444444446in"}![](./mue1ww5h.png){width="2.789721128608924in"
height="0.37777668416447946in"}The preprocessing of the dataset starts
with renaming the attributes. For example, one column is in such way -
"Agricultural land (% of land area) \[AG.LND.AGRI.ZS\]" where
"Agricultural land (% of land area)" is the text we need. So, we slice
the attribute name to use the text we need so that it is easier in
visualization. The next step is to handle missing values. The attributes
consist of missing values and have been removed by using mean. We then
checked for duplicate values in the attributes. The attribute values
were in datatype string, and we required it to be float. So, we
converted all the strings to float wherever needed.

![](./ju4v0sbi.png){width="4.4863888888888885in"
height="3.439582239720035in"}

> Fig 4.1 Missing values per attributes before cleaning
>
> 5\. Normalization

The features that we have taken into consideration had values in
different ranges. For example, the attribute 'Current account balance
(BoP, current US\$)' has values in the form of -2246921171, 6048537893
whereas the attribute 'Unemployment, total (% of total labor force)' has
values in the form 8.082, 22.61 and so on. Comparing values with
different ranges is possible only when we perform normalization of the
dataset. Normalization is a statistical technique used in data
preprocessing to scale and standardize the values of different features
within a dataset. We tried three different normalization techniques and
chose one technique based on our use case. The following are the
techniques that we applied --

> 5.1 Standard Scaler or Z-Score Normalization --
>
> This Scaler scales the features by removing the mean and scaling to
> unit variance. It transforms the data distribution to have a mean of 0
> and a standard deviation of 1.
>
> 5.2 MinMax Scaler --
>
> MinMaxScaler scales the features to a specified range, typically
> between 0 and 1. It shifts and scales the data, preserving the shape
> of the original distribution.
>
> 5.3 MaxAbs Scaler
>
> MaxAbsScaler scales each feature by its maximum absolute value. It
> does not shift or center the data and is mainly used to scale sparse
> data.

We have chosen the Standard Scaler to proceed further with our analysis.

> 6\. Similarity Matrix

![](./la0h2rmy.png){width="6.5in" height="5.466666666666667in"}

We proceeded to compare the similarity of one feature to another using
the similarity matrix. We used the cosine similarity to visualize the
matrix. If the box is closer to the color green, then the attributes
corresponding to the box are more similar to each other.

Some observation from the Similarity Matrix --

> a\) Urban Population is -0.90 units dissimilar to employment in
> agriculture b) Control in Corruption is 0.87 units similar to GDP per
> capita
>
> c\) Net Migration is -0.66 units dissimilar to Current Account Balance
>
> 7\. Dimensionality Reduction

The number of features we've chosen were 25 and the number of countries
we've chosen were 30, this results in a highly dimensional dataset. We
have performed Principal Component Analysis to reduce the dimensions to
two and then perform the next few operations.

> 7.1 Principal Component Analysis

![](./y5ce4zdu.png){width="6.5in" height="2.8625in"}

> PCA begins by centering the data, which involves subtracting the mean
> of each feature from the data points. The next step is to compute the
> covariance matrix. The covariance matrix provides information about
> how much two variables change together. The eigenvectors and
> eigenvalues of the covariance matrix are then calculated. The selected
> eigenvectors are then used to create a projection matrix. This matrix
> is used to transform the original high-dimensional data into a
> lower-dimensional space.
>
> Input Data: 30 X 25 Dimensional Data
>
> Output Data: 2 X 2 Dimensional Data
>
> **8.** **Feature** **Creation**

Feature creation is also known as feature engineering, is the process of
transforming raw data into a new format that enhances the performance of
the analysis and evaluation models. The features we created were as
follows:

> **8.1** **Social** **Development** **Index** **(SDI)**
>
> This is a combination of the following attributes - Access to
> electricity (% of population), Life expectancy at birth, total
> (years) - Military expenditure (% of GDP)
>
> **8.2** **Financial** **Development** **Index** **(FDI)**
>
> This is a combination of the following attributes - GDP per capita
> (current US\$), Current account balance (BoP, current US\$), Total
> reserves (includes gold, current US\$)
>
> **8.3** **Environmental** **Friendly** **Index** **(EFI)**
>
> This is a combination of the following attributes - Forest area (% of
> land area), CO2 emissions (metric tons per capita), Urban population
> (% of total population)
>
> **9.** **Comparing** **new** **features** **with** **Graphs**

We plotted graphs to compare the new features and following are the
results --

> Social Development Index

![](./qh5uk3qm.png){width="6.5in"
height="2.9402777777777778in"}![](./idxxe03t.png){width="6.5in"
height="2.8993055555555554in"}

> Financial Development Index
>
> Environmental Friendly Index
>
> **10.** **Clustering**

We performed k-Means Clustering for the resultant data after
dimensionality reduction, the k-Means algorithm first randomly chooses K
cluster centroids, assigns each data point to the nearest centroid,
recalculated centroids based on assigned data points. Iterate through
these steps until convergence (cluster assignments stabilize) and
finally, each data point is assigned to a cluster, and clusters are
represented by their centroids.

> **11.** **Clustering** **with** **k** **=** **2,3,4,5**

![](./tu40eer3.png){width="6.5in"
height="4.149305555555555in"}![](./fcnn3vki.png){width="6.345972222222223in"
height="4.254026684164479in"}

![](./iysy2rmx.png){width="6.5in"
height="4.163194444444445in"}![](./othi2cwi.png){width="6.433887795275591in"
height="4.211111111111111in"}

> **12.** **Identifying** **Cluster** **Validity**

![](./mlihuxla.png){width="2.894860017497813in"
height="0.8465277777777778in"}![](./wfk1sxu4.png){width="3.174304461942257in"
height="2.333193350831146in"}

> Identifying cluster validity is crucial in assessing the quality of a
> clustering solution. The Sum of Squared Error (SSE) is a common metric
> used for this purpose in the context of K-means clustering. SSE
> measures the sum of squared distances between each data point and its
> assigned cluster centroid. A lower SSE indicates tighter and more
> cohesive clusters. The elbow method is a visual technique to determine
> the optimal number of clusters (K). It involves ploting the SSE for
> different values of K and looking for the \"elbow\" point where the
> rate of SSE reduction sharply decreases.
>
> **13.** **Hierarchal** **Clustering**

Hierarchical clustering is a method of grouping data into a tree-like
structure of clusters, where each observation starts in its own cluster,
and clusters are successively merged or split based on similarity.

> **13.1** **Ward** **Method**
>
> The Ward linkage method and weighted method are two approaches within
> hierarchical clustering. Ward linkage minimizes the sum of squared
> differences within all clusters, making it sensitive to cluster
> compactness. This method tends to create more equally sized and
> spherical clusters.

![](./lf4pdaw0.png){width="6.5in" height="4.024305555555555in"}

> **13.2** **Weighted** **Method**
>
> ![](./haxl5juo.png){width="5.675694444444445in"
> height="3.7534722222222223in"}The weighted method assigns weights to
> observations, influencing the merging or spliting process. Weights can
> be used to emphasize the importance of specific data points in the
> clustering process, giving more influence to certain observations
> during the formation of clusters.

![](./kdk2rd4i.png){width="5.0in"
height="3.28125in"}![](./l4e5sduc.png){width="4.155972222222222in"
height="2.7013877952755907in"}

> **14.** **Results**
>
> **14.1** **Comparing** **Continents**

Let's look at the total reserves including gold, comparing the
continents.

> **14.2** **Graphs** **for** **Real** **Time** **World** **Events**

We took into consideration some major events that occurred in the past
30 years.

14.2.1 China's Economic Rise (Early 2000s)

We can see the significant growth of GDP of China from the year 2000 due
to various factors.

14.2.2 Brexit (2016 -- 2020)

![](./jehgrjyc.png){width="3.2181944444444444in"
height="2.058333333333333in"}![](./caouvzts.png){width="3.394860017497813in"
height="2.185416666666667in"}

The term Brexit refers to withdrawal of United Kingdom from the European
Union. It started from 2016 but the actual effect started from 2012
where there were talks going on about Brexit by the then Prime Minister
of UK. The current account balance over the years shows us the same.

14.2.3. The Great Recession (2007 -- 2009)

This is the period where the trade and economy of the major countries
have been disrupted leading to a financial crisis.

14.2.4. The Pandemic (2019 -- 2021)

![](./x3guynb2.png){width="2.676388888888889in"
height="1.7416666666666667in"}A pandemic is an epidemic occurring on a
scale that crosses international boundaries. During 2019 to 2021 the
world was hit with a pandemic making the GDP of major countries fall. We
see the rise in inflation rate and fall in trade leading to a disastrous
situation.

> **15.** **Discussion**

In this project we implemented thorough data preprocessing,
normalization, and dimensionality reduction lay a robust foundation for
the subsequent analyses. By employing techniques such as Principal
Component Analysis (PCA) and introducing novel indices, the study
effectively distills complex economic data into meaningful insights. The
clustering methodologies, including k-Means clustering and hierarchical
clustering, provide a nuanced understanding of the relationships between
influential countries, facilitating the identification of distinct
economic patterns. The integration of real-world events, such as
China\'s economic rise, Brexit, the Great Recession, and the recent
pandemic, enhances the contextualization of economic indicators,
offering a comprehensive view of global economic development.

> **16.** **Link** **to** **Github** **17.** **Conclusion**

Our analysis of three decades of World Bank data spanning 30 countries
and 25 indicators shows uncovered intricate patterns in global economic
development. Data cleaning, preprocessing and feature creation gave a
good view of societal progress. Real-world case studies from China's
rise to the recent pandemic anchored our findings in global events.

The analysis of such data has important implications to the patterns of
future. The patterns and events of the past gives the data that we need
to predict the future when the same pattern occurs again. Other than
that, it also helps in analysing if the countries are having a growth in
GDP, having a high inflation rate so that they can take necessary
countermeasures.

> 18\. References
>
> •
> [[https://databank.worldbank.org/source/world-development-indicators]{.underline}](https://databank.worldbank.org/source/world-development-indicators) •
> https://datatopics.worldbank.org/world-development-indicators/
>
> • Nielsen, Frank, and Frank Nielsen. \"Hierarchical clustering.\"
> *Introduction* *to* *HPC* *with* *MPI* *for* *Data* *Science* (2016):
> 195-211.
>
> • Humaira, Hestry, and R. Rasyidah. \"Determining the appropiate
> cluster number using Elbow method for K-Means algorithm.\"
> *Proceedings* *of* *the* *2nd* *Workshop* *on* *Multidisciplinary*
> *and* *Applications* *(WMA)* *2018,* *24-25* *January* *2018,*
> *Padang,* *Indonesia*. 2020.
>
> •
> [[https://towardsdatascience.com/what-is-feature-engineering-importance-tools-and-techniques-for-machine-learning-2080b0269f10]{.underline}](https://towardsdatascience.com/what-is-feature-engineering-importance-tools-and-techniques-for-machine-learning-2080b0269f10)
>
> • Sitikhu, Pinky, et al. \"A comparison of semantic similarity methods
> for maximum human interpretability.\" *2019* *artificial*
> *intelligence* *for* *transforming* *business* *and* *society*
> *(AITB)*. Vol. 1. IEEE, 2019.
>
> •
> [[https://www.w3schools.com/python/pandas/pandas_cleaning.asp]{.underline}](https://www.w3schools.com/python/pandas/pandas_cleaning.asp)
