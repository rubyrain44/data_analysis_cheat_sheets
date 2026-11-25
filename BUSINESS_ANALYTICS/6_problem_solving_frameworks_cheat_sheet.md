# ANALYTICAL PROBLEM-SOLVING FRAMEWORKS CHEAT SHEET

# 1. THE GENERAL ANALYTICAL FRAMEWORK

Use this process when approaching almost any business problem.

STEP 1: DEFINE THE PROBLEM

Understand what the business wants to solve.

Ask:
- What happened?
- What is the business concern?
- What decision needs to be made?
- What does success look like?

STEP 2: DEFINE THE OBJECTIVE

Determine what the analysis should accomplish.

Example:
Identify why monthly revenue declined.

STEP 3: IDENTIFY THE DATA

Determine which information is required.

Examples:
- Sales transactions.
- Customer records.
- Product information.
- Marketing data.
- Historical performance.

STEP 4: CHECK DATA QUALITY

Validate:
- Missing values.
- Duplicate records.
- Incorrect formats.
- Unexpected values.
- Inconsistent definitions.

STEP 5: DEVELOP HYPOTHESES

Create possible explanations that can be tested.

Example:
Revenue declined because fewer customers completed purchases.

STEP 6: ANALYZE THE DATA

Use:
- SQL.
- Excel.
- Power BI.
- Statistics.
- Charts and visualizations.

STEP 7: INTERPRET FINDINGS

Identify:
- Patterns.
- Differences.
- Trends.
- Relationships.
- Potential causes.

STEP 8: VALIDATE RESULTS

Check calculations, assumptions and alternative explanations.

STEP 9: MAKE RECOMMENDATIONS

Explain what the business could do based on the evidence.

STEP 10: MONITOR RESULTS

Measure whether the recommended action produces improvement.

IMPORTANT:
Analysis should support a decision, not just produce numbers.

---

# 2. ROOT CAUSE ANALYSIS FRAMEWORK

Purpose:
Identify the underlying reasons behind a business problem.

Example:

Problem:
Revenue decreased by 15%.

Investigate the following:

1. SALES VOLUME
Are fewer products being sold?

2. AVERAGE SELLING PRICE
Are customers spending less per unit?

3. CUSTOMER BEHAVIOR
Are customers purchasing less frequently?

4. CUSTOMER ACQUISITION
Are fewer new customers joining?

5. CUSTOMER RETENTION
Are more customers leaving?

6. PRODUCT PERFORMANCE
Are certain products underperforming?

7. GEOGRAPHIC PERFORMANCE
Are particular regions declining?

8. OPERATIONAL ISSUES
Are stock shortages or delivery problems affecting sales?

9. EXTERNAL FACTORS
Are economic conditions or competitors influencing performance?

ANALYTICAL APPROACH:

- Compare current and historical performance.
- Break down revenue by category.
- Identify the largest contributors to change.
- Investigate unusual patterns.
- Validate potential explanations.

IMPORTANT:
A decline may have several contributing factors.

---

# 3. THE 5 WHYS FRAMEWORK

Purpose:
Explore why a problem occurred by repeatedly asking why.

Example:

Problem:
Customer complaints increased.

WHY 1:
Why did complaints increase?
Because deliveries are arriving late.

WHY 2:
Why are deliveries late?
Because orders are dispatched late.

WHY 3:
Why are orders dispatched late?
Because warehouse processing is delayed.

WHY 4:
Why is warehouse processing delayed?
Because staffing is insufficient during peak demand.

WHY 5:
Why is staffing insufficient?
Because demand forecasting does not adequately account for seasonal demand.

Potential root cause:
Inaccurate demand forecasting and staffing planning.

IMPORTANT:
Verify each answer with evidence. Don't assume the last answer is automatically the true root cause.

---

# 4. THE PARETO ANALYSIS FRAMEWORK

Purpose:
Identify which categories contribute most to a problem or outcome.

Based on the Pareto principle, often called the 80/20 rule.

Example:
A business has 1,000 customer complaints.

Analysis shows:
- Delivery delays: 500.
- Product defects: 250.
- Billing problems: 150.
- Other: 100.

Delivery delays contribute 50% of complaints.

ANALYTICAL PROCESS:

1. Categorize the issues.
2. Count occurrences.
3. Calculate each category's percentage.
4. Rank categories from highest to lowest.
5. Calculate cumulative percentages.
6. Identify the largest contributors.
7. Prioritize improvement efforts.

IMPORTANT:
The 80/20 relationship is not guaranteed. Use the actual data to determine priorities.

---

# 5. SEGMENTATION FRAMEWORK

Purpose:
Break data into meaningful groups to identify patterns.

COMMON SEGMENTS:

CUSTOMERS:
- New vs returning.
- High vs low value.
- Active vs inactive.
- Subscription type.

GEOGRAPHY:
- Country.
- Region.
- City.

PRODUCTS:
- Category.
- Brand.
- Product type.

TIME:
- Month.
- Quarter.
- Year.
- Season.

