# Anomaly-Detection-with-GESD
Anomaly detection plays a very important role in a wide variety of use cases. Typically, anomalous data can be connected to some kind of problem or rare event such as e.g. bank fraud, medical problems, structural defects, malfunctioning equipment, etc. This connection makes it very interesting to be able to pick out which data points can be considered anomalies, as identifying these events are typically very interesting from a business perspective.

Also, many statistical techniques are sensitive to the presence of outliers. For example, simple calculations of the mean and standard deviation may be distorted by a single grossly inaccurate data point. Checking for outliers should be a routine part of any data analysis and potential outliers should be examined to see if they are possibly erroneous

## What is Anomaly Detection?
Anomaly detection is any process that finds the outliers of a dataset; those items that don’t belong. These anomalies might point to unusual network traffic, uncover a sensor on the fritz, or simply identify data for cleaning, before analysis.
There are various techniques that can be used to identify anomalies based on different schemes or approaches like graphical (box plots, scatter plots), distance-based schemes(nearest neighbor, clustering algorithms), statistical approaches (GESD, quartile-based techniques), etc. Each scheme has its pros and cons and the efficacy depends on the use case.

## What is GESD?
GESD is a simple statistical approach used to detect one or more outliers in a univariate data set that follows an approximately normal distribution. Statistical approaches assume that regular data follow some statistical model and the data not following the model are outliers.
GESD overcomes the primary limitation of the Grubbs test and the Tietjen-Moore test that the suspected number of outliers, k, must be specified exactly. If k is not specified correctly, this can distort the conclusions of these tests. The GESD test only requires that an upper bound for the suspected number of outliers be specified.
Given the upper bound, r, the generalized ESD test essentially performs r separate tests: a test for one outlier, a test for two outliers, and so on up to r outliers.

The generalized ESD test is defined for the hypothesis:
H0: There are no outliers in the data set
Ha: There are up to r outliers in the data set
Our test statistic is given by the formula below:

![image](https://user-images.githubusercontent.com/30365732/113633415-893dec00-9632-11eb-8344-db39aa4607d4.png)


Test statistic for GESD
Here, x_bar and σ denote sample mean and sample standard deviation, respectively.
In GESD we remove the observation that maximizes |xi — x_bar| and then recompute the above statistic with n-1 observations. We repeat this process until r observations have been removed. This results in the r statistics R1, R2 ………., Rr. This process will become more clear with the coding example.
Corresponding to the r test statistics, compute the following r critical values:

Critical Value calculation
where tp,ν is the 100p percentage point from the t distribution with ν degrees of freedom and

Our Significance level will be denoted by α.
The number of outliers is determined by finding the largest i such that Ri > λi.
Simulation studies by Rosner indicate that this critical value approximation is very accurate for n ≥ 25 and reasonably accurate for n ≥ 15.
Note that although the generalized ESD is essentially Grubbs test applied sequentially, there are a few important distinctions:
The generalized ESD test makes appropriate adjustments for the critical values based on the number of outliers being tested for that the sequential application of Grubbs test does not.
If there is significant masking, applying the Grubbs test sequentially may stop too soon.
