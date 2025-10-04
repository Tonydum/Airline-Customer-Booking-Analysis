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

https://app.powerbi.com/view?r=eyJrIjoiMWFjMGRlZDYtMjUxZi00M2FhLTg3MTctY2MxNTk5ZjRkYjUwIiwidCI6IjcxZmIyM2QxLWU1NzAtNGJiOS1iYTQzLWI0ZTllYmI4NDhlZiJ9

## 📌 Project Overview  
This project analyzes airline booking data to identify customer booking behavior, revenue trends, and areas for operational improvement. 
The dashboard helps airline managers understand how customers book flights (timing, channel, class), and where revenue is gained or lost.  

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
- **Power BI**: DAX measures, dashboards 
- **Excel**: Exploration and quick validation  

---

## 🏗️ Data Model

The dataset was provided as a flat file. To enable better analysis in Power BI, the data was cleaned and reshaped in Power Query.

Created calculated columns and lookup tables for Booking Class, Channel, Destination, and Dates.

This allowed the data to be treated like a fact table with supporting dimensions, making it easier to build measures and visuals.

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
Completed Booking = CALCULATE([Total Booking], customer_booking[booking_complete] = 1)

Booking Completion Rate = DIVIDE(customer_booking[Completed Booking], customer_booking[Total Booking])

Cancellation Rate = 
DIVIDE(
    CALCULATE(COUNTROWS('fact_bookings'), 'fact_bookings'[BookingStatus] = "Canceled"),
    COUNTROWS('fact_bookings')
)

Average Flight Duration = 
VAR averageflightduration = AVERAGE(customer_booking[flight_duration])
RETURN CONCATENATE(ROUND(averageflightduration, 0), " hours")

Average Lead Time = 
VAR averagetime = AVERAGE(customer_booking[purchase_lead])
RETURN CONCATENATE(ROUND(averagetime, 0), " days")

flight_time_category = 
SWITCH(
    TRUE(),
    customer_booking[flight_hour] >= 0 && customer_booking[flight_hour] < 6, "Late Night",
    customer_booking[flight_hour] >= 6 && customer_booking[flight_hour] < 12, "Morning",
    customer_booking[flight_hour] >= 12 && customer_booking[flight_hour] < 18, "Afternoon",
    customer_booking[flight_hour] >= 18 && customer_booking[flight_hour] <= 23, "Evening",
    "Undefined"
)

purchase_lead_time_category = 
SWITCH(
    TRUE(),
    customer_booking[purchase_lead] <= 7, "1 week or less",
    customer_booking[purchase_lead] > 7 && customer_booking[purchase_lead] <= 30, "1 week to 1 month",
    customer_booking[purchase_lead] > 30 && customer_booking[purchase_lead] <= 90, "1 month to 3 months",
    customer_booking[purchase_lead] > 90 && customer_booking[purchase_lead] <= 180, "3 months to 6 months",
    customer_booking[purchase_lead] > 180 && customer_booking[purchase_lead] <= 365, "6 months to 1 year",
    customer_booking[purchase_lead] > 365, "More than 1 year"
)
```

## 📊 Dashboard Highlights & Insights

1. Bookings by Lead Time


Insight: Most bookings made within 1 week of a flight have a high completion rate. This shows an opportunity to run last-minute promotions to capture more short-notice travelers.

![image](https://github.com/user-attachments/assets/bb839980-4b58-4139-a1e9-182bab92120a)


2. Trip Duration Impact


Insight: Customers booking long stays (over 1 year) are highly committed (26% completion), while short stays (under 1 week) also perform well at 19%. Airlines can promote both extended packages and short-trip deals to capture these segments.

![image](https://github.com/user-attachments/assets/94684491-6649-4ce4-ab6d-ad24c20de009)


3. Booking Time of Day


Insight: Morning flights see the most bookings and completions, while evening flights have low completion rates. Airlines could add capacity in the morning and use discounts or bundles to fill evening flights.

![image](https://github.com/user-attachments/assets/0707ec22-103e-4917-8d16-9675fc492135)


4. Service Add-ons


Insight: Customers who buy all add-ons (extra luggage, seat, meals) complete bookings more often (19%) compared to those with no add-ons (11%). Bundling services encourages higher booking commitment.

![image](https://github.com/user-attachments/assets/e218a035-0d1d-42fb-a1be-8776c1d3cd67)

![image](https://github.com/user-attachments/assets/cf79c9d8-62f1-447e-8006-aa2f72c1bb53)



## 💡 Business Impact

Revealed high cancellation risk for last-minute bookings, giving insight into revenue leakage.

Showed that business class drives disproportionate revenue, important for pricing and loyalty strategies.

Identified mobile bookings as a fast-growing channel, guiding digital investment priorities.

Highlighted key routes and destinations that drive most revenue.

## 📝 Recommendations

Introduce flexible cancellation policies or fees for last-minute bookings to reduce no-show losses.

Invest in mobile booking platform improvements to capture growth in mobile users.

Create targeted loyalty perks for business class passengers, since they drive revenue.

Focus marketing on top-performing routes, while exploring strategies to boost underperforming destinations.

## 🚀 How to Use

Clone or download the repository.

Open Airline-Booking-Analysis.pbix in Power BI Desktop.

All necessary data (CSV) is included - no external connections needed.

## 📌 Next Steps

Build predictive model for cancellation risk.

Incorporate seasonality trends (peak/off-peak booking behaviors).

Add customer segmentation (frequent flyers vs. one-time travelers).


