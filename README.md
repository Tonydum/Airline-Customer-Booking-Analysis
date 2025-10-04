# ✈️ Airline Customer Booking Analysis  

## 📑 Table of Contents  
1. [Project Overview](#-project-overview)  
2. [Dataset](#-dataset)  
3. [Tools & Skills Used](#-tools--skills-used)  
4. [Data Model](#-data-model)  
5. [KPIs & Measures](#-kpis--measures)  
6. [Dashboard Highlights](#-dashboard-highlights)  
7. [Business Impact](#-business-impact)  
8. [Recommendations](#-recommendations)  
9. [How to Use](#-how-to-use)  
10. [Next Steps](#-next-steps)  

---

## 📌 Project Overview  
This project analyzes airline booking data to identify customer booking behavior, revenue trends, and areas for operational improvement. The dashboard helps airline managers understand how customers book flights (timing, channel, class), and where revenue is gained or lost.  

Objectives:  
- Analyze booking trends across customer demographics and travel classes.  
- Track revenue and booking patterns by channel (web, mobile, agent).  
- Identify opportunities for upselling and improving booking experiences.  

---

## 📊 Dataset  
- **Source**: Airline customer bookings dataset (X records, Y features).  
- **Features include**:  
  - Customer demographics: Age, Gender, Location  
  - Booking details: Class (Economy, Business, First), Booking Channel (Mobile, Web, Agent)  
  - Travel details: Destination, Departure Date, Lead Time (days between booking and flight)  
  - Revenue: Ticket price, Ancillary services  
  - Target: Booking status (Completed, Canceled, No-show)  

---

## 🛠️ Tools & Skills Used  
- **Power BI**: Data modeling, star schema, DAX measures, dashboards  
- **SQL**: Data cleaning and preprocessing  
- **Excel**: Exploration and quick validation  

---

## 🏗️ Data Model  
The dataset was modeled into a **star schema** for efficient analysis:  

- **Fact Table**: `fact_bookings` (revenue, cancellations, lead time, booking status)  
- **Dimensions**:  
  - `dim_customer` (ID, demographics)  
  - `dim_date` (booking date, departure date)  
  - `dim_channel` (Web, Mobile, Agent)  
  - `dim_class` (Economy, Business, First)  
  - `dim_destination` (routes, regions)  

*(Insert schema diagram screenshot here)*  

---

## 📈 KPIs & Measures  
Key metrics created in Power BI using DAX:  
- **Total Revenue** = SUM(fact_bookings[Ticket Price])  
- **Total Bookings** = COUNTROWS(fact_bookings)  
- **Avg Lead Time** = AVERAGE(fact_bookings[Lead Time])  
- **Cancellation Rate** = (% of canceled bookings)  
- **Revenue by Class** = Breakdown by Economy, Business, First  
- **Revenue by Channel** = Breakdown by Web, Mobile, Agent  

### Example DAX:  
```DAX
Cancellation Rate = 
DIVIDE(
    CALCULATE(COUNTROWS('fact_bookings'), 'fact_bookings'[BookingStatus] = "Canceled"),
    COUNTROWS('fact_bookings')
)
