📉 Outlier Detection & Removal using the Percentile Method
Flexible, Distribution-Agnostic Outlier Handling for Real-World Data

A practical demonstration of how to identify and manage extreme values using percentile-based thresholds — a robust, intuitive approach that works well even when data isn’t normally distributed. This notebook compares two key strategies: removing outliers vs. capping them, so you can choose the best fit for your use case.

✅ Ideal for income, revenue, or any skewed numerical feature where extreme values are common but not necessarily invalid.

📌 Overview
Using a customer dataset with an income column, this notebook walks through a complete outlier treatment workflow based on the 1st and 99th percentiles. By excluding only the most extreme 2% of values (1% on each tail), it offers a balanced way to clean data without over-trimming.

🔍 Key Steps Demonstrated

📥 Data Inspection
The dataset includes demographic and behavioral features like age, gender, days_on_platform, and purchases, with income as the primary focus for outlier analysis. Initial inspection confirms the presence of a long-tailed, right-skewed distribution — typical of real-world financial data.

📏 Percentile-Based Boundary Setting
Instead of relying on assumptions about data shape (like Z-scores) or quartiles (like IQR), this method uses empirical percentiles:

Lower Limit: 1st percentile → 1,077.92
Upper Limit: 99th percentile → 255,072.86
This defines a “reasonable” range that excludes only the most extreme observations.

✂️ Trimming (Outlier Removal)
A filtered version of the dataset is created by excluding all records where income falls outside the 1st–99th percentile range.

Result: 100 rows removed (from 5,000 → 4,900)
Use when: Outliers are likely errors or irrelevant to your analysis
🧢 Capping (Winsorization)
Instead of deletion, extreme values are pulled back to the nearest boundary:

Incomes below 1,077.92 become 1,077.92
Incomes above 255,072.86 become 255,072.86
Result: Full dataset retained (5,000 rows), but extreme influence neutralized
Use when: Every observation is valuable (e.g., rare high-income customers)
📊 Visual Validation
Trimmed data: Histogram shows a smoother, more concentrated distribution
Capped data: Histogram reveals clear peaks at the boundaries — visual proof of capping
Box plots: After capping, no outliers appear, confirming successful treatment
These visuals make it easy to see how each method reshapes the data.

💡 Key Takeaways for Practitioners

🎯 Percentiles are flexible: No assumption of normality needed
⚖️ Trimming vs. Capping: Choose based on data value vs. noise trade-off
👀 Always visualize: Histograms and box plots reveal what summary stats hide
🔒 Preserve sample size: Capping is often preferred in modeling to avoid data loss
📐 1%–99% is a common default, but adjust based on domain knowledge (e.g., 5%–95% for more aggressive cleaning)
🚀 When to Use This Approach

Working with skewed or heavy-tailed data (e.g., income, sales, latency)
You need a simple, interpretable outlier rule
You want to avoid parametric assumptions
Downstream models are sensitive to extreme values (e.g., linear regression, clustering)
📬 Feedback & Contributions
Want to compare with IQR or Z-score methods, add dynamic percentile selection, or include missing value handling?
👉 Open an issue or submit a pull request — all ideas are welcome! 🤝
