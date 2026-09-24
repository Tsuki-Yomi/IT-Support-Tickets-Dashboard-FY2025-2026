# IT Support Ticket Analysis — Power BI Dashboard

An interactive Power BI dashboard analyzing 12 months of IT support ticket activity, built to demonstrate data modeling, DAX, and dashboard design skills using patterns drawn from my own experience as an IT In Charge.

**[Download the .pbix file](./IT%20Dashboard.pbix)** (open in Power BI Desktop) · Screenshots below

---

## Background

In my role as IT In Charge at a scaffolding trading and manufacturing company, I handle daily support tickets across quotations, invoicing, purchase orders, approvals, and system access — averaging around 3 tickets a day across a 30+ user ERP environment.

I wanted a project that reflected that real workload rather than a generic public dataset, but our ticket logs live in a vendor support portal with no export function. So I **simulated a dataset modeled on the real category mix, department split, resolution-time patterns, and seasonal (quarter-end) spikes I actually see in the role** — including two real process changes I was involved in — and built this dashboard to analyze it.

**Note on the data:** this dataset is simulated, not exported from a live system. It's built to reflect real operational patterns, not to reproduce exact company figures. Any numbers below describe the simulated dataset, not company records.

## What the dashboard shows

- **~1,050 tickets** across a 12-month period, broken down by category (Quotations & Sales Orders, Invoicing, Purchase Orders & Requisitions, Approval Cycle, Goods Receiving, Login/Access, Inventory Valuation), department (Sales, Procurement, Accounting, and a smaller Factory/HR tail), and priority.
- **Resolution time distribution** — most tickets resolve same-day to 2 days, with a visible tail of longer, vendor-escalated cases.
- **Quarter-end volume spikes**, consistent with real closing-period workload increases in finance-heavy ERP environments.
- **Two before/after process-improvement stories**, isolated using dedicated DAX measures:
  - **Approval Cycle tickets dropped ~54%** (average per month) after introducing an email notification that alerts users when a transaction reaches their stage of an approval cycle — a fix I identified and coordinated with our ERP vendor's technical team after noticing recurring delays caused by forgotten approvals.
  - **Recurring user-error tickets declined ~11%** across the year, modeled on the effect of documentation and light training aimed at recurring, preventable issues.

## How it's built

- **Data modeling:** star-schema style model with a dedicated Date table (built with `CALENDAR()`, marked as an official Date table) related to the main Tickets fact table — rather than relying on Power BI's automatic date hierarchy.
- **Power Query:** type correction, a custom `Resolution_Bucket` column grouping raw resolution days into readable buckets, and Month/Quarter extraction columns.
- **DAX:** measures for ticket totals, average resolution time, escalation rate, and two isolated period-over-period comparisons — including a 3-month moving average measure to separate genuine trend from quarter-end seasonal noise (built using `DATESINPERIOD` with explicit `ALL()` filter-context handling).
- **Report design:** a single interactive page with Department/Priority/Date slicers, KPI cards, and six supporting visuals, styled with Power BI's Accessible Tidal theme.

## Skills demonstrated

`Power BI` · `DAX` · `Power Query (M)` · `Data Modeling` · `Star Schema Design` · `Time Intelligence` · `Data Visualization` · `Dashboard Design`

## Screenshots

![Full dashboard, unfiltered](./screenshots/Full%20Dashboard%20-%20Unfiltered.png)

*Full dashboard view, no filters applied.*

![Filtered to High Priority Procurement tickets](./screenshots/Filtered%20to%20High%20Priority%20Procurement.png)

*Filtered to High Priority tickets in Procurement — demonstrates the Department/Priority/Date slicers.*

![Approval Cycle tickets before vs after email notification](./screenshots/Approval-Related%20Tickets%20Before-After.png)

*Close-up of the Approval Cycle before/after comparison — the dashboard's key process-improvement finding.*

---

**Author:** Mamoon Al Tawashi — IT In Charge, transitioning into Data Analytics.
[LinkedIn](http://www.linkedin.com/in/mamoon-al-tawashi-098a52234) · mamoonaltawashi@gmail.com
