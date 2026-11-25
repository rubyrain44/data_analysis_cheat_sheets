# DATA VISUALIZATION & GRAPHS CHEAT SHEET

## 1. WHY DATA VISUALIZATION?

Data visualization converts raw data into visual formats to identify:
- Trends over time.
- Comparisons between categories.
- Relationships between variables.
- Distributions and patterns.
- Outliers and anomalies.
- Business performance.

GOAL:
Make data easier to understand and support business decisions.

## 2. BAR CHART

PURPOSE:
Compare values across different categories.

BEST FOR:
- Sales by region.
- Revenue by product.
- Customers by segment.
- Profit by department.

EXAMPLE:
Compare revenue across five regions.

IMPORTANT:
- Horizontal bars work well with long category names.
- Sort bars when ranking categories.
- Start the value axis at zero in most cases.

## 3. COLUMN CHART

PURPOSE:
Compare values across categories using vertical bars.

BEST FOR:
- Monthly sales comparisons.
- Revenue by product.
- Orders by department.
- Year-over-year comparisons.

IMPORTANT:
- Similar to bar charts.
- Useful for a small number of categories.
- Avoid too many columns.

## 4. LINE CHART

PURPOSE:
Show trends and changes over time.

BEST FOR:
- Monthly revenue.
- Daily website traffic.
- Annual profit.
- Customer growth.
- Stock prices.

IMPORTANT:
- Time should generally be on the X-axis.
- Values should generally be on the Y-axis.
- Useful for identifying trends, seasonality, and fluctuations.
- Avoid connecting unrelated categorical data.

## 5. PIE CHART

PURPOSE:
Show proportions of a whole.

BEST FOR:
- Market share.
- Revenue contribution.
- Customer distribution.
- Sales by category.

IMPORTANT:
- Use only a small number of categories.
- Values should represent parts of the same whole.
- Categories should be mutually exclusive.
- Avoid pie charts with too many slices.
- Use a bar chart when precise comparisons matter.

## 6. DONUT CHART

PURPOSE:
Similar to a pie chart, showing proportions of a whole.

BEST FOR:
- Revenue by category.
- Customer segments.
- Market share.

IMPORTANT:
- Center space can display a KPI.
- Limit the number of segments.
- Not ideal for detailed comparisons.

## 7. SCATTER PLOT

PURPOSE:
Show relationships between two numerical variables.

BEST FOR:
- Advertising spend vs revenue.
- Price vs demand.
- Customer age vs spending.
- Marketing spend vs conversions.

IMPORTANT:
- Each dot represents an observation.
- X-axis = First numerical variable.
- Y-axis = Second numerical variable.
- Can reveal positive or negative correlations.
- Can identify clusters and outliers.

INTERPRETATION:
- Positive correlation: Both variables tend to increase together.
- Negative correlation: One tends to decrease as the other increases.
- No clear correlation: No obvious linear relationship.

IMPORTANT:
Correlation does not imply causation.

## 8. HISTOGRAM

PURPOSE:
Show the distribution of numerical data.

BEST FOR:
- Customer age distribution.
- Order value distribution.
- Employee salaries.
- Delivery times.

IMPORTANT:
- Groups numerical values into bins.
- X-axis = Value ranges.
- Y-axis = Frequency.
- Helps identify skewness, spread, and outliers.

## 9. BOX PLOT (BOX-AND-WHISKER)

PURPOSE:
Summarize data distribution and identify potential outliers.

SHOWS:
- Median.
- First quartile (Q1).
- Third quartile (Q3).
- Interquartile range (IQR).
- Whiskers.
- Potential outliers.

FORMULAS:

IQR = Q3 - Q1

Lower Fence = Q1 - 1.5 × IQR

Upper Fence = Q3 + 1.5 × IQR

BEST FOR:
- Comparing salary distributions.
- Comparing delivery times.
- Identifying unusual sales values.

IMPORTANT:
Points outside the fences are potential outliers, not automatically errors.

## 10. AREA CHART

PURPOSE:
Show trends over time with filled areas.

BEST FOR:
- Revenue over time.
- Website traffic.
- Cumulative sales.
- Contribution of categories over time.

IMPORTANT:
- Similar to line charts.
- Highlights magnitude and cumulative values.
- Stacked area charts show contributions from multiple categories.
- Overlapping areas can make interpretation difficult.

## 11. STACKED BAR / COLUMN CHART

PURPOSE:
Compare totals while showing category composition.

BEST FOR:
- Revenue by region and product.
- Sales by month and category.
- Orders by department and status.

TYPES:
- Stacked: Shows total and component contribution.
- 100% stacked: Shows percentage composition.
- Clustered: Places categories side by side for comparison.

IMPORTANT:
- Use stacked charts when composition matters.
- Use clustered charts when comparing individual categories.
- 100% stacked charts emphasize proportions rather than totals.

## 12. WATERFALL CHART

PURPOSE:
Show how positive and negative values contribute to a final total.

BEST FOR:
- Revenue changes.
- Profit analysis.
- Budget vs actual.
- Cash flow.
- Cost breakdowns.

EXAMPLE:

Starting Revenue: 100,000
Additional Sales: +20,000
Returns: -5,000
Discounts: -10,000
Final Revenue: 105,000

IMPORTANT:
Useful for explaining what caused a metric to increase or decrease.

## 13. FUNNEL CHART

PURPOSE:
Show values across sequential stages of a process.

BEST FOR:
- Marketing conversion.
- Sales pipelines.
- Customer onboarding.
- Recruitment processes.

