![Power BI](https://img.shields.io/badge/Tool-Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)

---

<p align="center">
  <img src="Images/banner.png" width="100%">
</p>

# 📊 {{PROJECT_TITLE}} | Power BI

_{{ONE_LINE_SUMMARY}}_

- 🎯 **Business Question:** {{BUSINESS_QUESTION}}
- 🏬 **Domain:** {{DOMAIN}}
- 🛠️ **Tools:** Power BI

👤 Author: Bạch Minh Nam

---

## 📑 Table of Contents
1. [📌 Background & Overview](#-background--overview)
2. [📂 Dataset Description & Data Structure](#-dataset-description--data-structure)
3. [🧠 Design Thinking Process](#-design-thinking-process)
4. [📊 Key Insights & Visualizations](#-key-insights--visualizations)
5. [🔎 Final Conclusion & Recommendations](#-final-conclusion--recommendations)

---

## 📌 Background & Overview

### Objective

{{COMPANY_CONTEXT_PARAGRAPH}}

The {{STAKEHOLDER}} needs a dashboard to answer {{N}} main questions:

✔️ **{{QUESTION_1_TITLE}}:** {{QUESTION_1_DETAIL}}

✔️ **{{QUESTION_2_TITLE}}:** {{QUESTION_2_DETAIL}}

✔️ **{{QUESTION_3_TITLE}}:** {{QUESTION_3_DETAIL}}

{{PROJECT_PURPOSE_PARAGRAPH}}

### 👤 Who is this project for?

✔️ {{AUDIENCE_1}} - {{AUDIENCE_1_REASON}}

✔️ {{AUDIENCE_2}} - {{AUDIENCE_2_REASON}}

✔️ {{AUDIENCE_3}} - {{AUDIENCE_3_REASON}}

---

## 📂 Dataset Description & Data Structure

### 📌 Data Source
- Source: {{DATA_SOURCE}}
- Format: {{DATA_FORMAT}}

### 📊 Data Structure & Relationships

#### 1️⃣ Tables Used

The dataset has **{{N_TABLES}} tables**:

- **{{TABLE_1}}** - {{TABLE_1_DESC}}
- **{{TABLE_2}}** - {{TABLE_2_DESC}}
- **{{TABLE_3}}** - {{TABLE_3_DESC}}

#### 2️⃣ Table Schema

**Table: {{TABLE_1}}** ({{TABLE_1_ROLE}})

| Column Name | Description |
|---|---|
| {{COLUMN}} | {{DESCRIPTION}} |

**Table: {{TABLE_2}}**

| Column Name | Description |
|---|---|
| {{COLUMN}} | {{DESCRIPTION}} |

**Table: {{TABLE_3}}**

| Column Name | Description |
|---|---|
| {{COLUMN}} | {{DESCRIPTION}} |

#### 3️⃣ Data Relationships

The {{N_TABLES}} tables are connected as follows:

- **{{TABLE_X}} → {{TABLE_Y}}**: {{RELATIONSHIP_DESC}} (joined on `{{KEY}}`)
- **{{TABLE_Y}} → {{TABLE_Z}}**: {{RELATIONSHIP_DESC}} (joined on `{{KEY}}`)

<p align="center">
  <img src="Images/data_model.png" width="80%">
</p>

---

## 🧠 Design Thinking Process

This project followed the Design Thinking framework across 3 main steps: Empathize, Define Point of View, and Ideate.

### 1️⃣ Empathize - Understanding the Stakeholder

| Question | Answer |
|---|---|
| **Who views this dashboard?** | {{STAKEHOLDER}} |
| **What problem does it solve?** | {{PROBLEM_SOLVED}} |
| **When & where is it used?** | {{USAGE_CONTEXT}} |
| **Why is this analysis needed?** | {{WHY_NEEDED}} |
| **How do they decide?** | {{HOW_DECIDE}} |
| **Pains** | {{PAINS}} |
| **Gains** | {{GAINS}} |
| **Key Questions to Answer** | • {{KEY_Q1}}<br>• {{KEY_Q2}}<br>• {{KEY_Q3}}<br>• {{KEY_Q4}}<br>• {{KEY_Q5}} |

### 2️⃣ Define Point of View - Choosing the Right Angles

| Point of View | Description | Why the stakeholder cares |
|---|---|---|
| **{{POV_1}}** | {{POV_1_DESC}} | {{POV_1_WHY}} |
| **{{POV_2}}** | {{POV_2_DESC}} | {{POV_2_WHY}} |
| **{{POV_3}}** | {{POV_3_DESC}} | {{POV_3_WHY}} |

**Northstar Metrics:**

| Northstar 1 | Northstar 2 |
|---|---|
| **{{NORTHSTAR_1_NAME}}** | **{{NORTHSTAR_2_NAME}}** |
| Formula: `{{NORTHSTAR_1_FORMULA}}` | Formula: `{{NORTHSTAR_2_FORMULA}}` |
| Success when: {{NORTHSTAR_1_SUCCESS}} | Success when: {{NORTHSTAR_2_SUCCESS}} |
| Why this metric: {{NORTHSTAR_1_WHY}} | Why this metric: {{NORTHSTAR_2_WHY}} |

### 3️⃣ Ideate - Structuring the Dashboard

| | **Page 1: {{PAGE_1_NAME}}** | **Page 2: {{PAGE_2_NAME}}** | **Page 3: {{PAGE_3_NAME}}** |
|---|---|---|---|
| **Layer 0 (Scorecards)** | {{P1_LAYER0}} | {{P2_LAYER0}} | {{P3_LAYER0}} |
| **Layer 1 (1-dimension breakdown)** | {{P1_LAYER1}} | {{P2_LAYER1}} | {{P3_LAYER1}} |
| **Layer 2 (2-dimension breakdown)** | {{P1_LAYER2}} | {{P2_LAYER2}} | {{P3_LAYER2}} |

---

## ⚒️ Main Process

1️⃣ **Connect & Load Data** - {{STEP_1_DESC}}

2️⃣ **Data Modeling** - {{STEP_2_DESC}}

3️⃣ **DAX Measures** - {{STEP_3_DESC}}

4️⃣ **Power BI Visualization** - {{STEP_4_DESC}}

---

## 📊 Key Insights & Visualizations

### 🔍 Dashboard Preview

> **⚙️ Advanced Power BI Features Used**
>
> - 🔖 **Bookmarks & Button** - A hidden filter panel is toggled by clicking the filter on the top right of each page. The panel slides in with: Date Range slider (May 1–31, 2024), and slicers for Product Name, Category, City, and Region - all applied simultaneously across the report page.
>
> <p align="center"><img src="Images/bookmarks.png" width="30%"></p>
>
> - 🔍 **Drill Through** - Right-click or click on any Campaign or SKU data point to drill into dedicated full-detail pages with expanded metrics tables.
>
> <p align="center"><img src="Images/Campaign_Performance_Detail.png" width="100%"></p>
> <p align="center"><img src="Images/SKU_Performance_Detail.png" width="100%"></p>
>
> - 💬 **Tooltips** - Hover over any data point on trend charts across all pages to reveal rich contextual detail (revenue breakdown, profit, ROAS) without cluttering the main view.
>
> <p align="center"><img src="Images/Tooltips1.png" width="48%"> <img src="Images/Tooltips2.png" width="48%"></p>
>
> - 🔙 **Back Button** - A navigation arrow sits on the top-left of every detail page, returning the user to the main report view.

---

#### 1️⃣ Page 1 - Executive Overview

<p align="center">
  <img src="Images/Executive_Overview.png" width="100%">
</p>

📌 **Analysis 1:**

- **Observation:** May 2024 delivered solid top-line results - Total Revenue reached **4,773.55M VND** (+5.9% vs. last period), Total Orders grew 6% to 2,858, and ROAS held at **12.11**. The company deployed **82.7% of its marketing budget** (394M / 476M VND). Despite strong headline numbers, profit was highly volatile - multiple days in Weeks 1–2 recorded **negative Total Profit**, pointing to inefficient early-month spending. Direct Sales consistently drove 78–83% of daily revenue, with Ads Sales spiking toward month-end (up to 40%). The scatter plot confirms a linear positive relationship between Marketing Cost and Marketing-driven Revenue, validating that higher ad spend does return proportionally more revenue - when allocated correctly.

- **Recommendation:**
  - 🔴 **Investigate early-May profit losses.** Negative profit days in Week 1–2 need root-cause analysis - identify which campaigns or SKUs were running below breakeven and whether discounting or high COGS were the driver.
  - 🟡 **Reallocate the remaining 17.3% budget strategically.** Rather than distributing evenly, concentrate residual budget on campaigns already proven to deliver ROAS above 12.
  - 🟢 **Use the spend–revenue correlation to justify scaling.** The scatter plot provides clear evidence that incremental marketing investment yields incremental revenue - a strong data point for budget expansion proposals.

---

#### 2️⃣ Page 2 - Campaign Performance

<p align="center">
  <img src="Images/Campaign_Performance.png" width="100%">
</p>

📌 **Analysis 2:**

- **Observation:** ROAS improved progressively across the month, peaking in **Week 5 at 17.43** - the highest weekly ROAS despite the lowest weekly spend (43.4M), suggesting audience warm-up effects compounded over time. CPC spiked sharply in **Week 1–2 (up to ~20K VND)** before normalizing, while CPM stayed relatively stable at 60–80K throughout. The Impressions vs. CTR scatter reveals weak correlation - more impressions did not reliably improve click-through rate, indicating inconsistent audience quality across campaigns. Drill-through to `Campaign_Performance_Detail` shows **AUDREY SHIRT LAL campaigns** dominated both spend (top 3) and returns (ROAS 197–625). Several small-budget campaigns showed ROAS of 700–950, likely inflated by attribution overlap with organic/direct sales.

- **Recommendation:**
  - 🔴 **Audit the Week 1–2 CPC spike.** A near-doubling of cost per click with no CTR improvement signals wasted spend - review bid strategy, audience overlap, and targeting breadth during that window.
  - 🟡 **Validate ultra-high ROAS campaigns before scaling.** ROAS of 700–950 on minimal spend likely reflects misattribution rather than true ad efficiency - cross-check against direct sales orders before increasing budget.
  - 🟢 **Scale AUDREY SHIRT LAL campaigns with confidence.** Proven ROAS of 197–625 at meaningful spend levels - this is the clearest data-backed case for additional budget allocation.

---

#### 3️⃣ Page 3 - Channel Performance

<p align="center">
  <img src="Images/Channel_Performance.png" width="100%">
</p>

📌 **Analysis 3:**

- **Observation:** Ads Sales generated **63.34% of total revenue** (2,952M VND) with a channel ROAS of **7.67**, while Direct Sales contributed 36.66% at ROAS **4.44** - confirming the Ads channel delivers superior efficiency per VND spent. The Membership tier overwhelmingly dominates revenue across both channels, with Silver, Platinum, Diamond, and Gold VIP contributing marginally. Geographically, **Hà Nội led all cities** (24.28% revenue share, 9.04% margin), followed by Hồ Chí Minh (12.65%, margin 6.93%). Secondary cities like **Bà Rịa–Vũng Tàu (10.30%)** and **Đà Nẵng (8.60%)** show stronger profit margins at lower volumes. Top products across both channels were consistently **Audrey Shirt 3 and Lisa Dress 5**.

- **Recommendation:**
  - 🔴 **Address HCM's margin problem (6.93%).** The city generates the 2nd highest revenue but the weakest margin among major cities - audit discount rates, return rates, and shipping costs specific to HCM orders.
  - 🟡 **Activate the loyalty program to move customers up tiers.** The near-total dominance of Membership-tier revenue signals the VIP program is underperforming - structured upgrade incentives could significantly lift AOV and retention.
  - 🟢 **Launch targeted Ads campaigns in Bà Rịa–Vũng Tàu and Đà Nẵng.** High margins at low volume make these cities ideal for cost-efficient expansion - lower competition than Hà Nội/HCM with better profitability per order.

---

#### 4️⃣ Page 4 - SKU Performance

<p align="center">
  <img src="Images/SKU_Performance.png" width="100%">
</p>

📌 **Analysis 4:**

- **Observation:** **Váy Chiết Eo Xoè** leads all categories in revenue contribution (31.17%) with a healthy ROAS of **11.75** and Ads Revenue of 996M - the undisputed hero category. **Áo Tách Set** ranks 2nd in revenue but recorded a **Total Profit of -259M VND** (Profit Margin -18.2%), making it the single most value-destroying product line in the portfolio. At the other extreme, **Váy Chiết Eo Ôm** achieved ROAS of **41.89** on just 11.6M in spend - the most efficient category by far, yet severely underfunded. Profit Margin across categories ranged from **-18.2% to +29.4%**, reflecting an extremely uneven product portfolio. From `SKU_Performance_Detail`, **Lisa Dress 5 (ROAS 67.73)** and **Audrey Shirt 3 (ROAS 9.76)** anchor the top of the revenue table, while Áo Tách Set products consistently appear with negative profit figures.

- **Recommendation:**
  - 🔴 **Halt ad spend on Áo Tách Set immediately.** Spending marketing budget to drive revenue on a -18.2% margin product accelerates losses - freeze campaigns and conduct a full pricing and cost review before resuming.
  - 🟡 **Significantly increase budget for Váy Chiết Eo Ôm.** ROAS of 41.89 with minimal spend is a clear signal of an underfunded high-performer - reallocating even 10–15M from underperforming categories here would materially improve overall ROAS.
  - 🟢 **Protect and grow Váy Chiết Eo Xoè as the flagship category.** Highest revenue, solid ROAS, and proven Ads-driven demand - this is the safest and highest-impact category to scale heading into June.

---

## 🔎 Final Conclusion & Recommendations

📍 Key Takeaways:

✔️ **Marketing spend is working - but only when targeted correctly.** Overall ROAS of 12.11 and revenue growth of +5.9% confirm the marketing strategy is directionally sound. However, the wide variance between campaigns (ROAS 7 to 625) and categories (margin -18% to +29%) shows that the average hides significant inefficiency. The strategic priority for June is not to spend more, but to spend smarter.

✔️ **Áo Tách Set is destroying value at scale.** The 2nd highest-revenue category is running at -259M VND profit and -18.2% margin - meaning every sale made worse the overall P&L. No marketing budget should be directed here until pricing, discounting, and COGS are restructured. This is the single highest-impact fix available.

✔️ **AUDREY SHIRT campaigns are the proven growth engine.** Delivering ROAS of 197–625 at the highest spend levels in the portfolio, these campaigns represent the clearest, lowest-risk opportunity for budget reallocation. Increasing their share of the remaining 17.3% budget is directly supported by the data.

✔️ **Váy Chiết Eo Ôm and Lisa Dress 5 are the biggest missed opportunities.** ROAS of 41.89 and 67.73 respectively, both running on minimal budgets. Shifting investment toward these two - funded by cutting spend on Áo Tách Set and underperforming campaigns - would likely push total ROAS well above the 12.11 baseline.

✔️ **Geographic and loyalty expansion offer structural long-term upside.** Bà Rịa–Vũng Tàu and Đà Nẵng show better margins than HCM at lower competitive intensity - prime targets for June Ads campaigns. Simultaneously, the near-total concentration of revenue in Membership-tier customers signals an untapped loyalty upgrade opportunity that could improve CLV without increasing ad spend.
