# Customer-Segmentation-Recommendation
Customer Segmentation and Recommendation System
A data engineering and analytics project built with PySpark,
Databricks, Delta Lake, and SQL. The project processes customer,
order, product, consent, and engagement data to create customer segments
and generate targeted recommendations.
Project Overview
Understanding customer behaviour helps businesses improve engagement,
personalize offers, and make better decisions. This project demonstrates
an end-to-end analytics workflow:
1. Generate and prepare sample business data.
2. Process customer and transaction data using PySpark.
3. Calculate customer-level RFM metrics (Recency, Frequency, and
   Monetary value).
4. Assign customers to segments using business rules.
5. Match customer segments with recommended actions.
6. Track recommendation outcomes and engagement events.
7. Run data-quality checks and edge-case tests.
8. Build Gold-layer analytics tables for reporting.
Technology Stack
- Language: Python
- Big data processing: PySpark
- Platform: Databricks
- Storage/table format: Delta Lake
- Querying: SQL
- Version control: Git and GitHub
Architecture
The project follows a source-to-Gold analytics workflow. The generated source
tables, the processed tables (RFM, segments, recommendations, outcomes) and the
Gold tables are all Delta tables in one schema; there are no separate
Bronze/Silver schemas:
Source / Sample Data
        |
        v
Data Preparation and Processing (PySpark)
        |
        v
Customer RFM Analysis
        |
        v
Customer Segmentation
        |
        v
Recommendation Generation
        |
        v
Outcome and Engagement Tracking
        |
        v
Data Quality Checks and Edge-Case Testing
        |
        v
Gold Analytics Tables
        |
        v
Dashboard / Business Reporting
Main Project Modules
  Module                              Purpose
  Data generation and preparation     Creates and prepares sample
customer and business data

  RFM analysis                        Calculates Recency, Frequency, and
Monetary metrics

  Segment rules                       Applies rules to group customers
into meaningful segments

  Action catalog                      Stores possible actions for
different customer needs

  Recommendation generation           Maps customers to relevant
recommended actions

  Outcome tracking                    Stores recommendation outcome
information

  Data quality                        Checks data for quality issues

  Edge-case testing                   Tests scenarios such as conflicting
segments and consent violations

  Gold analytics                      Produces aggregated tables for
reporting
Dashboard preparation               Loads Gold tables and prepares
reporting views and KPIs
Key Data Tables
The project includes source, processing, testing, and analytics tables.
The Gold analytics tables prepared for reporting are:
- gold_segment_summary -- customer counts by segment.
- gold_customer_spending -- customer spending summary.
- gold_recommendation_performance -- recommendation performance
  summary.
- gold_engagement_summary -- customer engagement summary.
Other tables support customer, order, product, consent, recommendation,
and outcome processing.
Example: Query the Gold Tables
Run these examples in a Databricks notebook after the Gold tables have
been created in the workspace.default schema.
# View customer counts by segment
display(spark.table("workspace.default.gold_segment_summary"))

# View customer spending
display(spark.table("workspace.default.gold_customer_spending"))

# View recommendation performance
display(spark.table("workspace.default.gold_recommendation_performance"))

# View engagement summary
display(spark.table("workspace.default.gold_engagement_summary"))
How to Run the Project
1. Sign in to your Databricks workspace.
2. Import or open the project notebooks in your workspace.
3. Run the notebooks in sequence, starting with data generation and
   preparation.
4. Continue through RFM analysis, segmentation, recommendation
   generation, and outcome tracking.
5. Run the data-quality checks and edge-case tests.
6. Run the Gold analytics notebook to create the reporting tables.
7. Run the dashboard-preparation notebook to query the Gold tables and
   prepare KPI outputs.
Important: Run the notebooks in the order defined by their numbering
and dependencies. Table names and schema locations may need adjustment
if you use a different Databricks catalog or schema.

Notebook Run Order

| Notebook | Purpose |
|---|---|
| 01-06 | Generate customers, products, orders, order lines, engagement events, support cases and consent |
| 07 | RFM metrics (delivered orders up to the analysis date) |
| 08 | Segment rules, RFM scores and customer segments |
| 09 | Action catalog |
| 10 | One recommendation per customer |
| 11 | 30-day outcome tracking |
| 12 | Data-quality validation |
| 13 | Edge-case tests on the real pipeline tables (each with an injected control row) |
| 14 | Gold analytics tables |
| 15 | Dashboard views and KPIs |

Data Timeline

The analysis (snapshot) date is 2026-10-30. RFM, segments, support-case checks
and recommendations use only data up to that date. The generated order and
engagement data continue until 2026-11-29, so the 30-day outcome window after
the recommendation date contains data. Orders, events and support cases are
always dated on or after the customer's signup date.
Business Value
This project demonstrates how customer data can be transformed into
useful business insights:
- Identify groups of customers with similar purchasing behaviour.
- Understand customer spending patterns.
- Recommend actions based on customer segments.
- Review recommendation and engagement summaries.
- Use data-quality checks to improve confidence in analytics outputs.
Future Improvements
- Build an interactive Databricks AI/BI dashboard.
- Add more advanced customer segmentation techniques.
- Improve recommendation logic using customer behaviour and feedback.
- Track recommendation outcomes over a clearly defined period.
- Add automated data-quality checks and pipeline scheduling.
- Add project screenshots and sample output to this README.
Project Status
The PySpark processing, segmentation, recommendation workflow,
validation notebooks, and Gold analytics tables have been developed.
Interactive dashboard creation and further enhancements can be added
next.
Author
Madhusmita Panda

Aspiring Data Engineer | PySpark | Python | SQL | Databricks