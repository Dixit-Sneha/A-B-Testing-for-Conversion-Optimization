# Website A/B Testing for Conversion Optimization

A Python-based data analysis project developed to evaluate and compare the performance of two website versions, Variant A and Variant B. The analysis uses statistical testing, confidence intervals, and simulated user traffic to measure conversion differences and determine whether the observed improvement is statistically meaningful.

## Project Overview

Website experiments can produce misleading results when natural variation in user behavior is not taken into account. This project applies statistical methods to distinguish genuine performance improvements from random fluctuations. It also simulates incoming users in batches to observe how conversion rates, statistical significance, and performance differences evolve as more data becomes available.

### Key Features

* **Hypothesis Testing:** Uses a two-proportion Z-test to determine whether the conversion difference between the two variants is statistically significant.
* **Confidence Interval Analysis:** Calculates and visualizes 95% confidence intervals to represent the uncertainty surrounding the estimated conversion rates.
* **Batch-Based Experiment Simulation:** Models incoming website traffic in sequential batches using binomial sampling to observe how experiment results develop over time.
* **Data Visualization:** Generates charts with error bars and trend plots to present conversion metrics and statistical results clearly.

---

## Technical Stack & Library Selection

The project is implemented using commonly used Python data analysis and statistical libraries:

* **`NumPy`**: Used for numerical operations, array processing, and binomial sampling through `np.random.binomial`.
* **`Pandas`**: Handles structured datasets, aggregation, and cumulative results across simulation batches.
* **`Matplotlib`**: Used to generate bar charts, line plots, and confidence interval visualizations.
* **`SciPy`**: Provides statistical functions required for the analysis.
* **`Statsmodels`**: Used for statistical modeling and implementation of the `proportions_ztest`.

---

## Experimental Setup & Framework

### 1. Initial Experiment Setup

* **Sample Size:** 10,000 users for each website variant.
* **Expected Conversion Rates:**

  * **Variant A:** 10% expected conversion rate.
  * **Variant B:** 12% expected conversion rate.

### 2. Simulated Live Traffic

* **Simulation Method:** Users are introduced through sequential batches across 30+ iterations.
* **Tracked Metrics:** Each stage records the conversion lift between Variant B and Variant A along with the corresponding p-value to monitor the progression of the experiment.

---

## Analysis & Key Findings

The standard experimental simulation produced the following results:

### Conversion Rates & Confidence Intervals

* **Variant A (Control):** 973 conversions → **9.73% conversion rate**

  * **95% Confidence Interval:** [9.15% ...
* **Variant B (Treatment):** 1,134 conversions → **11.34% conversion rate**

  * **95% Confidence Interval:** [10.72% ...

> **Statistical Insight:** The confidence intervals for the two variants show no overlap, providing strong evidence that the higher conversion rate observed for Variant B is unlikely to be caused by random variation alone.

### Statistical Significance

* **Z-statistic:** `5.10`
* **p-value:** `0.0000003`

Because the p-value is substantially lower than the commonly used significance level of **α = 0.05**, the Null Hypothesis (H0) is rejected. The results therefore provide strong statistical evidence that Variant B performs better than Variant A.

---

## Strategic Recommendations & Stopping Rules

For practical deployment of A/B experiments, the project recommends using predefined stopping conditions to avoid making decisions from unstable early results:

1. **Set a Minimum Sample Size:** Avoid ending an experiment prematurely because of temporary fluctuations during the first few batches.
2. **Monitor Statistical Significance:** The p-value should remain consistently below **0.05** across multiple consecutive batches before making a final decision.
3. **Check Conversion Lift Stability:** The improvement in Variant B should remain positive and gradually stabilize around the expected performance difference.

**Final Recommendation:** Based on the simulated results, Variant B should be deployed to production traffic, as the statistical analysis indicates a reliable improvement in conversion performance.
