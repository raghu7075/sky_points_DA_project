# SkyPoints – Member & Redemption Analytics

## About the Project

This project was developed as part of a Data Analyst technical assessment.

The main goal was to work with airline loyalty program data, clean and validate member information, process redemption transactions, and organize the data so it could be used for further analysis.

While working on this project, I used PySpark and SQL in Databricks to build a data processing workflow covering member records, country-wise data separation, and redemption transaction analysis.

## Tools & Technologies

- **Databricks** – Development environment
- **Python** – Data processing
- **PySpark** – Data transformation and validation
- **SQL** – Table creation, querying and data management
- **Delta Lake** – Table storage and MERGE operations
- **JSON** – Redemption feed processing
- **GitHub** – Project version control and documentation

## What I Worked On

### 1. Data Ingestion and Staging
- Loaded the sample member records and redemption feed.
- Parsed the incoming member data.
- Prepared the data for further processing.

### 2. Data Cleaning and Validation
- Checked mandatory fields and data types.
- Handled invalid and duplicate records.
- Validated member IDs and date fields.
- Derived member age from date of birth.
- Identified stale members based on their last flight date.

### 3. Country-wise Data Processing
- Created separate target tables for USA, India, Philippines, Canada and Australia.
- Maintained a central member master table.
- Used timestamp-based MERGE logic to update member records.
- Simulated a member moving from one country to another and synchronized the country tables.

### 4. Redemption Data Processing
- Read the semi-structured JSON redemption feed.
- Parsed nested redemption information using PySpark.
- Extracted transaction details such as transaction ID, date, partner, miles redeemed and status.
- Validated the transaction records.

### 5. Member and Redemption Integration
- Joined redemption transactions with the current member master.
- Enriched transactions with member name, country and membership tier.
- Generated redemption summaries for analysis.

### 6. Final Data Validation
- Checked duplicate member records.
- Verified country-wise record consistency.
- Checked missing and unmatched member records.
- Validated redemption transactions and member profile joins.

## Results

The following results were obtained using the sample dataset processed in the notebook:

| Metric | Result |
|---|---:|
| Member records processed | 5 |
| Country target records | 5 |
| Duplicate country records | 0 |
| Missing country records | 0 |
| Incorrect country assignments | 0 |
| Redemption transactions | 2 |
| Total miles redeemed | 17,000 |
| Unique members with redemptions | 1 |
| Unmatched redemption records | 0 |

**Final reconciliation:** Passed.

## Project Structure

```text
SkyPoints-Data-Analytics-Project/
│
├── Sky_ppoints_DA_project.ipynb
└── README.md
```

## How to Explore the Project

1. Open the `Sky_ppoints_DA_project.ipynb` notebook.
2. Review the workflow from raw data ingestion to final validation.
3. Run the cells in sequence in a Databricks environment with the required Spark and Delta Lake support.
4. Review the output tables and reconciliation results.

## A Few Things I Learned

Working on this assignment gave me practical experience with PySpark transformations, SQL table management, JSON parsing, Delta Lake MERGE operations and data-quality validation.

One interesting part was handling a member's country movement. I used a simulated update to understand how the central member master and country-specific tables can stay synchronized.

I also learned the importance of validating data at different stages instead of assuming that successfully loaded data is automatically correct.

## Notes and Assumptions

- This project uses sample assessment data, not live customer data.
- The member country movement is simulated for demonstration.
- The sample input is provided within the notebook rather than through a live external ingestion pipeline.
- The source data dictionary identifies Member_Name as a key, while the implementation uses Member_ID as the operational identifier for deduplication and member matching. This assumption should be confirmed with the source data owner.
- The timestamp-based latest-record logic is a prototype; a production implementation should use an authoritative source update timestamp or version.

---

**Project developed as part of a Data Analyst technical assessment.**
