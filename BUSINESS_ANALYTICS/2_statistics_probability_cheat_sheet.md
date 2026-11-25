# STATISTICS & PROBABILITY CHEAT SHEET

# 2. STATISTICS & PROBABILITY

## Measures of Central Tendency

MEAN:
The arithmetic average of a dataset.

Mean = Sum of Values / Number of Values

Example:
Values: 10, 20, 30, 40, 50

Mean = 150 / 5 = 30

MEDIAN:
The middle value when data is sorted.

Example:
10, 20, 30, 40, 50

Median = 30

For an even number of values:
Average the two middle values.

MODE:
The most frequently occurring value.

Example:
10, 20, 20, 30, 40

Mode = 20

WHEN TO USE:
- Mean: General average when extreme values aren't distorting it.
- Median: Better when data contains outliers or is skewed.
- Mode: Identify the most common value.

IMPORTANT:
The mean is sensitive to extreme values.
The median is generally more resistant to outliers.

---

## Measures of Dispersion (Spread)

RANGE:
Difference between the maximum and minimum values.

Range = Maximum - Minimum

VARIANCE:
Measures how spread out values are around the mean.

Population Variance:
σ² = Σ(x - μ)² / N

Sample Variance:
s² = Σ(x - x̄)² / (n - 1)

STANDARD DEVIATION:
Square root of variance.

Population:
σ = √σ²

Sample:
s = √s²

IMPORTANT:
- Low standard deviation = Values are relatively close together.
- High standard deviation = Values are more spread out.
- Standard deviation uses the same units as the original data.
- Sample variance uses n - 1 to account for estimating the population mean.

Example:
Dataset A: 48, 49, 50, 51, 52
Dataset B: 10, 30, 50, 70, 90

Both have a mean of 50, but Dataset B has much greater spread.

---

## Percentiles & Quartiles

PERCENTILE:
The value below which a specified percentage of observations falls.

QUARTILES:
Divide sorted data into four sections.

- Q1 = 25th percentile.
- Q2 = 50th percentile (Median).
- Q3 = 75th percentile.

INTERQUARTILE RANGE (IQR):
Measures the spread of the middle 50% of data.

IQR = Q3 - Q1

Used to:
- Understand data distributions.
- Compare spread.
- Identify potential outliers.

---

## Outliers

Outliers are unusually high or low observations.

Common IQR method:

Lower Fence = Q1 - 1.5 × IQR

Upper Fence = Q3 + 1.5 × IQR

Values outside these fences are potential outliers.

IMPORTANT:
- Outliers aren't automatically errors.
- Investigate their source.
- They may represent genuine unusual events.
- Removing them can distort analysis.

---

## Probability

Probability measures how likely an event is to occur.

Probability =
Favorable Outcomes / Total Equally Likely Outcomes

Probability ranges from 0 to 1.

- 0 = Impossible.
- 0.5 = 50% chance.
- 1 = Certain.

Example:
Rolling a six-sided die:

Probability of rolling a 6 = 1/6

IMPORTANT:
The simple formula assumes equally likely outcomes.

### Basic Probability Rules

COMPLEMENT:
Probability an event does NOT happen.

P(Not A) = 1 - P(A)

ADDITION RULE:
Probability of A or B.

P(A or B) = P(A) + P(B) - P(A and B)

For mutually exclusive events:

P(A or B) = P(A) + P(B)

MULTIPLICATION RULE:
Probability of A and B.

For independent events:

P(A and B) = P(A) × P(B)

CONDITIONAL PROBABILITY:
Probability of A given B has occurred.

P(A | B) = P(A and B) / P(B)

IMPORTANT:
Independence means one event does not change the probability of the other.

---

## Common Probability Distributions

NORMAL DISTRIBUTION:
A symmetrical, bell-shaped distribution.

Characteristics:
- Mean = Median = Mode.
- Symmetrical around the mean.
- Most observations are near the center.

68-95-99.7 RULE:
Approximately:
- 68% of values fall within 1 standard deviation.
- 95% fall within 2 standard deviations.
- 99.7% fall within 3 standard deviations.

BINOMIAL DISTRIBUTION:
Models the number of successes in a fixed number of independent trials with the same success probability.

Example:
Number of customers who purchase out of 100 visitors.

