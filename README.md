Open Source Buffalo – City Budget Tracker

A civic-tech tool for exploring, monitoring, and visualizing the City of Buffalo’s budget through open data APIs.

This repository powers OpenSourceBuffalo.com’s budget dashboard, which connects directly to the City’s open data portal to provide a transparent, interactive view of Buffalo’s revenues, expenditures, payroll, and vendor spending.

Overview

The City of Buffalo publishes the current City Budget Documents in PDF format here:
https://www.buffalony.gov/1778/2025-2026-Adopted-Budget

The City of Buffalo Budget Tracker uses live APIs from the City's open data portal to break down the city’s finances by department, program, and fund.
It allows developers to analyze spending patterns, visualize year-to-date performance, and compare adopted vs. actual expenditures.

Data Sources (Socrata APIs)
| Purpose                       | API Name    | Endpoint                                                                                                 |
| ----------------------------- | ----------- | -------------------------------------------------------------------------------------------------------- |
| **Appropriations / Expenses** | `xy5k-883e` | (https://data.buffalony.gov/resource/xy5k-883e.json) |
| **Revenues**                  | `cvx5-9drv` | (https://data.buffalony.gov/resource/cvx5-9drv.json) |
| **Payroll (Employees)**       | `hm3x-8br6` | (https://data.buffalony.gov/resource/hm3x-8br6.json) |
| **Checkbook (Vendors)**       | `bktd-jwim` | (https://data.buffalony.gov/resource/bktd-jwim.json) |

Translating the budget to open data

Using Socrata Open Query Language (SoQL) developers can query the City's open data.  See Socrata documentation here: https://dev.socrata.com/

Buffalo’s financial system uses segment codes that define the hierarchy of budget data:

| Segment               | Field                       | Meaning             | Example                                  |
| --------------------- | --------------------------- | ------------------- | ---------------------------------------- |
| **Segment 2**         | `segment2code` / `segment2` | Department          | `01-COMMON COUNCIL` → **COMMON COUNCIL** |
| **Segment 3**         | `segment3code` / `segment3` | Program or Division | `311 CALL CENTER`                        |
| **Segment 5**         | `segment5code` / `segment5` | Appropriation Type  | `PERSONAL SERVICES`                      |
| **Segment 8**         | `segment8code` / `segment8` | Revenue Source      | `PROPERTY TAXES`                         |
| **Object Code**       | `objectcode` / `object`     | Budget Line Item    | `1010 Regular Pay`, `4020 Supplies`      |
| **Organization Code** | `organizationcode`          | Sub-unit identifier | e.g., department cost center             |

Here's developer documentation for the City's Expendatures dataset:
https://dev.socrata.com/foundry/data.buffalony.gov/bktd-jwim
