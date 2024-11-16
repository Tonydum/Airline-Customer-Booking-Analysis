# Airline Customer Booking Analysis Project

# Table of Contents

- [Project Overview](#Project Overview)

## Project Overview

This project analyzes booking behavior from an airline’s customer dataset to uncover key insights into booking completion rates, customer preferences, and flight schedules. The dataset contains 50,000 bookings, of which 7,000 are completed and 43,000 are not, resulting in a 15% booking completion rate. The analysis aims to identify factors that influence booking behavior and provide recommendations to improve the airline's operational efficiency and customer engagement.

## Objective

The objective of this project is to:

- Identify key factors influencing booking completion, including the impact of sales channels, customer preferences (e.g., baggage, meals), and booking lead times.
- Analyze whether customers who book earlier are more likely to complete their bookings.
- Provide insights into customer preferences that drive booking completions, such as extra baggage, preferred seats, and meal choices.
- Evaluate the effect of the sales channel (Internet vs. Agent) on booking completion rates and add-on service purchases.
- Determine if specific flight times, routes, or destinations are associated with incomplete bookings.
- Understand how the length of stay or trip type (RoundTrip vs. One-Way) impacts booking completion rates.

## Key Metrics Analyzed

1. Booking Completion Rate

- Percentage of bookings completed vs. abandoned, based on customer actions throughout the booking process.

2. Booking Lead Time

- Number of days between booking initiation and flight departure, and its impact on booking completion.

3. Customer Preferences

- Correlation between preferences (extra baggage, preferred seat, in-flight meals) and the likelihood of completing a booking.

4. Sales Channel Comparison

- Comparison of booking completion rates between customers using different sales channels (Internet vs. other channels such as agents).

5. Booking Time and Route Impact

- Identification of peak booking times (e.g., weekends, mornings, evenings) and routes or destinations with high rates of incomplete bookings.

## Technologies Used

Power BI: For data analysis and visualization.

DAX: For custom calculations and metrics in Power BI.

## Dataset

The dataset used in this analysis contains the following key columns:

booking_complete: Whether the booking was completed or not.

purchase_lead: The number of days between the booking and the flight.

sales_channel: Whether the booking was made via Internet or Mobile.

wants_extra_baggage, wants_preferred_seat, wants_in_flight_meals: Customer preferences for extra services.

flight_hour: The time of day the flight is scheduled.

length_of_stay: The duration of the trip.

## Analysis Process

Data Cleaning: Removed duplicates and handled missing data.

### Data Transformation:

Categorized flight hours into segments (Late Night, Morning, Afternoon, Evening).
Segmented lead times into buckets (1 week, 1 month, 3 months, etc.).
Categorized length of stay (short, medium, long stays).

### DAX Calculations: 

Created custom measures & calculated columns in Power BI for:

```dax
Total Booking = COUNTROWS(customer_booking)
```
```dax
Completed Booking = CALCULATE([Total Booking], customer_booking[booking_complete] = 1)
```
```dax
Booking Completion Rate = customer_booking[Completed Booking] / customer_booking[Total Booking]
```
```dax
Average Lead Time = 
VAR averagetime = AVERAGE(customer_booking[purchase_lead])
RETURN CONCATENATE(ROUND(averagetime, 0), " days")
```
```dax
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
```dax
flight_time_category = 
SWITCH(
    TRUE(),
    customer_booking[flight_hour] >= 0 && customer_booking[flight_hour] < 6, "Late Night",
    customer_booking[flight_hour] >= 6 && customer_booking[flight_hour] < 12, "Morning",
    customer_booking[flight_hour] >= 12 && customer_booking[flight_hour] < 18, "Afternoon",
    customer_booking[flight_hour] >= 18 && customer_booking[flight_hour] <= 23, "Evening",
    "Undefined"
)
```
### Visualization: 

Built interactive Power BI dashboards showing key insights and recommendations.

## Key Insights

![image](https://github.com/user-attachments/assets/bb839980-4b58-4139-a1e9-182bab92120a)

Bookings made within 1 week of the flight have the highest completion rate of 17%, suggesting that focusing on last-minute marketing campaigns could help capture more high-conversion bookings.

![image](https://github.com/user-attachments/assets/94684491-6649-4ce4-ab6d-ad24c20de009)

Longer stays (more than 1 year) show a 26% completion rate, while shorter stays (1 week or less) maintain a solid 19%, indicating that promoting extended stay packages and short-trip deals could effectively boost both segments.

![image](https://github.com/user-attachments/assets/0707ec22-103e-4917-8d16-9675fc492135)

Morning flights (6:00 AM to 11:59 AM) see the highest booking volume, while evening flights struggle with low completion rates, indicating an opportunity to increase morning flight capacity while offering discounts for evening flights to improve overall booking performance.

![image](https://github.com/user-attachments/assets/e218a035-0d1d-42fb-a1be-8776c1d3cd67)

Customers who select all three services (extra luggage, seat, meals) have the highest completion rate at 19%, compared to 11% for those who select none, suggesting that offering bundled service packages could encourage higher commitment and booking completions.

### Dashboard

![image](https://github.com/user-attachments/assets/cf79c9d8-62f1-447e-8006-aa2f72c1bb53)

## Recommendations

Target Last-Minute Bookers: Run last-minute booking campaigns for customers booking flights within 1 week.

Optimize Mobile Experience: Improve the mobile app or website to increase mobile bookings.

Incentivize Service Add-ons: Promote bundled services (extra luggage, preferred seat, in-flight meals) to increase booking completion.

Optimize Flight Schedules: Offer discounts for evening and late-night flights to increase demand.