POISSON DISTRIBUTION:
Models the number of events occurring in a fixed interval when events happen at a constant average rate under suitable assumptions.

Example:
Number of customer support calls per hour.

UNIFORM DISTRIBUTION:
All outcomes in a defined range have equal probability (for a discrete uniform distribution).

SKEWED DISTRIBUTION:
Data is asymmetrical.

- Positive skew: Long tail to the right.
- Negative skew: Long tail to the left.

IMPORTANT:
Real business data is not always normally distributed.

---

## Correlation

Correlation measures the strength and direction of a linear relationship between two variables.

Correlation coefficient (r):
Ranges from -1 to +1.

- +1 = Perfect positive linear correlation.
- 0 = No linear correlation.
- -1 = Perfect negative linear correlation.

POSITIVE CORRELATION:
Both variables tend to increase together.

NEGATIVE CORRELATION:
One variable tends to decrease as the other increases.

NO LINEAR CORRELATION:
No linear relationship is detected.

IMPORTANT:
- Correlation does not imply causation.
- A correlation of zero doesn't rule out a nonlinear relationship.
- Outliers can strongly affect correlation.
- Correlation alone doesn't explain why variables are related.

Example:
Advertising spend and sales may have a positive correlation.

This doesn't automatically prove advertising caused higher sales.

---

## Regression

Regression models relationships between variables and can help predict outcomes.

SIMPLE LINEAR REGRESSION:

Y = a + bX

Where:
- Y = Predicted outcome (dependent variable).
- X = Predictor (independent variable).
- a = Intercept.
- b = Slope.

Example:
Predicting sales based on advertising spend.

SLOPE:
Expected change in Y for a one-unit increase in X.

INTERCEPT:
Predicted Y when X = 0.

R-SQUARED (R²):
Measures the proportion of variation in the outcome explained by the model.

Example:
R² = 0.80

The model explains 80% of the observed variation in the outcome in the fitted dataset.

IMPORTANT:
- High R² doesn't automatically mean a model is accurate.
- Correlation and regression do not establish causation.
- Check model assumptions and residuals.
- Avoid extrapolating beyond the data range without justification.

---

# 5. HYPOTHESIS TESTING & A/B TESTING

## Hypothesis Testing

A statistical method used to evaluate whether sample evidence supports a difference or effect.

NULL HYPOTHESIS (H0):
Assumes no effect or difference.

ALTERNATIVE HYPOTHESIS (H1):
Assumes an effect or difference exists.

Example:

H0: A new website design does not change conversion rate.

H1: A new website design changes conversion rate.

## P-Value

The probability, assuming the null hypothesis and statistical model assumptions are true, of observing results at least as extreme as those obtained.

COMMON SIGNIFICANCE LEVEL:
Alpha (α) = 0.05

If p-value < 0.05:
Reject the null hypothesis at the 5% significance level.

If p-value >= 0.05:
Fail to reject the null hypothesis.

IMPORTANT:
- A p-value is NOT the probability that the null hypothesis is true.
- Statistical significance does not necessarily mean business significance.
- A small p-value does not measure the size or importance of an effect.
- Failing to reject H0 does not prove H0 is true.

---

## Confidence Intervals

A confidence interval provides a range of plausible values for a population parameter based on sample data.

COMMON CONFIDENCE LEVEL:
95%

Interpretation:
A method that produces 95% confidence intervals will capture the true population parameter in approximately 95% of repeated samples, assuming the method's conditions are met.

IMPORTANT:
- Wider intervals indicate greater uncertainty.
- Larger samples often produce narrower intervals.
- More variability generally produces wider intervals.
- A confidence interval should be considered alongside practical business impact.

---

## Type I & Type II Errors

TYPE I ERROR:
Rejecting a true null hypothesis.

Also called:
False Positive.

TYPE II ERROR:
Failing to reject a false null hypothesis.

Also called:
False Negative.

STATISTICAL POWER:
Probability of correctly rejecting a false null hypothesis.

Higher power makes it more likely to detect a real effect.

---

## Sampling

A sample is a subset of a population used for analysis.

POPULATION:
The entire group being studied.

SAMPLE:
The selected observations from that population.

COMMON SAMPLING METHODS:

RANDOM SAMPLING:
Every population member has an equal chance of selection.

