 Bykea Ride Analytics — Power BI Dashboard & Data Analysis

A end-to-end data analytics project analyzing **153,000 ride-booking records** from Bykea's Karachi operations (2024), covering booking volume, revenue, cancellations, payment behavior, and service quality — built with **Power Query, DAX, and Power BI**.


---

## 📊 Project Overview

This project analyzes a full year (2024) of ride-hailing bookings across Karachi to uncover:
- Booking completion vs. cancellation trends
- Revenue drivers by vehicle type, payment method, and time of day
- Root causes behind customer and driver cancellations
- Customer retention and service quality performance

The raw dataset was intentionally messy (duplicate IDs, inconsistent casing, malformed dates, null placeholders) — a core part of this project was cleaning it into an analysis-ready model before building the dashboard.

---

## 🗂️ Repository Contents

| File | Description |
|---|---|
| `Bykea_Ride_Analysis.pbix` | Power BI dashboard file (3 pages: Home, Revenue, Summary) |
| `rideBookings.csv` | Raw source dataset (153,000 rows) |
| `Bykea_Ride_Analytics_Report.pdf` | Full written analysis report with charts, findings & recommendations |
| `README.md` | This file |
| 'Bykea Ride Analysis png'
---

## 🧹 Data Cleaning (Power Query)

- Removed 4,233 duplicate `Booking ID` records
- Stripped malformed quote-wrapping from `Booking ID` / `Customer ID` fields
- Standardized 35 raw `Vehicle Type` text variants into 7 clean categories
- Standardized 25 raw `Booking Status` variants into 5 categories
- Converted `"null"` string placeholders in `Payment Method` into true nulls
- Parsed inconsistent date/time formats into proper date types
- Cleaned and title-cased 150+ `Pickup`/`Drop Location` values

## 📐 Key DAX Measures

```DAX
Completion Rate = DIVIDE([Completed Bookings], [Total Bookings])

Revenue per KM = DIVIDE(SUM(finance_transactions[Booking Value]), SUM(finance_transactions[Ride Distance]))

Customer Retain Rate = DIVIDE([Repeat Customers], [Total Unique Customers])

Premium Peak Hour Index =
DIVIDE(
    CALCULATE([Premium Bookings], 'Day_Part'[Day_Part] IN {"Morning","Evening"}),
    [Premium Bookings]
)

Service Quality Score = DIVIDE(AVERAGE(Driver Ratings) + AVERAGE(Customer Rating), 2) / 5 * 100
```

## 📈 Dashboard Pages

1. **Home** — KPI cards (Total Bookings, Completion Rate, Total Revenue, Avg Booking Value), booking trend, status breakdown, vehicle-type table, payment method chart
2. **Revenue** — Cancellation reason breakdowns (customer & driver), ride distance trend, ratings by vehicle type
3. **Summary** — Customer Retain Rate, Revenue per KM, Premium Peak Hour Index, monthly revenue trend, Service Quality Score gauge

---

## 🔑 Key Findings

- ✅ **62.00%** completion rate — driver-side cancellations (**18.01%**) are the single largest loss category
- 🚗 **Rickshaw** leads both volume and revenue (Rs 12.88M, 27% of total)
- 💳 **75.1%** of revenue is digital (EasyPaisa, JazzCash, cards) vs. 24.9% cash
- ⏰ Morning + Evening peak windows drive **60%** of daily revenue
- 🔁 Only **2.45%** of customers rebook — the biggest growth opportunity identified
- ⭐ Service Quality Score: **86.4 / 100**, consistent across all vehicle types

Full findings, charts, and recommendations are in [`Bykea_Ride_Analytics_Report.pdf`](./Bykea_Ride_Analytics_Report.pdf).

---

## 🛠️ Tools Used

- **Power BI** — data modeling, DAX, dashboard design
- **Power Query** — data cleaning and transformation
- **Python (pandas)** — exploratory data analysis and reporting

---

## 👤 Author

**Aqsa Ayub**
Data Analyst | Power BI 


