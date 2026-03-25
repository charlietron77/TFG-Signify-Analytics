# TFG-Signify-Analytics
# Data

The data used in this project is proprietary to Signify EMEA and cannot be shared publicly due to corporate confidentiality agreements.

## Data Source

- **System:** SAP PS Module (Project System)
- **Report:** Weekly Deepdive Report
- **Format:** .xlsm (Excel Macro-Enabled Workbook)
- **Storage:** Microsoft SharePoint — 098 Finance folder
- **Frequency:** Weekly uploads by the operations team

## Dataset Structure

The analytical dataset is constructed by consolidating weekly Deepdive snapshots into a longitudinal panel dataset. Each row represents a single WBS element observed at a specific reporting period.

| Category | Variables |
|----------|-----------|
| Identification | Project Definition, WBS Element.1, Sales document, Order, 12NC Code |
| Temporal | Planned Recogn. Date, Actual Recogn. Date, Snapshot_Period |
| Operational | WBS Status, Delivered Quantity, Ordered Quantity, Open POs, Total Hours, PM Hours, SE Hours |
| Financial | Act cost inclu open PO, Cost budget, Act IGM %, Budget IGM %, Material cost, Labour cost, External cost, Material cost expected, Minimum EaC costs, Max EaC IGM% |

## Derived Features (ML Model)

| Feature | Formula |
|---------|---------|
| Cost_Overrun_Ratio | Act cost inclu open PO / Cost budget |
| Labour_Ratio | Labour cost / Act cost inclu open PO |
| External_Ratio | External cost / Act cost inclu open PO |
| OpenPO_Ratio | Open POs / Act cost inclu open PO |
| Delivery_Ratio | Delivered Quantity / Ordered Quantity |
| EaC_Budget_Ratio | Minimum EaC costs / Cost budget |

## Target Variable

**Is_At_Risk** — Binary classification label.  
A WBS element is classified as at risk (1) when its actual IGM% falls more than 2 percentage points below the budgeted IGM%.

## Data Volume

| Snapshot | Date | Observations |
|----------|------|-------------|
| 1 | 09/02/2026 | 9,722 |
| 2 | 23/02/2026 | 9,782 |
| 3 | 02/03/2026 | 9,818 |
| 4 | 09/03/2026 | 9,844 |
| **Total** | | **39,166** |
