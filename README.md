# Automated-Sales-VS-Finance-Reconciliation-Engine
This project delivers an automated, audit-ready data validation and reconciliation pipeline designed to align revenue logs between Sales CRM exports and Finance General Ledger (GL) systems. By embedding automated validation controls and full-outer join reconciliation logic, the model eliminates manual auditing overhead, isolates data entry errors at ingestion, and identifies all sources of financial variance.

<br>

**PROJECT OVERVIEW**
<br>Modern commercial operations frequently experience financial reporting friction due to discrepancies between CRM Sales tracking systems (closed deals) and General Ledger (GL) Finance ERP systems (posted transactions). In manual environments, unbilled revenue, direct ledger adjustments, and early-payment discounts create unexplained financial variances.

Furthermore, raw CRM exports frequently contain data quality defects (blank customer emails, duplicate transaction IDs, and negative amounts). Without an automated validation and reconciliation layer, these errors distort executive revenue metrics, delay month-end financial closing, and increase audit risk.

<br>

The raw files can be found [here](https://github.com/SalamiEritosin/Automated-Sales-VS-Finance-Reconciliation-Engine/tree/main/Files/raw_files)

<br> The reconciliation engine [here](https://github.com/SalamiEritosin/Automated-Sales-VS-Finance-Reconciliation-Engine/tree/main/Files/reconcilliation_engine)


<br>

**PROJECT OBJECTIVES**
<br>
1.	Automated Validation: Build automated Power Query validation logic on raw CRM exports to flag duplicates, missing inputs, and logic violations prior to processing.

2.	Reconciliation Engine: Construct a Full Outer Join reconciliation model comparing Sales and Finance datasets on Transaction_ID.

3.	Variance Classification: Automatically categorize variances into Matched, Missing in Finance (Unbilled Revenue), Missing in Sales (Direct GL Entries), and Value Mismatches (Discounts/Fees).

4.	Executive Reporting: Generate an audit-ready summary dashboard quantifying net exposure and exception counts.

<br>

**KEY ANALYTICAL FINDINGS:**


1.	Total Sales Revenue Reported (CRM): **$207,850.00**

2.	Total Finance Revenue Posted (GL): **$214,400.00**

3.	Gross Discrepancy (Net Variance): **-$6,550.00** (Finance exceeds Sales)

4.	Variance Root-Cause Breakdown:

   <br> [here](https://github.com/SalamiEritosin/Automated-Sales-VS-Finance-Reconciliation-Engine/blob/main/Files/result/Reconcilliation.png)

   <br>

**Unbilled CRM Revenue Exposure ($47,600.00 across 5 Orders)**
<BR>**Status:** Missing in Finance

**Affected Orders:** ORD-1013 ($18,400.00), ORD-1019 ($9,500.00), ORD-1020 ($4,200.00), ORD-2007 ($4,300.00), ORD-2008 ($11,200.00)

**Finding:** Represents $47.6K in closed customer deals that have not been invoiced or posted in the General Ledger.

<br>

 **Direct GL Cash Collections ($54,750.00 across 5 Orders)**
<BR>**Status:** Missing in Sales

**Affected Orders:** ORD-1014 ($25,250.00), ORD-1033 ($5,300.00), ORD-1034 ($11,000.00), ORD-2099 ($7,800.00), ORD-2100 ($5,400.00)

**Finding:** Finance has received and posted $54.75K directly into the General Ledger without corresponding deal logging in CRM, leading to inaccurate sales reporting.

<br>

**Pricing & Fee Discrepancies**
<BR>**Status:** Amount Mismatch
Impact: transaction processing fees deducted at settlement, creating systematic variances between CRM gross contract values and GL net cash receipts.  

<br>

5.	**Data Quality Exceptions:** Flagged 4 high-priority data hygiene defects in the Sales pipeline (ORD-1003 missing email, ORD-1007 invalid email format, ORD-1011 duplicate record, ORD-1014 negative sales value).

<br>

**BUSINESS IMPACT:**

By replacing manual VLOOKUP routines with an automated Power Query ETL workflow, this engine reduces month-end reconciliation time from days to minutes, enforces strict data governance prior to financial reporting, and provides leadership with complete confidence in core revenue metrics.



