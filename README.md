# Airline Customer Booking Analysis Project

## Project Overview

This project analyzes booking behavior from an airline’s customer dataset to uncover key insights into booking completion rates, customer preferences, and flight schedules. The dataset contains 50,000 bookings, of which 7,000 are completed and 43,000 are not, resulting in a 15% booking completion rate. The analysis aims to identify factors that influence booking behavior and provide recommendations to improve the airline's operational efficiency and customer engagement.

## Key Metrics Analyzed

Total Bookings: 50,000
Completed Bookings: 7,000
Non-Completed Bookings: 43,000
Booking Completion Rate: 15%
Average Lead Time: 85 days

## Objective

The objective of this project is to:

Identify key factors influencing booking completion rates.
Provide actionable insights to optimize operations.
Recommend strategies to improve customer engagement and increase completed bookings.

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

Created custom measures in Power BI for:

Total Bookings
Completed Bookings
Booking Completion Rate
Service Preference Impact (baggage, seat, meals).

### Visualization: 

Built interactive Power BI dashboards showing key insights and recommendations.

## Key Insights

Lead Time: Bookings made within 1 week of the flight have a completion rate of 17%, indicating a focus on last-minute marketing could capture more bookings.

Length of Stay: Longer stays (more than 1 year) have a 26% completion rate, suggesting extended stay promotions could increase bookings.

Sales Channel: Internet bookings dominate at 91.86%, while Mobile has only 8.14% of completed bookings, highlighting an opportunity to improve the mobile experience.

Flight Time: Morning flights (6:00 AM to 11:59 AM) have the highest booking volume, while evening flights have the lowest completion rate, showing potential for capacity adjustments and evening discounts.

Service Choices: Customers who select all three services (extra luggage, seat, meals) have a 19% completion rate, compared to 11% for those who select none, suggesting that bundled service packages can improve commitment.

## Recommendations

Target Last-Minute Bookers: Run last-minute booking campaigns for customers booking flights within 1 week.

Optimize Mobile Experience: Improve the mobile app or website to increase mobile bookings.

Incentivize Service Add-ons: Promote bundled services (extra luggage, preferred seat, in-flight meals) to increase booking completion.

Optimize Flight Schedules: Offer discounts for evening and late-night flights to increase demand.

## Technologies Used

Power BI: For data analysis and visualization.
DAX: For custom calculations and metrics in Power BI.

## Project Files

Airline_Customer_Booking_Analysis.pbix: The Power BI dashboard file containing all analysis and visualizations.
Dataset.csv: The raw dataset (replace this with actual filename if shared).
README.md: This README file.

## Conclusion

By focusing on key areas such as lead time, customer preferences, and flight time, this analysis provides actionable insights that can help airlines optimize their operations and improve booking completion rates. The recommendations offered will help the airline increase customer engagement and overall profitability.
