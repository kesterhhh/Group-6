# Nigerian FinTech Market Analysis Project

## Project Overview
Comprehensive analysis of FinTech product adoption, user preferences, and market positioning in Nigeria using SQL, Power BI, and advanced data analytics techniques.

## Team Members
- Oluwatofunmi Adedayo Fak-Adeniyi (tofunmiadedayo2@gmail.com)
- Kester Ejiofobiri (kestereji@gmail.com)
- Michael Abiodun (m.abiodun130@gmail.com)
- Olamilekan Koyi (tktrades24@gmail.com)

## Analysis Highlights
![DAshboard](1_User_Demographics.jpg)

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
CREATE OR ALTER VIEW vw_service_usage_intensity AS
SELECT 
    age_group,
    SUM(CASE 
        WHEN digital_banking_freq = 'Daily' THEN 3
        WHEN digital_banking_freq = 'Weekly' THEN 2
        WHEN digital_banking_freq = 'Monthly' THEN 1
        ELSE 0 
    END) as digital_banking_intensity
FROM vw_fintech_clean
GROUP BY age_group;
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
[Link to Interactive Dashboard]
