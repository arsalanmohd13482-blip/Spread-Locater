# 📊 Spread Locator — Statistical Distribution Analysis

> **A statistical analysis framework for understanding e-commerce transaction behavior through probability distributions, transformations, and probability-based insights.**

## 📌 Project Overview

**Spread Locator** analyzes synthetic e-commerce transaction data to understand how customer purchasing behavior can be represented using different statistical distributions.

The project focuses on two major dimensions:

- **Transaction activity** — how frequently transactions occur and whether they succeed or fail.
- **Transaction value** — how transaction amounts are distributed, including skewness and extreme spending behavior.

The analysis uses **1,000 synthetic transactions** containing transaction amount, date, transaction frequency, region, and checkout status.

---

## 🎯 Business Objective

An e-commerce platform wants to understand:

- How likely a checkout is to succeed or fail
- How transaction activity changes across days
- How customer spending is distributed
- Whether transaction amounts follow a normal or skewed pattern
- How transformations can improve statistical analysis
- How probability thresholds can support operational decisions

The goal is to convert these statistical patterns into **practical business insights** for transaction monitoring, demand planning, and customer spending analysis.

---

## 🗂️ Dataset

The synthetic dataset contains **1,000 transaction records** with the following attributes:

| Column | Description |
|---|---|
| `transaction_id` | Unique identifier for each transaction |
| `customer_id` | Identifier of the customer |
| `transaction_amount` | Monetary value of the transaction |
| `transaction_date` | Date of the transaction |
| `transaction_count` | Number of transactions associated with a customer |
| `region` | Customer region: North, South, East, or West |
| `transaction_status` | Checkout outcome: Success or Fail |

Transaction amounts were generated using a **Log-Normal distribution** to represent realistic right-skewed e-commerce spending behavior. :contentReference[oaicite:1]{index=1}

---

# 🔬 Statistical Analysis

## 1️⃣ Bernoulli & Binomial Distribution

### Bernoulli Distribution

Used to model an individual checkout outcome:

**Success = 1**  
**Failure = 0**

The observed transaction success probability is used as the Bernoulli parameter.

**Result:**

- Successful transactions: **845 / 1,000**
- Estimated probability of success: **84.5%**

### Binomial Distribution

A Binomial model is used to estimate the probability of observing different numbers of successful transaction opportunities across **10 possible opportunities**.

This provides a simple way to understand **repeated transaction behavior and customer engagement**.

---

## 2️⃣ Poisson Distribution

The Poisson distribution is applied to **daily transaction volume**.

The analysis:

1. Converts transaction dates into daily values
2. Counts transactions occurring each day
3. Estimates the average daily transaction rate (**λ**)
4. Calculates Poisson probabilities for different transaction volumes

**Observed average:** approximately **11.11 transactions per day**.

This can help an e-commerce business identify expected transaction volume and prepare for periods of unusually high activity.

---

## 3️⃣ Transaction Amount — Log-Normal Analysis

Transaction amounts are analyzed using a **Log-Normal distribution** because monetary values are positive and typically right-skewed.

The project compares:

- Original transaction amounts
- Log-transformed transaction amounts
- Fitted Log-Normal probability density

The fitted model helps describe the overall spending pattern while accounting for the long right tail created by high-value transactions.

---

## 4️⃣ Q-Q Plot Analysis

A **Q-Q plot** is used to compare raw transaction amounts against a theoretical normal distribution.

### Purpose

- Check whether transaction amounts are approximately normal
- Identify skewness
- Detect deviations in the tails
- Understand whether normal-distribution assumptions are appropriate

The Q-Q analysis demonstrates why the raw transaction amounts should not automatically be treated as normally distributed.

---

## 5️⃣ Box-Cox Transformation

The **Box-Cox transformation** is applied to transaction amounts to reduce skewness and move the distribution closer to normality.

The analysis compares:

**Original Data → Box-Cox Transformed Data → Q-Q Plot**

The optimal transformation parameter (**λ**) is estimated directly from the data.

This is useful when statistical methods require data that is closer to a normal distribution or has more stable variance.

---

## 6️⃣ Z-Score & Probability

Z-scores are calculated for individual transaction amounts to measure how far each transaction is from the average in standard-deviation units.

The project also evaluates:

> **What is the probability that a transaction exceeds ₹5,000?**

This converts a business spending threshold into a statistical probability.

**Key result:**

- Mean transaction amount: approximately **₹2,522**
- Standard deviation: approximately **₹2,530**
- Z-score for ₹5,000: approximately **0.98**
- Estimated probability of exceeding ₹5,000: approximately **16.37%**

This can help identify and monitor relatively high-value transactions.

---

## 7️⃣ Probability Density Function (PDF) & Cumulative Distribution Function (CDF)

### PDF

The empirical PDF shows **where transaction amounts are concentrated** and helps visualize the overall spending distribution.

### CDF

The empirical CDF shows the cumulative probability:

> **P(Transaction Amount ≤ X)**

Selected spending boundaries such as:

- ₹1,000
- ₹2,000
- ₹3,000
- ₹5,000
- ₹10,000

are evaluated to understand what proportion of transactions falls below each threshold.

This provides a practical way to define **customer spending segments and transaction-value boundaries**.

---

# 📈 Distribution Selection

| Business Question | Statistical Method |
|---|---|
| Will a checkout succeed or fail? | **Bernoulli** |
| How many successful opportunities may occur? | **Binomial** |
| How many transactions occur per day? | **Poisson** |
| How are transaction amounts distributed? | **Log-Normal** |
| Are transaction amounts normally distributed? | **Q-Q Plot** |
| Can skewness be reduced? | **Box-Cox** |
| How unusual is a transaction? | **Z-Score** |
| What percentage falls below a spending threshold? | **CDF** |
| Where are transaction values concentrated? | **PDF** |

---

# 💡 Key Business Insights

The analysis demonstrates that **no single statistical distribution explains every aspect of e-commerce transaction behavior**.

- **Bernoulli** is appropriate for individual transaction outcomes.
- **Binomial** helps model repeated transaction opportunities.
- **Poisson** is useful for daily transaction volume.
- **Log-Normal** is the primary model for transaction amounts.
- **Q-Q and Box-Cox** help diagnose and handle non-normality.
- **Z-scores** identify unusual transaction values.
- **PDF and CDF** provide practical spending distributions and thresholds.

These insights can support:

- 📦 **Demand & capacity planning**
- 🛒 **Customer spending segmentation**
- 🚨 **High-value transaction monitoring**
- ⚙️ **Checkout performance monitoring**
- 📊 **Data-driven operational decisions**

---

# 🛠️ Tools & Technologies

- Python
- NumPy
- Pandas
- SciPy
- Matplotlib
- Seaborn
- Probability & Statistics

---

# 📁 Project Structure

```text
Spread-Locator/
│
├── spread_locater.py
├── Ecom_sales
└── README.md
