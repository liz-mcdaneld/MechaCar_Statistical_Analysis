# MechaCar Statistical Analysis

## Purpose

AutosRU’s is producing a new prototype of vehicle, the MechaCar, but they are suffering from production troubles. Management has requested the data analytics team to review production data for insights that may help the manufacturing team progress through the production process. 

## Overview

•	Load, clean, and reshape datasets using tidyverse in R.

•	Form null and alternative hypothesis.

•	Evaluate simple linear regression and multiple linear regression models.

•	Implement and evaluate one-sample t-Test, two-sample t-Test, and ANOVA (analysis of variance) models.

•	Identify key characteristics of A/A and A/B testing.

•	Determine the appropriate statistical test for a hypothesis and dataset. 

## Linear Regression to Predict MPG

The MechaCar dataset contains a sample size of 50 prototypes measuring the MPG (mile per gallon) across multiple variables. The linear regression is calculated using R in RStudio and using the dplyr library.
R script was applied to the dataset on several variables to get the following:

![linear_regression_mechacar_mpg](https://user-images.githubusercontent.com/103263248/186195663-b92bcb05-3f94-4aa0-a0fa-63e6b4f4296a.png)

### Summary of Linear Regression to Predict MPG

A summary of the linear regression is displayed to determine the quality of the dataset. In this summary the distribution of the residuals the dataset fits in with the normal parameters. The value of the minimum and maximum are comparable at -19.4701 and 18.5849. The median is close to zero at -0.0692.

![summary_stat_mechacar_mpg](https://user-images.githubusercontent.com/103263248/186195715-c22b3a8a-c427-4986-80bc-19dce8725595.png)

#### Addressing the following questions:

##### Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?

The predetermined level of confidence was 95%. This means the p-value should be compared to alpha = 0.05 level of significance to verify the statistical significance.

###### Coefficients:
mpg: 0 < .05, statistically significant, non-random amount of variance
vehicle length: 0 < .05, statistically significant, non-random amount of variance
vehicle weight: .08 > .05 not statistically significant, random amount of variance
spoiler angle: .31 > .05 not statistically significant, random amount of variance
ground clearance: 0 > .05 statistically significant, non-random amount of variance
AWD: .19>=.05 not statistically significant, random amount of variance
In summary, vehicle length and ground clearance variables represent non-random amounts of variance as applied to the mpg values.

##### Is the slope of the linear model considered to be zero? Why or why not?

###### Coefficients:
vehicle length: 6.267
vehicle weight: .001
spoiler angle: .069
ground clearance: 3.546
AWD: -3.411
The multiple linear regression formula for MPG is: mpg = -.01 + 6.267(vehicle length)+.001(vehicle weight)+.069(spoiler angle)+3.546(ground clearance)-3.411(AWD), and results in a non-zero slope.

##### Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?

R-squared is 0.7149, this shows the dataset is an effective dataset being a strong correlation for the dataset. It is possible there may be other variables not included in the dataset contributing to the variation in the mpg. Further evaluation and test of other variables not included could provide answers to this question.

## Summary Statistics on Suspension Coils

### Manufacturing Lot Summary

The summary statistics of all the manufacturing lots is:

![total_summary](https://user-images.githubusercontent.com/103263248/186195818-305d0bb2-b69a-458c-acf5-6fdd8dd165d3.png)

### Summary by Manufacturing Lot

The summary for the individual manufacturing lots is:

![lot_summary](https://user-images.githubusercontent.com/103263248/186195826-eb1a9fd7-73f0-46cd-b81e-a868c8235571.png)

#### Addressing the following question:

##### The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

The variance of the suspension coils total is less than 100 psi at 62. When reviewing the individual Lots, Lot 3 is a large contributing factor to the variance with its variance being 170 which is exceeding the 10 -psi specification. Lot 1 has a low variance factor of 0.097 and Lot 2 has a low variance factor of 7.46, both below the 100 psi specification. 

## T-Tests on Suspension Coils

### t-Test for all Lots, pop mu = 1,500 psi

All Manufacturing Lots: p-value = 0.6028, alpha = 0.05
The total manufacturing lot is 0.60 > 0.05 and not statistically significant from the normal distribution. This means normality can be assumed. The mean falls within the 95% confidence interval.

![t-test_lots_popmu1500psi](https://user-images.githubusercontent.com/103263248/186195864-4e5094f5-41d4-4e91-b298-69303a74cf7b.png)

### t-Test for Lot 1 

Lot 1: p-value = 1, alpha = 0.05
Lot 1 is 1 > 0.05, and not statistically significant from the normal distribution. This means normality can be assumed. The mean falls within the 95% confidence interval.

![t-test_subset_lot1](https://user-images.githubusercontent.com/103263248/186195883-eb645e93-8ac2-478d-9d35-77a3c12b165f.png)

### t-Test for Lot 2

Lot 2: p-value = 0.6072, alpha = 0.05
Lot 2 is 0.60 > 0.05, and not statistically significant from the normal distribution. This means normality can be assumed. The mean falls within the 95% confidence interval.

![t-test_subset_lot2](https://user-images.githubusercontent.com/103263248/186195900-05b03343-5906-46ed-8b0d-f8bd7cd1499c.png)

### t-Test for Lot 3

Lot 3: p-value = 0.04168, alpha =0 .05
Lot 3 is 0.04 < 0.05, and it is statistically significant from the normal distribution. This means normality cannot be assumed. Although, the mean does fall within the 95% confidence interval.

![t-test_subset_lot3](https://user-images.githubusercontent.com/103263248/186195928-4f13cbc6-94e3-40ba-8edc-d93d01658704.png)

### Summary of t-Test

The Lot 1, Lot 2, and the overall manufacturing show a normal distribution. This means there is no sufficient evidence to reject the null hypothesis that shows the two means are statistically similar.

## Study Design: MechaCar vs Competition

Somparing MechaCar to the competition’s metrics could be of interest to the consumer. The metrics to compare could include cost, fuel efficiency, horsepower, maintence cost, safety ratings, or cosmetics.

#### What metric or metrics are you going to test?

The next metrics to test should be the safety rating, fuel efficiency and horsepower. These are import as they can all contribute to consumer safety concerns.

#### What is the null hypothesis or alternative hypothesis?

The alternative hypothesis is that the average, or mean, of the safety rating is not zero.
The null hypothesis is that the average, or mean, of the safety rating is zero.

#### What statistical test would you use to test the hypothesis? And why?

A multiple linear regression statistical summary to show how the variable affect the safety ratings for MechaCar compared to the competitors. 

#### What data is needed to run the statistical test?

Randoms samples for MechaCar and their competitor would need to be collected. This includes the safety ratings, fuel efficiency, and horsepower. The collected data will be run through RStudio for analysis. 