STRATIFIED SAMPLING:
Divide the population into groups and sample from each group.

SYSTEMATIC SAMPLING:
Select observations at regular intervals.

CONVENIENCE SAMPLING:
Use observations that are easiest to access.

IMPORTANT:
- A sample should represent the population.
- Biased samples can lead to misleading conclusions.
- Larger samples don't automatically eliminate sampling bias.

---

## A/B Testing

A/B testing compares two versions of something to determine which performs better.

Example:
- Group A sees the original website.
- Group B sees a redesigned website.

Possible metrics:
- Conversion Rate.
- Revenue Per Visitor.
- Click-Through Rate.
- Engagement.
- Customer Retention.

### A/B Testing Process

1. Identify the business problem.
2. Define a testable hypothesis.
3. Choose a primary success metric.
4. Randomly assign participants to groups.
5. Run the experiment.
6. Collect sufficient data.
7. Analyze the results.
8. Evaluate statistical and business significance.
9. Make a recommendation.

IMPORTANT:
- Randomization reduces selection bias.
- Use an adequate sample size.
- Avoid stopping tests early just because results look favorable.
- Change one main factor at a time when appropriate.
- Check for unintended effects on other metrics.
- Ensure groups are comparable.

---

# 6. STATISTICAL CONCEPTS TO REMEMBER

| Concept | What It Tells You |
|---|---|
| Mean | Average value |
| Median | Middle value |
| Mode | Most frequent value |
| Range | Overall spread |
| Variance | Average squared spread |
| Standard Deviation | Typical spread around mean |
| IQR | Spread of middle 50% |
| Percentile | Relative position in data |
| Probability | Likelihood of an event |
| Correlation | Strength and direction of linear relationship |
| Regression | Models relationships and predicts outcomes |
| P-value | Evidence against the null hypothesis |
| Confidence Interval | Range from a statistical estimation method |
| Sample | Subset of a population |
| Statistical Power | Ability to detect a real effect |

---

# 7. COMMON STATISTICS INTERVIEW QUESTIONS

Q: What is the difference between mean and median?

A: Mean is the arithmetic average. Median is the middle value in sorted data and is less affected by extreme values.

Q: When would you use median instead of mean?

A: When data contains significant outliers or is skewed, such as salaries or house prices.

Q: What is standard deviation?

A: A measure of how spread out values are around the mean.

Q: What does a high standard deviation indicate?

A: Values are more dispersed and less concentrated around the mean.

Q: What is an outlier?

A: An observation unusually far from the rest of the data. It should be investigated before being removed.

Q: What is correlation?

A: A measure of the strength and direction of a linear relationship between two variables.

Q: What is the difference between correlation and causation?

A: Correlation means variables move together. Causation means a change in one variable contributes to a change in another.

Q: What is regression analysis?

A: A statistical method used to model relationships between variables and estimate or predict outcomes.

Q: What is R-squared?

A: A measure of the proportion of variation in the outcome explained by a regression model.

Q: What is a p-value?

A: The probability, assuming the null hypothesis is true, of observing results at least as extreme as those obtained.

Q: What is a confidence interval?

A: An interval produced by a statistical method to estimate a population parameter, with a specified long-run coverage rate.

Q: What is hypothesis testing?

A: A method of using sample data to evaluate a claim about a population.

Q: What is the difference between Type I and Type II errors?

A: Type I is a false positive. Type II is a false negative.

Q: What is A/B testing?

A: An experiment comparing two versions to determine whether one produces a better outcome.

Q: Why is random sampling important?

A: It helps reduce selection bias and makes results more representative of the population.

---

# 8. FINAL STUDY REMINDERS

- Know mean, median and mode.
- Understand variance and standard deviation.
- Know how to identify potential outliers.
- Understand percentiles and quartiles.
- Understand basic probability.
- Recognize normal, binomial and Poisson distributions.
- Understand correlation vs causation.
- Know the basics of linear regression.
- Understand R-squared.
- Know null and alternative hypotheses.
- Understand p-values and significance levels.
- Know how confidence intervals work.
- Understand Type I and Type II errors.
- Know the purpose of sampling.
- Understand A/B testing and randomization.
- Remember that statistical significance isn't necessarily business significance.