CHANNEL:
- Website.
- Mobile app.
- Physical store.
- Paid advertising.
- Organic traffic.

ANALYTICAL PROCESS:

1. Define the population.
2. Choose meaningful segments.
3. Calculate relevant KPIs for each segment.
4. Compare performance.
5. Identify differences.
6. Investigate possible explanations.

IMPORTANT:
Segmentation can reveal patterns hidden by overall averages.

---

# 6. COHORT ANALYSIS FRAMEWORK

Purpose:
Understand how groups of customers behave over time.

Example:
Group customers by the month they first purchased.

Cohort A:
Customers acquired in January.

Cohort B:
Customers acquired in February.

Cohort C:
Customers acquired in March.

Compare:
- Retention.
- Repeat purchases.
- Revenue.
- Churn.
- Engagement.

Example:

January Cohort:
Month 1 retention = 100%
Month 2 retention = 80%
Month 3 retention = 65%

February Cohort:
Month 1 retention = 100%
Month 2 retention = 85%
Month 3 retention = 70%

Interpretation:
The February cohort shows better retention at the observed stages.

IMPORTANT:
Compare equivalent customer ages and account for incomplete observation periods.

---

# 7. FUNNEL ANALYSIS FRAMEWORK

Purpose:
Identify where users drop out of a process.

Example:

Website Visitors: 10,000

Product Views: 6,000

Add to Cart: 3,000

Checkout Started: 2,000

Purchases: 1,000

Conversion from visitors to purchases:

1,000 / 10,000 × 100 = 10%

Checkout Conversion:

1,000 / 2,000 × 100 = 50%

ANALYTICAL PROCESS:

1. Define funnel stages.
2. Count users at each stage.
3. Calculate conversion rates.
4. Calculate drop-off rates.
5. Identify the largest losses.
6. Investigate possible causes.
7. Recommend improvements.

IMPORTANT:
Ensure stages are defined consistently and users are tracked correctly through the funnel.

---

# 8. BUSINESS SCENARIO FRAMEWORKS

## Scenario 1: Revenue Is Declining

BUSINESS PROBLEM:
Revenue decreased compared with the previous period.

INVESTIGATE:

- Sales volume.
- Average order value.
- Average selling price.
- Customer acquisition.
- Customer retention.
- Product performance.
- Regional performance.
- Seasonality.

QUESTIONS TO ASK:

- Is the decline across the entire business?
- Are certain products responsible?
- Are fewer customers purchasing?
- Are existing customers spending less?
- Did prices or costs change?
- Is the decline seasonal?

POSSIBLE RECOMMENDATIONS:

- Improve underperforming product categories.
- Investigate customer retention.
- Review pricing strategies.
- Address regional performance issues.

---

## Scenario 2: Customer Churn Is Increasing

BUSINESS PROBLEM:
More customers are leaving.

INVESTIGATE:

- Churn by customer segment.
- Subscription type.
- Customer tenure.
- Product usage.
- Customer complaints.
- Pricing changes.
- Customer service performance.

QUESTIONS TO ASK:

- Are new customers leaving quickly?
- Are long-term customers leaving?
- Is churn concentrated in one segment?
- Did something change before churn increased?

POSSIBLE RECOMMENDATIONS:

- Improve onboarding.
- Investigate service problems.
- Review pricing.
- Develop targeted retention strategies.

---

## Scenario 3: Conversion Rate Is Decreasing

BUSINESS PROBLEM:
Fewer visitors are completing purchases.

INVESTIGATE:

- Traffic sources.
- Device types.
- Website performance.
- Funnel drop-offs.
- Checkout failures.
- Product availability.
- Pricing changes.

QUESTIONS TO ASK:

- Did website traffic change?
- Are mobile users converting differently?
- At which funnel stage are users leaving?
- Did a website update occur?
- Are technical problems affecting purchases?

POSSIBLE RECOMMENDATIONS:

- Improve checkout experience.
- Fix technical problems.
- Optimize mobile experience.
- Test changes using controlled experiments.

---

## Scenario 4: Marketing Spend Is Increasing but Sales Are Not

BUSINESS PROBLEM:
Marketing costs increase without corresponding sales growth.

INVESTIGATE:

- Advertising spend.
- Cost per click.
- Click-through rate.
- Conversion rate.
- Customer acquisition cost.
- Return on ad spend.
- Campaign performance.

QUESTIONS TO ASK:

- Which campaigns generate customers?
- Are clicks converting?
- Are acquisition costs increasing?
- Are customers profitable?
- Is marketing reaching the right audience?

POSSIBLE RECOMMENDATIONS:

- Reallocate budget toward effective campaigns.
- Improve landing pages.
- Review targeting.
- Investigate conversion problems.

IMPORTANT:
Don't evaluate campaigns using clicks alone. Connect marketing activity to meaningful business outcomes.

---

## Scenario 5: A Region Is Underperforming

BUSINESS PROBLEM:
One geographic region has lower sales than others.

INVESTIGATE:

