# Nigerian FinTech Market Analysis Project

## Project Overview
Comprehensive analysis of FinTech product adoption, user preferences, and market positioning in Nigeria using SQL, Power BI, and advanced data analytics techniques.

## Team Members
- Oluwatofunmi Adedayo Fak-Adeniyi (tofunmiadedayo2@gmail.com)
- Kester Ejiofobiri (kestereji@gmail.com)
- Michael Abiodun (m.abiodun130@gmail.com)
- Olamilekan Koyi (tktrades24@gmail.com)

## Analysis Highlights
![DAshboard](Fintech-Group.jpg)

### Key Metrics
- Total Users: 38
- Daily Active Users: 71%
- Expert Users: 50%
- Primary Age Groups: Middle Adult (52.6%), Young Adult (31.6%)

### Service Usage Analysis
1. Most Popular Services:
   - Digital Banking (2.63 engagement score)
   - Mobile Payments (1.97 engagement score)
   - Investment Services (0.74 engagement score)

2. Platform Adoption:
   - Opay: 16 expert users
   - Kuda: 11 expert users
   - Moniepoint: 10 expert users
   - PalmPay: 10 expert users

## Technical Methodology

### Data Processing
1. SQL Implementation:
   - Created cleaned views using CTEs
   - Implemented service usage analysis
   - Platform expertise calculations
   - Feature priority metrics

2. Power BI Analysis:
   - DAX measures for user metrics
   - Engagement scoring
   - Platform adoption tracking
   - Service usage intensity

### Analysis Framework
```sql
-- Example of our analysis approach
-- STEP 1: Data Cleaning and Standardization
-- Run this block first
CREATE OR ALTER VIEW vw_fintech_clean AS
WITH age_categories AS (
    SELECT 
        RespondentID,
        CASE 
            WHEN Age = '18-24' THEN 'Young Adult'
            WHEN Age = '25-34' THEN 'Middle Adult'
			  WHEN Age = '35-44' THEN 'Senior Adult'
            WHEN Age = '45+' THEN 'Elder'
        END AS age_group,
        Age as original_age
    FROM fintech_response
),
service_familiarity AS (
    SELECT 
        RespondentID,
        COALESCE(Moniepoint, 'Not Familiar') as Moniepoint,
        COALESCE(Kuda, 'Not Familiar') as Kuda,
        COALESCE(Opay, 'Not Familiar') as Opay,
        COALESCE(Paystack, 'Not Familiar') as Paystack,
        COALESCE(Piggyvest, 'Not Familiar') as Piggyvest,
        COALESCE(Cowrywise, 'Not Familiar') as Cowrywise,
        COALESCE(FairMoney, 'Not Familiar') as FairMoney,
        COALESCE(Palmpay, 'Not Familiar') as Palmpay,
        COALESCE(Flutterwave, 'Not Familiar') as Flutterwave,
        COALESCE(Paga, 'Not Familiar') as Paga
    FROM fintech_response
)

SELECT 
    f.RespondentID,
    ac.age_group,
    ac.original_age,
    f.Which_of_the_following_financial_services_do_you_currently_use as current_services,
    f.Digital_Mobile_Banking as digital_banking_freq,
    f.Micro_Lending_Platforms as lending_freq,
    f.Savings_Investment_Platforms as investment_freq,
    f.Cryptocurrency_Services as crypto_freq,
    f.Blockchain_Services as blockchain_freq,
    f.Mobile_Payment as mobile_payment_freq,
    f.For_the_services_you_ve_used_how_often_do_you_use_them_Remittance_Solutions as remit_freq,
    f.Crowdfunding_Platforms as crowd_freq,
    f.FinTech_Adoption_trends as adoption_trends,
    f.Fee_Sensitivity_Score as fee_sensitivity,
    f.What_s_most_important_to_you_in_a_financial_service as priority_features,
    f.Education_Level as education,
    f.How_do_you_prefer_to_access_financial_services as access_pref,
    sf.Moniepoint, sf.Kuda, sf.Opay, sf.Paystack, sf.Piggyvest,
    sf.Cowrywise, sf.FairMoney, sf.Palmpay, sf.Flutterwave, sf.Paga
FROM fintech_response f
JOIN age_categories ac ON f.RespondentID = ac.RespondentID
JOIN service_familiarity sf ON f.RespondentID = sf.RespondentID;
```

## Key Findings & Recommendations

### Market Positioning
1. Product Priorities:
   - Focus on digital banking and mobile payments
   - Develop integrated investment features
   - Consider crypto services for young adults

2. Pricing Strategy:
   - Implement tiered pricing based on usage
   - Target fee sensitivity in middle adult segment
   - Bundle services for multi-platform users

3. Marketing Approach:
   - Primary: Middle Adults (25-34)
   - Secondary: Young Adults (18-24)
   - Focus on digital banking convenience

## Project Structure
```
├── data/
│   ├── raw/
│   └── processed/
├── sql/
│   ├── cleaning_scripts/
│   └── analysis_queries/
├── powerbi/
│   ├── measures/
│   └── visualizations/
└── documentation/
    ├── methodology/
    └── findings/
```

## Challenges & Limitations
- Limited sample size (38 users)
- Data gaps in platform usage patterns
- Time constraints in analysis depth

## Tools Used
- SQL Server
- Power BI
- DAX
- Data Analysis
- Visualization Tools

## Dashboard Access
Link to Interactive Dashboard[here](https://app.powerbi.com/view?r=eyJrIjoiMDY2NTAxYjUtYjI1My00MDc0LTliYTgtYTZhYmNlYjJmMGMzIiwidCI6IjUxN2QzNTAyLTI5MDEtNGRlMi1hODdiLTk1YzUwN2E5YTA4OCJ9)

