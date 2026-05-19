# 🚖 NCR Rides Performance Intelligence Platform

> **A data-driven decision system that helps ride-hailing and logistics companies diagnose operational failures, reduce ride cancellations, and improve service quality — powered by real booking transaction data.**

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Business Goals](#-business-goals)
- [Dataset Information](#-dataset-information)
- [Tools Used](#-tools-used)
- [Data Cleaning & Transformation](#-data-cleaning--transformation)
- [Analysis Focus Areas](#-analysis-focus-areas)
- [Key Insights](#-key-insights)
- [Dashboard](#-dashboard)
- [Recommendations](#-recommendations)
- [Conclusion](#-conclusion)
- [Stakeholders](#-stakeholders)
- [Author](#-author)

---

## 📋 Project Overview

NCR Rides is a ride-hailing company experiencing a **38% operational failure rate** — a performance gap costing significant revenue and eroding customer trust. Without a centralized intelligence system, operations teams relied on manual reports that were too slow to drive real-time decisions.

This project delivers a **self-service Power BI analytics platform** that transforms raw booking transaction data into actionable operational intelligence. The platform enables city managers, operations teams, and business leaders to diagnose failure root causes, monitor service health daily, and make data-backed interventions across drivers, vehicle types, and zones.

---

## 🔴 Business Problem

| # | Problem Statement |
|---|---|
| 1 | **High cancellation rate** causing direct revenue loss across customer- and driver-initiated cancellations |
| 2 | **Supply-demand mismatch** generating "No Driver Found" failures in specific zones and time slots |
| 3 | **Incomplete rides** eroding customer trust and triggering refund claims |
| 4 | **VTAT/CTAT performance** not benchmarked by vehicle type or zone — SLAs impossible to enforce |
| 5 | **Rating gaps** between drivers and customers left unanalysed — poor performers not flagged |

---

## 🎯 Business Goals

### Goal 1 — Reduce Cancellation Rate by 20%
Identify top cancellation triggers by driver, vehicle type, and zone, then build intervention playbooks (incentives, alerts, rules) targeting the **45,000+ failed rides**.

### Goal 2 — Recover Lost Revenue from Failed Rides
Estimate monthly revenue lost to cancellations and incomplete rides based on an **average booking value of $508**, and project ROI for each corrective action.

### Goal 3 — Set and Enforce VTAT/CTAT SLAs
Benchmark arrival time performance per vehicle type and pickup zone, then publish internal SLA targets for operations teams to hold drivers accountable.

### Goal 4 — Improve Quality Scores Across the Fleet
Cross-reference driver ratings, vehicle types, and cancellation reasons to build a **Driver Quality Index** — flagging low performers and rewarding top ones.

### Goal 5 — Build a Live Ops Monitoring System
Deliver a self-service BI dashboard enabling city managers to monitor ride health daily without relying on the data team for manual reports.

### Goal 6 — Eliminate Supply-Demand Dead Zones
Map the **10,500 "No Driver Found" failures** by location and time of day to create targeted driver deployment schedules and surge-readiness alerts.

---

## 🗃️ Dataset Information

The dataset contains **real booking transaction records** with the following schema:

| Column Name | Description |
|---|---|
| `Date` | Date of the booking |
| `Time` | Time of the booking |
| `Booking ID` | Unique identifier for each ride booking |
| `Booking Status` | Status of booking (Completed, Cancelled by Customer, Cancelled by Driver, etc.) |
| `Customer ID` | Unique identifier for customers |
| `Vehicle Type` | Type of vehicle (Go Mini, Go Sedan, Auto, eBike/Bike, UberXL, Premier Sedan) |
| `Pickup Location` | Starting location of the ride |
| `Drop Location` | Destination location of the ride |
| `Avg VTAT` | Average time for driver to reach pickup location (in minutes) |
| `Avg CTAT` | Average trip duration from pickup to destination (in minutes) |
| `Cancelled Rides by Customer` | Customer-initiated cancellation flag |
| `Reason for Cancelling by Customer` | Reason for customer cancellation |
| `Cancelled Rides by Driver` | Driver-initiated cancellation flag |
| `Driver Cancellation Reason` | Reason for driver cancellation |
| `Incomplete Rides` | Incomplete ride flag |
| `Incomplete Rides Reason` | Reason for incomplete rides |
| `Booking Value` | Total fare amount for the ride |
| `Ride Distance` | Distance covered during the ride (in km) |
| `Driver Ratings` | Rating given to driver (1–5 scale) |
| `Customer Rating` | Rating given by customer (1–5 scale) |
| `Payment Method` | Method used for payment (UPI, Cash, Credit Card, Uber Wallet, Debit Card) |

---

## 🛠️ Tools Used
**A Full Stack Project** 

| Tool | Purpose |
|---|---|
| **SQL** | Data querying from the operational database |
| **Excel** | Preliminary data manipulation and validation |
| **Power Query** | Data transformation and loading into the model |
| **Power BI** | Data visualization, reporting, and dashboard delivery |

---

## 🧹 Data Cleaning & Transformation

The following steps were applied to ensure data quality before analysis:

- Standardized column data types: text, whole number, and time formats applied consistently
- Removed duplicate booking records using Power Query's deduplication feature on `Booking ID`
- Converted date format from `yyyy-dd-mm` to `dd-mm-yyyy` for regional consistency
- Separated the `Time` column from the combined date-time field into a standalone column


---

## 🔍 Analysis Focus Areas

The analysis was structured across eight key domains:

1. **Booking Performance Analysis** — Volume trends, completion rates, and booking status distribution
2. **Cancellation Root-Cause Analysis** — Breakdown of customer vs. driver cancellations by reason, zone, and vehicle type
3. **Driver and Customer Rating Intelligence** — Cross-analysis of ratings to identify quality gaps
4. **Vehicle Type Performance Benchmarking** — Comparing completion, cancellation, and timing metrics across vehicle categories
5. **Location-Level Demand Treemaps** — Mapping ride demand by pickup and drop zones to identify high-volume corridors
6. **VTAT/CTAT SLA Tracking** — Arrival time performance analysis across vehicle types and time slots
7. **Payment Method Revenue Segmentation** — Revenue contribution and preference breakdown by payment channel
8. **Incomplete Ride Risk Profiling** — Identifying patterns in rides that start but fail to complete

---

## 💡 Key Insights

### 🔴 Insight 1 — Driver Cancellations Are the Single Largest Failure Category
**18% of all bookings** were driver-initiated cancellations — amounting to approximately **27,000 rides**. The primary reasons include customer health concerns, overcrowding, and personal vehicle issues. Each cancelled ride represents lost fare revenue (avg. $508) and a damaged customer relationship. No early-warning system currently exists to predict or prevent driver-side cancellations before they occur.

---

### 🟠 Insight 2 — 10,500 Bookings Ended With Zero Driver Assignment
**7% of all bookings** resulted in "No Driver Found" — the clearest signal of a geographic and temporal supply gap. Specific zones and time windows have systematically insufficient driver coverage. Without spatial and temporal segmentation, the company cannot proactively deploy drivers or issue surge-readiness alerts before demand spikes hit.

---

### 🟡 Insight 3 — 9,000 Trips Started but Never Finished
**6% of all rides** were marked incomplete — attributable to vehicle breakdowns, sudden customer demand changes, and route-related issues. These incomplete trips trigger refund claims, depress driver ratings, and accelerate customer churn. No real-time mechanism exists to flag rides at risk of incompletion during the trip.

---

### 🔵 Insight 4 — VTAT and CTAT Are Tracked but Never Benchmarked
Vehicle Time at Arrival (VTAT) and Customer Time at Arrival (CTAT) data is collected across all bookings, but no SLA thresholds have been defined or enforced. As a result, the business cannot identify which vehicle types, routes, or time slots are consistently slow — making it impossible to set accurate customer expectations or hold drivers accountable through performance contracts.

---

### 🟣 Insight 5 — Rating Data Is Collected but Not Cross-Analysed
Both driver and customer ratings are captured post-ride, but they are never cross-referenced. Low-rated drivers are not flagged for intervention, and poor-rating patterns by vehicle type or pickup location remain invisible to management. This structural blind spot limits driver accountability programs and quality improvement initiatives.

---

### 🟤 Insight 6 — Revenue Concentration Risk Across Payment Methods
Payment method analysis reveals uneven revenue distribution across UPI, Cash, Credit Card, Uber Wallet, and Debit Card. A high dependency on cash payments in certain zones creates reconciliation challenges and limits the platform's ability to offer digital incentives or loyalty rewards effectively — reducing retention levers available to the business.

---

### ⚫ Insight 7 — Vehicle Type Performance Is Uneven Across the Fleet
Completion rates, VTAT averages, and rating scores vary significantly across Go Mini, Go Sedan, Auto, eBike/Bike, UberXL, and Premier Sedan. Certain vehicle categories outperform others on arrival time but underperform on customer satisfaction — indicating that fleet composition decisions are being made without performance data. Underperforming categories continue to receive bookings without corrective action.

---

### 🔶 Insight 8 — Customer Cancellations Cluster Around Preventable Triggers
Customer-initiated cancellations are not random — they cluster around identifiable triggers such as long VTAT wait times, specific vehicle types, and high-demand time windows. These patterns suggest that a significant share of customer cancellations are preventable with better driver-dispatch logic, real-time ETA communication, and proactive customer alerts when wait times exceed thresholds.

---

## 📊 Dashboard

The Power BI report is structured across **five dashboard pages**, each answering a specific operational question:

---

### Page 1 — Booking Performance Overview
> *Answers: How are bookings distributed across status categories? What is the overall failure rate?*

<!-- 📸 SCREENSHOT PLACEHOLDER -->
> **[<img width="991" height="595" alt="image" src="https://github.com/user-attachments/assets/e2b1e9b9-08c3-4ac0-84dd-0c079d512bc3" />
]**


---

### Page 2 — Cancellation Root-Cause Analysis
> *Answers: Why are rides being cancelled? Who is cancelling — drivers or customers? Which zones and vehicle types have the highest cancellation rates?*

<!-- 📸 SCREENSHOT PLACEHOLDER -->
> **[<img width="988" height="583" alt="image" src="https://github.com/user-attachments/assets/3e474b98-3978-43c1-b896-f691c30206b6" />
]**

---

### Page 3 — VTAT / CTAT SLA Performance
> *Answers: Which vehicle types are slowest to arrive? Which zones consistently exceed acceptable arrival times?*

<!-- 📸 SCREENSHOT PLACEHOLDER -->
> **[<img width="1014" height="597" alt="supply demand ncr" src="https://github.com/user-attachments/assets/d98a3ed0-11e5-4a21-9f0f-7a4af8a975a0" />
]**

---

### Page 4 — Driver & Customer Rating Intelligence
> *Answers: Which drivers and vehicle types have the lowest ratings? Where do rating gaps between drivers and customers exist?*

<!-- 📸 SCREENSHOT PLACEHOLDER -->
> **[<img width="1037" height="594" alt="image" src="https://github.com/user-attachments/assets/4265bc36-f2a7-4d69-a479-0644e770914e" />
]**

---

### Page 5 — Revenue, Demand & Payment Segmentation
> *Answers: How much revenue is being lost to failed rides? Which zones generate the most demand? How is revenue split across payment methods?*

<!-- 📸 SCREENSHOT PLACEHOLDER -->
> **![<img width="1047" height="605" alt="image" src="https://github.com/user-attachments/assets/e5291014-2f0f-45a1-8209-0c97b45cfd10" />
]**


---

## ✅ Recommendations

### R1 — Launch a Driver Cancellation Early-Warning System
**Addresses:** Goals 1 & 2 | **Insight:** Driver cancellations account for 18% of all bookings.

Deploy a predictive alert layer that monitors driver behaviour before a ride is accepted. Flag drivers who have exceeded a rolling cancellation threshold (e.g., 3 cancellations within 48 hours) and temporarily restrict their eligibility to receive new bookings. Simultaneously, create a structured intervention playbook: targeted incentives for drivers who complete high-demand rides in problematic zones, automated SMS nudges when a driver has an incoming booking from a customer with a high rating, and escalation to the Driver Experience team for repeat offenders.

**Expected Impact:** 20% reduction in driver-initiated cancellations → recovery of approximately 5,400 rides/month → estimated **$2.7M+ in monthly revenue recovered** at an average booking value of $508.

---

### R2 — Implement Zone-Level Driver Deployment Scheduling
**Addresses:** Goal 6 | **Insight:** 10,500 "No Driver Found" failures mapped to specific zones and time windows.

Use the demand treemap data to identify the top 10 supply-deficit zones and their peak-failure time windows. Build a weekly driver deployment schedule that incentivises drivers to be online and positioned in those zones during those windows — using surge multipliers, guaranteed minimums, or gamified milestone bonuses. Publish an internal "Dead Zone Alert" dashboard for city operations managers to trigger real-time deployment adjustments.

**Expected Impact:** Reduce "No Driver Found" failures by 40–50% → recovers approximately **4,200–5,250 rides/month**.

---

### R3 — Define and Publish VTAT/CTAT SLA Targets by Vehicle Type and Zone
**Addresses:** Goal 3 | **Insight:** Arrival time data collected but no benchmarks enforced.

Using the VTAT/CTAT analysis, calculate the 75th percentile arrival time for each vehicle type and pickup zone combination. Publish these as internal SLA thresholds for the operations team. Build a Power BI alert system that flags breaches daily. Tie SLA compliance to driver performance scores — with SLA-compliant drivers receiving priority in dispatch queues and persistent violators receiving coaching or temporary queue deprioritisation.

**Expected Impact:** Measurably improves arrival time consistency, reduces customer-side cancellations caused by long waits, and enables the Customer Success team to set accurate ETA expectations in the app.

---

### R4 — Build a Driver Quality Index
**Addresses:** Goal 4 | **Insight:** Rating data collected but never cross-analysed.

Construct a composite Driver Quality Index (DQI) combining: driver rating score, cancellation rate, VTAT average, and incomplete ride frequency — weighted by ride volume to avoid penalising low-volume outliers. Segment drivers into four tiers: Elite, Standard, At-Risk, and Suspended. Automate weekly DQI refresh in Power BI. Reward Elite drivers with preferential booking allocation, bonuses, or public recognition. Enrol At-Risk drivers in a structured reactivation program before suspension.

**Expected Impact:** Improves average driver rating across the fleet, reduces repeat low-quality ride experiences, and creates a scalable driver accountability culture without requiring manual data review.

---

### R5 — Create a Real-Time Incomplete Ride Risk Flag
**Addresses:** Goal 5 | **Insight:** 9,000 incomplete trips — each triggering refunds, low ratings, and churn.

Build a rule-based risk scoring model that flags ongoing rides likely to become incomplete. Risk triggers include: vehicle type with high historical incompletion rate, ride distance exceeding zone-average by >30%, driver with prior incomplete ride in the last 7 days, or trip duration exceeding 2× the CTAT SLA for that route. When a ride crosses the risk threshold, alert the operations team to proactively contact the driver or reroute support resources.

**Expected Impact:** Reduce incomplete rides by 30% → saves approximately 2,700 rides/month → **reduces refund liability and churn from high-value customers**.

---

### R6 — Accelerate Digital Payment Adoption in Cash-Heavy Zones
**Addresses:** Goal 2 (revenue recovery) | **Insight:** Revenue concentration risk from cash-dependent zones.

Identify zones with >50% cash payment share and run targeted digital adoption campaigns: offer a one-time discount for first digital payment, integrate NCR Wallet onboarding nudges post-ride, and partner with local fintech platforms for seamless UPI setup. Track adoption monthly in the payment segmentation dashboard. This unlocks digital incentive tools (cashback, loyalty rewards) that are currently inaccessible to cash-dependent customers.

**Expected Impact:** Expands retention levers, reduces cash reconciliation costs, and enables loyalty program integration.

---

### R7 — Retire or Restructure Underperforming Vehicle Categories
**Addresses:** Goal 4 & 5 | **Insight:** Vehicle type performance varies significantly across the fleet.

Use the vehicle benchmarking analysis to identify categories that consistently underperform across VTAT, completion rate, and customer rating. For each underperformer, evaluate whether the issue is driver-side (training, incentives), vehicle-side (maintenance, capacity), or demand-side (wrong category for the zone). Categories that remain below threshold after a 60-day intervention window should be retired from specific zones or replaced with higher-performing vehicle types.

**Expected Impact:** Improves overall fleet efficiency, concentrates resources on high-performing categories, and raises the platform's average service quality score.

---

## 🏁 Conclusion

NCR Rides entered this project with a **38% operational failure rate** and no systemic way to understand why rides were failing or where to intervene. This analysis reveals that the failure is not random — it is structured, predictable, and addressable.

The data tells a clear story: **driver cancellations, supply-demand dead zones, and incomplete rides** are three distinct but interconnected failure modes that together cost the business tens of thousands of rides and millions in monthly revenue. Overlaid on these is a quality management gap — rating data collected but never actioned, arrival time tracked but never benchmarked, and vehicle performance measured but never used to drive fleet decisions.

The NCR Rides Performance Intelligence Platform directly closes these gaps. It gives every stakeholder — from the City General Manager to the Driver Experience Lead — a real-time, self-service view of operational health, without depending on the data team for manual reports.

With the seven recommendations in this report implemented over a rolling 90-day playbook, NCR Rides can realistically:

- **Recover 20%+ of lost rides** through driver cancellation intervention
- **Eliminate 40–50% of supply dead zones** through data-driven deployment scheduling
- **Reduce incomplete trips by 30%** through real-time ride risk flagging
- **Raise fleet-wide quality scores** through the Driver Quality Index
- **Unlock digital retention tools** by accelerating payment method modernisation

The platform is built to scale. As more data flows through the system, the insights sharpen, the interventions become more precise, and the gap between operational failure and operational excellence narrows. This is not just a reporting tool — it is the foundation of a **data-driven operations culture** at NCR Rides.

---

## 👥 Stakeholders

| Role | Primary Use Case |
|---|---|
| Operations Manager | Monitor daily ride health; track cancellation and completion KPIs |
| Head of Driver Experience | Review driver DQI; manage intervention and reward programs |
| Customer Success Lead | Identify rating gaps; reduce customer churn from poor ride experiences |
| Business Intelligence Team | Maintain and extend the Power BI model; build new analytical layers |
| City General Manager | High-level performance overview; zone-level deployment decisions |
| Product Manager (Dispatch & Routing) | Use VTAT/CTAT and supply-gap data to improve dispatch algorithm logic |

---
## Project Files
📊 Excel sheets([dataset](https://docs.google.com/spreadsheets/d/1KqhRB4lfEyP5fWDr-IYt96yuXEsMMyaV/edit?usp=drive_link&ouid=106853209004558054249&rtpof=true&sd=true) \
📂 Weather Checking Habits Analysis[ Dashboard](https://drive.google.com/file/d/1UkBOFbQaJMQOK0L32ubvpb91_CTKpHhE/view?usp=drive_link) 

---
## 👤 Author

**Ngwuta-Cletus Peter | The Full Stack Data Analyst**

## contact:
📩 Email: <Ngwutacletuspeter@gmail.com>\
📮 Linkdin: <https://www.linkedin.com/in/peter-ngwuta-cletus-290281292/>

---

*© Cletus Peter | The Full Stack Data Analyst*
