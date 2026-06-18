![Power BI](https://img.shields.io/badge/Tool-Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)

---

<p align="center">
  <img src="Images/banner.jpg" width="100%">
</p>

# 📊 Fashion Revenue & Marketing Campaign Analysis | Power BI

_Tactical report to optimize marketing budget allocation based on KPIs and bridge the gap between Meta Ads performance and e-commerce retail sales._

- 🎯 **Business Question:** How can we link retail revenue data with marketing costs, monitor budget utilization progress, and optimize ad spend efficiency based on key KPIs ?
- 🏬 **Domain:** Fashion Retail & E-commerce
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

The business operates within the fashion retail and e-commerce industry, executing multi-channel marketing campaigns to drive sales growth and elevate brand visibility. Given a defined marketing budget, the company must understand exactly how each currency unit spent transforms into profit or loss, eliminating wasted expenditures on underperforming products and ads.

The Executive Board and leadership team require a tactical dashboard to address three fundamental business needs:

✔️ **Executive Overview:** What is our current budget utilization rate? Does the relationship between marketing costs and net revenue reliably deliver optimal net profits on a daily and weekly basis?

✔️ **Campaign & Channel Performance:** Which marketing campaigns yield the highest profitability? How are the ad platform technical metrics (CPC, CPM, CTR) fluctuating? Does the paid acquisition channel (Ads Sales) truly outperform organic/store-driven sales (Direct Sales)?

✔️ **SKU Performance:** Which product categories and SKUs contribute the largest revenue share? Which items achieve excellent ROAS metrics to justify scaling, and which ones are driving margins into negative territory?

The core objective of this project is to build an automated dashboard framework that integrates siloed Facebook Ads data with confirmed backend order fulfillments, empowering leadership to optimize cash flows and make precise budget reallocation choices.

### 👤 Who is this project for?

✔️ **Marketing Manager** - Needs to monitor granular technical ad performance across Meta Ads, control CPM, CPC, CTR, and ROAS trends to optimize creatives, targeting parameters, and adjust weekly spend allocations.

✔️ **Sales Manager** - Needs to manage revenue across distribution channels (Ads vs Direct), examine customer purchasing power by geographical city, and leverage customer loyalty tiers to structure conversion incentives.

✔️ **Board of Directors (CEO/Directors)** - Require a high-level perspective of the financial bottom line, relying on two core metrics (ROAS & Profit Margin %) to control cash flow risks and approve strategic budget expansions.

---

## 📂 Dataset Description & Data Structure

### 📌 Data Source
- Source: Fashion Marketing & Sales Analysis Dataset.
- Format: Excel Workbook (`.xlsx`)

### 📊 Data Structure & Relationships

#### 1️⃣ Tables Used

The dataset consists of **4 main tables**:

- **`order`** - Granular transaction line-level data including order timestamp, statuses, customer demographics, revenue, and product cost of goods (3,451 rows).
- **`danh sach san pham`** - Master product catalog detailing full item names, listed retail prices, production costs, and category labels (2,250 rows).
- **`mkt_camp_cost`** - Daily ad campaign cost and aggregate tracking metrics (Impressions, Clicks, Spend, CPC, CPM, CTR) at a campaign level (854 rows).
- **`mkt_camp_by_sku_cost`** - Meta Ads performance data distributed dynamically down to the specific product/SKU variation level (3,874 rows).

#### 2️⃣ Table Schema (Core Fields)

**Table: `order`** (Fact Table)

| Column Name | Description |
|---|---|
| ID | Unique transaction order identifier |
| Thời gian | Exact datetime stamp of the completed order |
| Mã sản phẩm | Unique product/SKU variant code, used as a key |
| Số lượng | Quantity of items purchased within the order line |
| Giá | Actual transaction selling price for the product line (VND) |
| Giá vốn | Cost of goods sold (COGS) for the product line (VND) |
| Trạng thái | Fulfilment status |

**Table: `danh sach san pham`** (Dimension Table)

| Column Name | Description |
|---|---|
| Mã sản phẩm | Primary key representing the unique SKU variant |
| Tên sản phẩm | The full catalog name of the fashion product |
| Giá bán | Official listed retail price of the item (VND) |
| Giá vốn | Master production cost/COGS for the item (VND) |
| Danh mục | General product category grouping |

**Table: `mkt_camp_by_sku_cost`** (Fact Table / Ad Performance)

| Column Name | Description |
|---|---|
| Tên chiến dịch | The designated name of the marketing campaign running on Meta Ads |
| Ngày | Reporting calendar date for the ad tracking |
| Mã Sản phẩm | SKU code used to join directly against the master product dimension table |
| Số tiền đã chi tiêu (VND) | Total advertising expenditure for the entire campaign on that day |
| Tiền đã chạy \nTheo Sản phẩm | Portion of the ad budget allocated specifically to that unique SKU (VND) |

> ℹ️ *Note: The tables above highlight the critical fields mapped into the reporting schema. To explore the complete set of columns and additional attributes, please refer to the original file: [data_dictionary.md](data_dictionary.md).*

#### 3️⃣ Data Relationships

The reporting schema is integrated within Power BI using a Star Schema structure:

- **`danh sach san pham` → `order`**: 1-to-Many Relationship (mapped via the primary tracking key `Mã sản phẩm`)
- **`danh sach san pham` → `mkt_camp_by_sku_cost`**: 1-to-Many Relationship (mapped via the cross-functional keys `Mã sản phẩm` / `Mã Sản phẩm`)
- **`Dim_Date` → `order`**: 1-to-Many Relationship (mapped from `Date` to the order timestamp `Thời gian`)
- **`Dim_Date` → `mkt_camp_by_sku_cost`**: 1-to-Many Relationship (mapped from `Date` to the marketing log date `Ngày`)
- **`dim_mkt_camp_cost` → `fact_mkt_camp_by_sku_cost`**: 1-to-Many Relationship (mapped via the custom-generated tracking key `CampaignID` to bridge aggregate daily campaign metrics with granular SKU performance)

<p align="center">
  <img src="Images/data_model.png" width="80%">
</p>

---

## 🧠 Design Thinking Process

This analytics deployment followed the Design Thinking structure across 3 stages to ensure the final solution solves real business needs.

### 1️⃣ Empathize - Understanding the Stakeholder

| Question | Answer |
|---|---|
| **Who views this dashboard?** | Marketing Manager, Sales Manager, and the Board of Directors (CEO). |
| **What problem does it solve?** | Unifies fragmented insights from Facebook Ad Manager and disconnected ERP backend sheets into an end-to-end overview. |
| **When & where is it used?** | Daily for revenue tracking, weekly for campaign reviews; accessed on laptops and shared screens during stakeholder status updates. |
| **Why is this analysis needed?** | Capital constraints dictate that every marketing unit spent must be justified by profitability to safeguard operational cash flows. |
| **How do they decide?** | Evaluates ROAS alongside Profit Margin, matching performance gaps across campaigns/SKUs to expand or cut investments. |
| **Pains** | Hours wasted on manual Excel calculations; experiencing strong top-line numbers only to find net losses from high COGS or hidden ad spend. |
| **Gains** | Decisive, data-backed budget scaling; real-time clarity regarding exactly where the breakeven point sits across all product categories. |
| **Key Questions to Answer** | • Which Meta Ads campaign delivers the optimal ROAS return?<br>• What are the weekly trend directions for CPC, CPM, and CTR?<br>• What is the revenue split between Ads Sales and organic Direct Sales?<br>• Which geographical cities generate the highest net Profit Margin?<br>• Which SKUs are our true heroes versus value-destroying items? |

### 2️⃣ Define Point of View - Choosing the Right Angles

| Point of View | Description | Why the stakeholder cares |
|---|---|---|
| **Executive Management Angle** | Focuses on high-level gross revenue, total advertising costs, finalized successful transactions, and final net profit. | The CEO and Board require absolute visibility into budget utilization rates and cash runway safety margins. |
| **Marketing Campaign Angle** | Isolates core platform health metrics: Spend, Impressions, Link Clicks, CTR, CPC, CPM, and individual campaign-level ROAS. | The Marketing Manager needs this tactical view to turn off failing sets, optimize copy, and duplicate winning setups. |
| **Product & SKU Angle** | Breaks down transaction revenue, matching specific ad spend allocations to calculate exact profit margins after COGS. | Empowers the sales and inventory teams to identify flagship fashion products and discontinue unprofitable inventory. |

**Northstar Metrics:**

| Northstar 1 | Northstar 2 |
|---|---|
| **ROAS (Return on Ad Spend)** | **Profit Margin (%)** |
| Formula: `Ads Revenue / Marketing Spend` | Formula: `(Total Revenue - COGS - Marketing Cost) / Total Revenue` |
| Success when: ROAS exceeds defined target baseline | Success when: The profit margin climbs into positive percentage territory and improves consistently. |
| Why this metric: Directly quantifies the revenue-generating efficiency of every dollar funneled into digital advertisements. | Why this metric: Guarantees the brand focuses on sustainable bottom-line health rather than chasing unprofitable top-line scale. |

### 3️⃣ Ideate - Structuring the Dashboard

| | **Page 1: Executive Overview** | **Page 2: Campaign Performance** | **Page 3: Channel & SKU Detail** |
|---|---|---|---|
| **Layer 0 (Scorecards)** | Revenue, Orders, Marketing Cost, ROAS, Profit Margin | Spend, Impressions, CTR, CPC, CPM, Campaign ROAS | Category Revenue, Category Margin, SKU Count, Hero SKU ROAS |
| **Layer 1 (1-dimension breakdown)** | Daily Revenue & Net Profit trends; overall marketing budget usage gauge | Weekly tracking of CPC & CPM shifts; ad costs contrasted against campaign returns | Revenue share & profit margins distributed by item Category; regional sales across Cities |
| **Layer 2 (2-dimension breakdown)** | Channel split (Ads vs Direct) crossed against Customer VIP Tiers | Scatter matrix comparing Impressions vs CTR by campaign; detailed weekly performance grids | Granular SKU profitability matrix (Spend, COGS, Profit, ROAS, ROI for every standalone item code) |

---

## ⚒️ Main Process

1️⃣ **Connect & Load Data** - Linked Power BI to the underlying `Project 3 - Dataset.xlsx` workbook, clearing null headers and structuring datetimes within the core Fact tables.

2️⃣ **Data Modeling** - Modeled a classic Star Schema by creating 1-to-Many relationships originating from the master `danh sach san pham` dimension down to both the `order` and `mkt_camp_by_sku_cost` tables using the `Mã sản phẩm` key, supported by a separate Date Table.

3️⃣ **DAX Measures** - Built essential business metrics, including: `Total Revenue = SUM(order[Giá] * order[Số lượng])`, `Marketing Spend = SUM(mkt_camp_by_sku_cost[Tiền đã chạy theo sản phẩm])`, `ROAS = DIVIDE([Ads Revenue], [Marketing Spend])`, alongside complex `Profit Margin %` formulas.

4️⃣ **Power BI Visualization** - Built clear report pages using an uniform color palette, placing high-level KPI cards at the top (Layer 0), interactive trend breakdowns in the middle (Layer 1), and structured granular tables at the base (Layer 2).

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
> - 🔙 **Back Button** - A navigation arrow sits on the top-left of every detail page, returning the user to the main report view.

> - 💬 **Tooltips** - Hover over any data point on trend charts across all pages to reveal rich contextual detail (revenue breakdown, profit, ROAS) without cluttering the main view.
>
> <p align="center"><img src="Images/Tooltips1.png" width="48%"> <img src="Images/Tooltips2.png" width="48%"></p>
>

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
