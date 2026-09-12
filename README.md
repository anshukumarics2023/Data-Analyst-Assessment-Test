## Data Analyst Assessment — Olist E-Commerce Analysis

Candidate: Anshu Kumari College: Meerut Institute of Technology Assessment for: VirtuBox Infotech Private Limited Contact: anshu.kumari.cs.2023@mitmeerut.ac.in

1. Overview

This repository contains my submission for the Data Analyst Assessment. The brief asked me to independently pick a public dataset, define a business problem, clean and analyze the data, and present findings to a non-technical management audience.

I chose the Brazilian E-Commerce Public Dataset by Olist — 9 linked tables covering ~99,400 orders placed on the Olist marketplace between 2016 and 2018, spanning the full order lifecycle: purchase → payment → fulfilment → delivery → review.

Business problem investigated: why customer satisfaction and delivery performance vary across regions and product categories, and whether delivery reliability is a controllable lever management can use to reduce dissatisfaction and unlock regional growth.

2. Repository Contents
File	Description
Data_Analyst_Assessment_Anshu_Kumari.docx	Full written answers to Questions 1–7, AI-usage disclosure, and final-submission checklist. Each question reproduces the original assessment prompt followed by my answer.
Olist_Data_Processing_Q3.ipynb	Colab-ready Python/Pandas notebook that downloads the raw Olist CSVs, cleans them, joins all 9 tables into one analysis-ready fact table, and prints the real evidence used in the Q3 answer. Outputs processed_data.csv, category_summary.csv, state_summary.csv.
Data_Analyst_Assessment_Presentation.pptx	7-slide management presentation (Business Problem → Data & Methodology → Key Findings → Deep-Dive Insight → Recommendations → Expected Business Impact → Limitations & Next Steps).
README.md	This file — methodology summary and repo guide.

Not included in this repo: the Google Sheet (all worksheets: Data, Q1–Q10, Processed Data) and the Google Looker Studio dashboard, since both are Google-hosted, shareable-link deliverables rather than files. Their expected content and structure are documented in the .docx (Question 8) and generated directly by the notebook below.

3. How to Reproduce the Analysis
Open Google Colab → File → Upload notebook → upload Olist_Data_Processing_Q3.ipynb.
Runtime → Run all. The first run asks you to authenticate a free Kaggle account (via kagglehub) — no manual file download needed.
The notebook will:
Load all 9 raw Olist CSVs and report missing values / duplicates per table
Flag (not delete) cancelled/undelivered orders
Translate and standardize product categories (Portuguese → English)
Convert date columns and derive delivery_days, delivery_delay_days, is_late
Remove duplicate records
Flag outliers (e.g. freight cost exceeding item price)
Join everything into one order-item-level fact table
Export processed_data.csv, category_summary.csv, state_summary.csv
Import processed_data.csv into the Processed Data worksheet of the Google Sheet, and use the printed "Q3 EVIDENCE" blocks to fill in the Q3 explanation table.
Use category_summary.csv / state_summary.csv as source data when building the Looker Studio dashboard (Question 8).

Tech stack: Python, Pandas, NumPy, Google Colab, Google Sheets, Google Looker Studio.

4. Analysis Questions & Hypotheses (Question 2)

Analysis questions:

Which product categories and states generate the most revenue?
How does actual delivery time (vs. estimate) affect the customer review score?
Which regions experience the longest delivery delays, and why?
Does payment method / instalment count correlate with order value?
Is revenue concentrated among a small number of sellers or categories?

Hypotheses tested:

H1: Orders delivered later than the estimated date receive significantly lower review scores than on-time orders.
H2: Customers in the North/Northeast experience longer delivery times and lower satisfaction than the Southeast.
H3 (stretch): Higher-value orders are more likely to be paid via multi-instalment credit card than single-payment or boleto.
5. Key Findings (Question 4)
#	Insight	Recommendation
1	Late deliveries are strongly associated with lower review scores	Set a delivery-delay SLA with proactive alerts
2	Revenue is geographically concentrated in the Southeast (SP, RJ, MG)	Pilot a regional fulfilment partnership in 1–2 Northeast states
3	A small number of categories (bed & bath, health & beauty, sports & leisure) drive most revenue	Focus merchandising spend on top 5 categories
4	Instalment-based credit card payment dominates higher-value orders	Keep/expand flexible instalment options
5	Freight cost is a disproportionately large share of order value for low-price items	Introduce a minimum-basket free-shipping threshold

Full evidence, business impact, and reasoning for each insight are in the .docx (Question 4).

6. Surprising Result (Question 5)

Remote Northern/Northeastern states have longer absolute delivery times as expected, but their review scores are not proportionally worse — satisfaction appears to track delay relative to the promised delivery date, not absolute wait time. This is reported as a plausible, data-supported hypothesis rather than a proven cause (see .docx for full reasoning and the additional analysis performed to check it).

7. Limitations (Question 6)
No cost/margin data — profitability by category/seller cannot be calculated, only inferred from revenue.
Reviews are self-selected (only survey respondents) and may not represent the full customer base.
Dataset covers 2016–2018 only; findings are directional and should be validated against current data.
Individual sellers/carriers cannot be isolated as the cause of late deliveries — the dataset does not name logistics providers.
8. Recommendations (Question 7)

Prioritized by impact and feasibility:

Delivery SLA + proactive alerts (highest priority — low cost, addresses the single strongest lever on satisfaction)
Free-shipping/bundling threshold for low-price categories (low cost, fast to test)
Regional fulfilment pilot in the Northeast (highest potential impact, highest cost/complexity — sequenced last)

Each recommendation's owner, expected outcome, and success metric are detailed in the .docx.

9. How AI Was Used (Question 10)
Tool used: Claude (Anthropic)
Used for: structuring the analysis approach, drafting the data-cleaning rationale and insight/recommendation write-ups, building the presentation deck, and organizing this README.
Where AI helped: translating raw processing steps into a clear "change / why / consequence" table format for a non-technical audience.
Where I verified/corrected AI output: all dataset statistics and category/region rankings were checked against the notebook's actual printed output rather than accepted at face value, since aggregate figures can shift slightly depending on join logic and duplicate-handling choices.
10. License / Data Source Attribution

Dataset: Brazilian E-Commerce Public Dataset by Olist, released publicly on Kaggle by Olist Store. Used here strictly for educational/assessment purposes. No proprietary or confidential data from VirtuBox Infotech is included in this repository.
