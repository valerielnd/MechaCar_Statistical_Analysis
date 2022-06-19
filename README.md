# MechaCar_Statistical_Analysis

As AutosRUs newest prototype, the MechaCar, is suffering from production troubles 
that are blocking the manufacturing team’s progress; we will perform several statistical
analyses tests Using R, a programming language for statistical computing and graphic, 
to review the production data for insights that may help the manufacturing team.

To proceed, we will use two data sets:

* 	MechaCar MPG dataset which contains mpg test results for 50 prototype MechaCars. 
	In this data set, multiple metrics, such as vehicle length, vehicle weight, 
	spoiler angle, drivetrain, and ground clearance were collected for each vehicle.
	
	
*	Suspension Coil dataset, which contains  the weight capacities of multiple suspension 
	coils from multiple production lots.

	
## Linear Regression to Predict MPG

Using R, we designed a linear model to predict the mpg of MechaCar prototypes.

In the MechaCar MPG dataset, as five other metrics, in addition to the 
vehicles MPG were collected, we performed a multiple linear regression to find
which ones account for the variability observed in the MPG of MechaCar prototypes.

We performed the multiple linear regression using the following steps:

*	First, we imported and read the MechaCar_mpg.csv file as a data frame.

* 	We performed a multiple linear regression using the lm() function with the formula:
	mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance
	
* 	We obtained the statistical metrics of our mutilple multiple linear regression model
	using the summary() function:
	summary(lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD, data=MechaCar))
	
We obtained the following results:

![result_mlr](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/mpg_MLR.png)

According to the results, the vehicle length and ground clearance as well
as the intercept has a significant impact on the MPG. 

In addition, the p-value of our linear regression analysis is 5.35 x 10-11, much 
smaller than our assumed significance level of 0.05%. Therefore, we can state that there 
is sufficient evidence to reject our null hypothesis, which means that the coefficients of our linear 
model all zero.

Even though we have only two significant variables, having an r-squared value of 0.71,
we can say that our linear model explains roughly 71% of the variability in the MPG of MechaCar prototypes.

However, as the intercept is statistically significant, it explains a significant 
amount of variability in the MPG when the five other variables
in our model are null. This could mean that the vehicle length and ground clearance
may need to be scaled or transformed to help improve the predictive power of our model
or other variables could explain the variability of the MPG.

Although our multiple variables linear model seems to be a good model to predict the the MPG of MechaCar prototypes,
the lack of significant variables might also be evidence of overfitting. At this point,
we could try to generate simple and multiple regressions with the vehicle's length and ground
clearance to create more accurate predictive models.


## Summary Statistics on Suspension Coils

Using the MechaCar Suspension_Coil.csv dataset, we created two summary statistics tables to 
determine if the manufacturing process is consistent across production lots.

In the first table, we computed the mean, median, variance, and standard deviation of the 
suspension coil’s PSI continuous variable across all manufacturing lots:

![suspension_coil_total](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/suspension_coil_total.png)

As the mean is 1498.78 and the median is 1500, the distribution of the suspension coil’s PSI continuous variable 
across all manufacturing lots should be approximately normal where values farther from the mean occur less 
frequently. 

![normality](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/normality.png)

However, as the standard deviation is approximately 7.9 and the variance is 62.29, which does not exceed
the design specification of 100 pounds, the data set has some variability, and we need to investigate more.

Since there is some variability in the data set, to determine in which production lot the manufacturing process is
less consistent, and where the design specification is not met, we computed the same PSI metrics for each lot
in a second table:

![psi_per_lot](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/psi_per_lot.png)

In this table, as the mean and the median in lot one and lot 2 are equal, the distribution of 
The suspension coil’s PSI for them is normal.

In those lots, the standard deviation is not significant, between 1 and 2.7, and the variance does not
exceed the design specification of 100 pounds. In addition, the manufacturing process for those lots is somewhat 
consistent.

As for lot 3, since the standard deviation is 13 and the variance exceeds 100 pounds, the manufacturing process in this 
lot is a bit inconsistent.


## T-Tests on Suspension Coils

Using the MechaCar Suspension_Coil.csv dataset, we decided to perform t-tests to determine if the mean of all 
manufacturing lots and each lot individually is statistically different from the population mean 
of 1,500 pounds per square inch.

First, we performed a one-sample t-test to determine if the mean of all manufacturing lots is 
statistically different from the population mean of 1,500 pounds per square inch.

![all_lot](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/comp_all_lots.png)

As the p-value obtained is 0.06% and greater than our assumed significance level of 0.05%, we 
fail to reject the null hypothesis, and we would state that the two means are statistically similar.

Then we performed another one-sample t-test to determine if the mean of manufacturing lot1 is 
statistically different from the population mean of 1,500 pounds per square inch.

![lot1](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/comp_lot1.png)

As the p-value obtained is 1% and greater than our assumed significance level of 0.05%, we 
fail to reject the null hypothesis, and we would state that the two means are statistically similar.

Then we performed another one-sample t-test to determine if the mean of manufacturing lot2 is 
statistically different from the population mean of 1,500 pounds per square inch.

![lot2](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/comp_lot2.png)

As the p-value obtained is 0.6 and greater than our assumed significance level of 0.05%, we 
fail to reject the null hypothesis, and we would state that the two means are statistically similar.

Finally, we performed another one-sample t-test to determine if the mean of manufacturing lot3 is 
statistically different from the population mean of 1,500 pounds per square inch.

![lot3](https://github.com/valerielnd/MechaCar_Statistical_Analysis/blob/main/comp_lot3.png)

As the p-value obtained is 0.04 and less than our assumed significance level of 0.05%, we 
reject the null hypothesis and we could state that the two means are statistically different.

## Study Design: MechaCar vs Competition

As fuel price is constantly increasing, one study that we could do to compare MechaCar 
performance against the competition is to find which metrics possibly affect their highway fuel efficiency
versus the competition. Knowing this information, customers with, for example, a specific budget 
and looking for particular specifications will be able to determine how much they can expect to spend on fuel.

To conduct this statistical study, we will need to collect the following data on MechaCar and its comparable models: 

* highway fuel efficiency
* vehicle weight
* horsepower
* MPG
* cost
* Acceleration
* Number of cylinders

To determine if there is a relationship between the multiple independent variables: weight, horsepower, MPG, cost 
Acceleration, number of cylinders and the dependent variale : highway fuel efficiency, and if, 
in addition, we can use a linear model to predict the value of the dependent variable,
we will perform Multiple linear regression.

The null hypothesis: The coefficients of the linear model are equal to zero
The alternative hypothesis: not every coefficient is simultaneously equal to zero

Hence, we will generate a multiple linear regression model to determine if there is a significant relationship 
with the dependent variable and evaluate the r-squared value of the model to determine if the model sufficiently 
predicts our dependent variable.





 