EXAMPLE:

Website Visitors: 10,000
Product Views: 6,000
Add to Cart: 2,000
Purchases: 800

CONVERSION RATE:
Stage Conversions / Previous Stage × 100

IMPORTANT:
Identify where the largest drop-off occurs.

## 14. TREEMAP

PURPOSE:
Display hierarchical data using nested rectangles.

BEST FOR:
- Sales by category and subcategory.
- Revenue by department.
- Product portfolio analysis.

IMPORTANT:
- Rectangle size represents magnitude.
- Color can represent another metric.
- Useful for large numbers of categories.
- Exact comparisons can be difficult.

## 15. HEATMAP

PURPOSE:
Use color intensity to highlight patterns in data.

BEST FOR:
- Sales by day and hour.
- Correlation matrices.
- Customer activity.
- Regional performance.

IMPORTANT:
- Color represents value intensity.
- Consistent color scales matter.
- Include a clear legend.
- Avoid misleading color ranges.

## 16. GEOGRAPHIC / MAP CHART

PURPOSE:
Visualize data by geographic location.

BEST FOR:
- Revenue by country.
- Customers by state.
- Sales by city.
- Delivery performance by region.

IMPORTANT:
- Use geographic fields correctly.
- Check ambiguous location names.
- Maps are useful when location matters to the decision.
- Use bar charts if geography isn't important.

## 17. COMBO CHART

PURPOSE:
Combine two chart types to compare different metrics.

BEST FOR:
- Revenue and profit margin.
- Sales volume and conversion rate.
- Actual vs target.
- Revenue and growth percentage.

EXAMPLE:
- Columns = Revenue.
- Line = Profit Margin.

IMPORTANT:
- Useful when metrics have different scales.
- Secondary axes may be appropriate.
- Label axes clearly to avoid confusion.

## 18. KPI CARDS & GAUGES

KPI CARD:
Displays one important metric.

Examples:
- Total Revenue.
- Total Profit.
- Number of Orders.
- Average Order Value.

GAUGE:
Displays performance against a target.

Examples:
- Sales vs monthly target.
- Revenue vs budget.
- Conversion rate vs goal.

IMPORTANT:
- Include context and comparison periods.
- Avoid showing numbers without units.
- Use clear targets and thresholds.

## 19. HOW TO CHOOSE THE RIGHT GRAPH

| Business Question | Best Chart |
|---|---|
| Compare categories | Bar / Column |
| Show trends over time | Line |
| Show proportions | Pie / Donut |
| Show relationships | Scatter |
| Show distributions | Histogram |
| Identify outliers | Box Plot |
| Show cumulative changes | Waterfall |
| Show process drop-off | Funnel |
| Show hierarchical data | Treemap |
| Show geographic patterns | Map |
| Compare two metrics | Combo |
| Show KPI performance | Card / Gauge |
| Compare composition | Stacked Bar / Column |

## 20. DATA VISUALIZATION BEST PRACTICES

DO:
- Choose charts based on the business question.
- Use clear titles.
- Label axes.
- Include units.
- Use consistent colors.
- Sort categories logically.
- Highlight important information.
- Use appropriate scales.
- Keep dashboards simple.
- Make visuals accessible.

DON'T:
- Use too many colors.
- Use 3D charts unnecessarily.
- Overload dashboards.
- Use pie charts with many categories.
- Misrepresent values with misleading axes.
- Use dual axes without clear labels.
- Add unnecessary decoration.
- Confuse correlation with causation.

## 21. COMMON DATA VISUALIZATION INTERVIEW QUESTIONS

Q: What chart would you use to show monthly revenue?

A: A line chart because it clearly shows trends over time.

Q: What chart would you use to compare sales across regions?

A: A bar or column chart because it allows direct comparison across categories.

Q: How would you show the relationship between marketing spend and revenue?

A: A scatter plot to identify potential relationships and correlations.

Q: How would you identify outliers in customer spending?

A: A box plot or histogram.

Q: When would you use a pie chart?

A: When showing the percentage contribution of a small number of categories to a whole.

Q: What is the difference between a stacked and clustered bar chart?

A: A stacked chart shows totals and composition. A clustered chart places categories side by side for direct comparison.

Q: What is a misleading visualization?

A: A visualization that distorts or obscures the data through inappropriate scales, axes, colors, or presentation.

Q: What makes a good dashboard?

A: A good dashboard presents relevant KPIs clearly, provides context, allows useful filtering, and supports business decisions.

Q: What is data storytelling?

A: Combining data, visualizations, and explanations to communicate insights and recommend actions.

## 22. EXCEL & POWER BI CHART KNOWLEDGE

EXCEL:
- Insert > Charts.
- PivotCharts.
- Conditional Formatting.
- Recommended Charts.
- Sparklines.
- Slicers.

POWER BI:
- Visualizations pane.
- Bar and column charts.
- Line charts.
- Matrix and tables.
- Cards and KPIs.
- Maps.
- Drill-through.
- Slicers.
- Tooltips.
- Bookmarks.

IMPORTANT:
Excel is useful for quick analysis and reporting.
Power BI is useful for interactive reports and reusable business dashboards.

## 23. INTERVIEW REMINDERS

- Know the purpose of common charts.
- Understand categorical vs numerical data.
- Understand distributions and outliers.
- Know correlation vs causation.
- Understand axes and scales.
- Know when to use stacked charts.
- Understand time-series visualization.
- Practice explaining chart insights.
- Connect every visualization to a business question.
- Avoid misleading representations.