# Starbucks Offer Uplift Modeling Project

## Project Overview

This project analyzes the effectiveness of Starbucks' marketing offers using **uplift modeling** techniques. The goal is to identify which customers are most responsive to different types of offers (e.g., BOGO, discount, informational) and to quantify the **incremental impact** of each offer type on purchasing behavior.

The project applies **causal inference principles** to segment customers into:

- **Highly Persuadable:** Customers with significant uplift (>10%)
- **Persuadable:** Customers with moderate uplift (5–10%)
- **Sure Thing / Lost Cause:** Customers unlikely to change behavior with the offer
- **Do Not Disturb:** Customers negatively influenced by the offer (< -5% uplift)

---

## Dataset

The dataset includes approximately **15,000 customers** and **280,000 action records**, with events such as:

- `offer_received`
- `offer_viewed`
- `transaction`
- `offer_completed`

Additional data includes **customer demographics** and **offer metadata** (e.g., type, duration).

---

## Modeling Approach

1. **Data Preparation:**
   - Merged transactional logs with offer metadata.
   - Engineered a **treatment flag** to identify whether a customer received a specific offer.
   - Defined an **outcome window** (e.g., 7–10 days post-offer) to capture transactions relevant to each offer.
   - Logistic Regression used on BOGO dataset to assess treatment and control bias using **propensity score**

2. **Uplift Modeling:**
   - Used uplift decision trees to estimate **incremental effect sizes**.
   - Created segments based on predicted uplift scores.
   - Explored multiple offer types: **BOGO, Discount, Informational**.

3. **Thresholds:**
   - **Persuadable:** >10% uplift
   - **Do Not Disturb:** < -5% uplift

These thresholds align with **industry best practices** and are intentionally conservative to ensure business actionability.

---

## Key Visuals

- **Uplift Curve:** Visualizes predicted uplift across customers, sorted from lowest to highest, with a reference line at **zero uplift** (no intervention baseline).
- **Pie Charts:** Show distribution of customers across the four main uplift categories for each offer type (Starbucks branding style: green tones + a contrasting red for Do Not Disturb).

---

## Business Insights

This framework allows Starbucks to:

- **Target offers more precisely,** focusing on customers most likely to convert because of the offer.
- **Avoid wasting resources** on Sure Things and Lost Causes.
- **Protect against negative effects** by identifying Do Not Disturb segments.
- **Refine marketing windows,** as demonstrated by sensitivity to different offer durations (e.g., 7-day vs. 10-day impact windows).

---

## Next Steps

- Fine-tune uplift thresholds based on **financial impact modeling.**
- Extend analysis to **long-term customer value** (LTV uplift) beyond immediate transactions.
