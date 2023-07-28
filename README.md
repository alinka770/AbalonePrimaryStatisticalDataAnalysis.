# Abalone_Primary_statistical_data_analysis.
The goal of the work is to study the methods of primary statistical data analysis, master the capabilities of Python libraries for conducting such analysis, and acquire skills in implementing these methods independently.

To use this project, you need to move the file "abalone.csv" to the path "D:\abalone.csv"


This project consists from 2 parts: 

First part of the project:

I downloaded this dataset into a DataFrame and conducted its primary statistical data analysis, during which:
1. Displayed the first and last few rows of the dataset to ensure it was loaded without errors.
2. Analyzed the data type of each indicator in the dataset.
3. Displayed and analyzed the statistical characteristics of each indicator. For quantitative indicators, these were the minimum, maximum, mean, median, and standard deviation. For qualitative indicators, the total number of values, the number of unique values, the mode value, and its frequency were considered.
4. Checked for missing values in the data. If any were found, I either removed all rows with missing values or filled the gaps with the mean/median/mode of the corresponding column.
5. For each indicator that can be considered as a discrete random variable, I plotted the probability function graph.
6. For each indicator that can be considered as a continuous random variable, I performed the identification of a normal distribution. For this purpose:
   - I calculated the skewness and kurtosis coefficients for the indicator and tested the hypotheses about their equality to zero (whether both coefficients confirm the hypothesis of equality to zero).
   - I constructed a histogram and kernel density estimation (KDE) of the probability density function (PDF) to determine whether a normal distribution is indicated or if any other distribution is identified. I also checked whether the data is homogeneous.
   - I constructed a normal probability plot and displayed the sample data on it to check if the data points lie on a straight line, suggesting a normal distribution.
7. For each indicator that showed a distribution different from normal according to the results of the previous step, I performed log transformation and Box-Cox transformation to check if a normal distribution is indicated after the transformation.
8. For each indicator that can be considered as a continuous random variable, I conducted a search for outliers using one of the methods discussed in the lecture. If anomalies were found, I replaced them with NaN. After conducting the outlier search for all indicators, I formed a new dataset without NaN values. I considered two options for forming the new dataset: 1) removing all rows with missing values (NaN), 2) replacing NaN values with the mean/median of the corresponding column.

Second part of the project:

I wrote custom functions for conducting primary statistical data analysis on the given indicator `x`. The implemented functions are as follows:

1. `describe(x, DI=False)` - calculates and displays the statistical characteristics (minimum, maximum, mean, median, standard deviation, skewness, and kurtosis) of the indicator `x` in a table format. If `DI=True`, it also shows confidence intervals for the characteristics.

2. `histogram(x, bins=None, normed="frequency")` - constructs a histogram for the given indicator `x`. It takes three arguments: `x` - the indicator, `bins` - the number of bins (classes), and `normed` - which can take one of three values: "frequency," "probability," or "density." If the user provides something else, they will see the message "Invalid value for the 'normed' argument," and the histogram will be constructed with the default parameter. The type of histogram is determined based on the value of `normed`.

3. `kde(x, h=None)` - constructs a graph of kernel density estimation with a Gaussian kernel for the given indicator `x`. It takes two arguments: `x` - the indicator and `h` - the bandwidth (window width). If the user provides something else, they will see the message "Invalid value for the 'h' parameter," and the graph will be constructed with the default parameter. If `h=None`, the bandwidth will be determined using Silverman's or Scott's rule.

4. `normal_paper(x)` - constructs a normal probability plot for a normal distribution and displays the data of the indicator `x` on it.

5. `outliers(x, alpha=0.05)` - searches for outlier values in the indicator `x` using one of the methods discussed in the lecture (any method of choice). It returns the found outlier values and also constructs a graph where the values of the indicator are plotted on the ordinate axis, and their indices are plotted on the abscissa axis. Anomalous values are marked in red on the graph, while non-anomalous values are marked in black. The parameter `alpha` determines the probability that a value is considered an outlier, and by default, it is set to 0.05.

I compared the performance of my custom functions with the functions used from Python libraries.