- Revenue.
- Order volume.
- Customer count.
- Average order value.
- Conversion rate.
- Product availability.
- Marketing activity.
- Regional operating costs.

QUESTIONS TO ASK:

- Is demand lower?
- Are fewer customers being acquired?
- Are certain products unavailable?
- Are competitors performing better?
- Are there operational problems?

POSSIBLE RECOMMENDATIONS:

- Improve regional marketing.
- Address inventory issues.
- Review product availability.
- Investigate customer behavior.

---

# 9. PRIORITIZATION FRAMEWORKS

## Impact vs Effort Matrix

Purpose:
Determine which projects or actions should be prioritized.

HIGH IMPACT / LOW EFFORT:
Quick wins.

HIGH IMPACT / HIGH EFFORT:
Major strategic projects.

LOW IMPACT / LOW EFFORT:
Optional improvements.

LOW IMPACT / HIGH EFFORT:
Usually low priority.

IMPORTANT:
Prioritize work based on business value, available resources and urgency.

## Urgency vs Importance

URGENT + IMPORTANT:
Address immediately.

IMPORTANT + NOT URGENT:
Plan and schedule.

URGENT + NOT IMPORTANT:
Consider delegating or minimizing.

NEITHER:
Consider postponing or removing.

## Cost-Benefit Analysis

Purpose:
Compare expected benefits with associated costs.

Net Benefit = Total Benefits - Total Costs

Benefit-Cost Ratio = Total Benefits / Total Costs

IMPORTANT:
Consider both financial and non-financial benefits, along with uncertainty and implementation risks.

---

# 10. DECISION-MAKING FRAMEWORK

When making recommendations:

1. IDENTIFY THE PROBLEM
What needs to improve?

2. REVIEW THE EVIDENCE
What does the data show?

3. IDENTIFY OPTIONS
What actions could address the issue?

4. EVALUATE TRADE-OFFS
What are the costs, risks and benefits?

5. MAKE A RECOMMENDATION
Which option offers the strongest expected outcome?

6. DEFINE SUCCESS
Which KPIs will measure improvement?

7. MONITOR RESULTS
Did the action work?

IMPORTANT:
Recommendations should be supported by evidence and realistic business considerations.

---

# 11. COMMUNICATING ANALYTICAL FINDINGS

Use this simple structure:

PROBLEM:
What business issue are we addressing?

FINDING:
What did the analysis reveal?

EVIDENCE:
Which numbers or trends support the finding?

IMPACT:
Why does it matter?

RECOMMENDATION:
What should happen next?

SUCCESS METRIC:
How will improvement be measured?

EXAMPLE:

PROBLEM:
Customer retention declined.

FINDING:
Customers acquired through one marketing channel have lower retention.

EVIDENCE:
Their 90-day retention rate is lower than customers acquired through other channels.

IMPACT:
The business may be spending more to acquire customers who generate less long-term value.

RECOMMENDATION:
Investigate the channel's targeting and onboarding experience.

SUCCESS METRIC:
90-day retention rate and customer acquisition cost.

IMPORTANT:
Do not assume the marketing channel caused the retention difference without further investigation.

---

# 12. COMMON ANALYTICAL INTERVIEW QUESTIONS

Q: How would you approach an unfamiliar business problem?

A: Clarify the objective, identify relevant data, validate its quality, develop hypotheses, perform analysis, interpret findings and communicate recommendations.

Q: What would you do if revenue suddenly dropped?

A: Validate the numbers, compare historical performance, segment revenue by product, region and customer, investigate volume and pricing, identify contributing factors and recommend actions.

Q: How do you identify the root cause of a problem?

A: Break the problem into contributing factors, investigate patterns, test possible explanations and validate findings with evidence.

Q: Why is segmentation useful?

A: It reveals differences between groups that may be hidden in overall averages.

Q: What is cohort analysis used for?

A: Understanding how groups of customers behave over time, particularly retention and repeat purchasing.

Q: What is funnel analysis?

A: Measuring progression through stages of a process and identifying where users drop off.

Q: How do you prioritize multiple analytical requests?

A: Consider business impact, urgency, effort, dependencies and deadlines.

Q: What if your analysis contradicts what management expects?

A: Validate the data, review assumptions, communicate the findings objectively and explain the evidence and limitations.

Q: How do you know whether a recommendation worked?

A: Define success metrics before implementation and compare results against an appropriate baseline or comparison group.

Q: What if the data doesn't answer the business question?

A: Identify the information gap, explain the limitations and determine whether additional data collection or analysis is needed.

---

# 13. FINAL STUDY REMINDERS

- Start with the business question.
- Understand the objective before analyzing.
- Validate data quality.
- Develop testable hypotheses.
- Investigate root causes.
- Use segmentation to find hidden patterns.
- Understand cohort analysis.
- Understand funnel analysis.
- Compare trends and performance.
- Consider seasonality.
- Identify bias and limitations.
- Prioritize by impact and effort.
- Make evidence-based recommendations.
- Communicate findings clearly.
- Define KPIs to measure success.
- Monitor outcomes after implementation.