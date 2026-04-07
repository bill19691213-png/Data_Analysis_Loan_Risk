# Loan Risk Portfolio Analysis

A business-focused data analysis project that evaluates loan default risk, identifies loss-heavy portfolio segments, and recommends lending actions using SQL and Power BI.

## Overview

This project analyzes historical consumer loan data to understand which borrower and loan segments contribute the most to portfolio risk. The analysis is designed from a lender’s point of view: not just identifying who defaults more often, but identifying which segments generate a disproportionately high share of losses relative to their share of total originations.

The project is split into two parts:

- **Part 1:** portfolio overview and risk exploration
- **Part 2:** loss concentration analysis and segment-level action priorities

## Business Problem

Lenders need to grow loan volume without taking on excessive default risk. A segment can have a high default rate but still matter little if its volume is small. On the other hand, a moderately risky segment can damage the portfolio if it is large enough.

The goal of this project is to identify the segments（grades,loan terms,purpose,ext）that create the greatest portfolio risk and translate those findings into practical lending recommendations.

## Key Business Question

**Which loan segments generate a disproportionately high share of portfolio losses, and what actions should the lender prioritize to reduce risk while preserving healthy loan volume?**

## Dataset

- Source: Lending Club consumer loan dataset
- Grain: loan-level records
- Key fields used:
  - loan status
  - funded amount
  - term
  - interest rate
  - grade / sub-grade
  - annual income
  - debt-to-income ratio
  - purpose
  - FICO range
  - issue date

## Tools Used

- **SQL (BigQuery):** data cleaning, feature creation, aggregation
- **Power BI:** dashboard design and business storytelling
- **Excel / CSV exports:** output validation and quick checks
- **GitHub:** project documentation and portfolio presentation

## Method

### Part 1 – Portfolio Risk Overview
Built summary tables to evaluate:
- overall default rate
- trends by year
- risk by grade and term
- risk by purpose
- risk by borrower credit quality

### Part 2 – Loss Concentration & Action Prioritization
Built additional SQL tables to answer the main business question:
- `loan_risk_feature_base`
- `segment_loss_concentration`
- `borrower_risk_band`
- `segment_action_matrix`
- `final_priority_segments`

This second phase focuses on:
- identifying segments whose **loss share exceeds their portfolio share**
- separating **material concentrations** from small noisy segments
- translating analysis into **tighten / monitor / maintain** actions

## Dashboard Preview

### Page 1 – Portfolio Overview
<img width="1427" height="801" alt="image" src="https://github.com/user-attachments/assets/6d1560e9-a737-40d8-902d-1aeca2389969" />


### Page 2 – Loss Concentration & Segment Priority
<img width="1427" height="803" alt="image" src="https://github.com/user-attachments/assets/094a5f10-fa55-45fb-8749-ccde377bcd5f" />


## Key Findings

- **60-month debt consolidation loans** were the largest concentration of portfolio risk, especially in weaker credit grades.
- Lower-grade **60-month credit card loans** also contributed an outsized share of losses.
- Safer high-volume segments were concentrated in **A/B grade 36-month loans**, particularly in debt consolidation and credit card categories.
- Borrowers in the **660–699 FICO range with higher DTI** showed elevated default risk and large defaulted funded amounts.
- Portfolio risk was driven not only by borrower quality, but also by the interaction of **grade, term, and purpose**.

## Business Recommendations

- Tighten underwriting for lower-grade **60-month debt consolidation** loans.
- Review pricing and exposure limits for weaker-grade **60-month credit card** segments.
- Maintain or expand safer **36-month A/B** segments that carry meaningful volume but under-index in losses.
- Use **FICO + DTI** combinations as an additional monitoring layer when reviewing portfolio concentration.

## Repository Structure

- `sql/` → all SQL scripts used to build analysis tables
- `images/` → dashboard screenshots used in this README
- `data/` → exported output samples
- `docs/` → supporting notes and methodology details

## How to Reproduce

1. Load the loan dataset into BigQuery
2. Run SQL scripts in the `sql/` folder in order
3. Export output tables for dashboard use
4. Build visuals in Power BI
5. Review dashboard pages for findings and recommendations

## Limitations

- This project focuses on **descriptive and diagnostic analytics**, not predictive modeling.
- Defaulted funded amount is used as a practical proxy for loss concentration.
- Results are based on historical loan performance and should not be interpreted as a production underwriting model.

## Next Steps

Potential future extensions:
- build a default prediction model
- compare pricing vs realized risk more directly
- add explainability methods for borrower-level prediction
- estimate expected loss using PD / LGD style logic

## Author

**Bill Li**  
Data Analyst portfolio project focused on SQL, BI dashboards, and business-driven risk analysis.
