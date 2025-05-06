# OLA-Case-Study   Link : https://drive.google.com/file/d/1AF9josCwzk6P174Ucu4FaNHg1lhu2R3C/view?usp=drive_link

This project is a comprehensive case study focused on analyzing ride-booking data for OLA Cabs Bengaluru. It simulates a real-world dataset and solves business problems using SQL for querying and Power BI for visualization.

📌 Problem Statements
The key business questions addressed in this project include:

SQL-Based Analysis:
1. Retrieve all successful bookings.

2. Analyze average ride distance by vehicle type.

3. Count cancelled rides by customers and categorize reasons.

4. Identify top 5 customers by ride count.

5. Evaluate driver cancellations due to specific issues.

6. Analyze driver ratings, especially for premium vehicles.

7. Explore payment method preferences (e.g., UPI).

8. Examine average customer ratings by vehicle type.

9. Calculate revenue from successful bookings.

10. Identify incomplete rides and their reasons.

Power BI Dashboards:
1. Visualize ride volume trends over time.

2. Breakdown booking statuses.

3. Rank top vehicle types by total ride distance.

4. Compare average customer ratings across vehicle types.

5. Analyze reasons for cancellations by both customers and drivers.

6. Revenue breakdown by payment methods.

7. Top 5 high-value customers.

8. Daily ride distance distribution.

9. Driver rating distribution.

10. Comparison of customer vs. driver ratings.


SQL Questions & Answers

#1. Retrieve all successful bookings:
Create View Successful_Bookings As
SELECT * FROM bookings
WHERE Booking_Status = 'Success';

#2. Find the average ride distance for each vehicle type:
Create View ride_distance_for_each_vehicle As
SELECT Vehicle_Type, AVG(Ride_Distance)
as avg_distance FROM bookings
GROUP BY Vehicle_Type

#3. Get the total number of cancelled rides by customers:
Create View cancelled_rides_by_customers As
SELECT COUNT(*) FROM bookings
WHERE Booking_Status = 'cancelled by Customer';

#4. List the top 5 customers who booked the highest number of rides:
Create View Top_5_Customers As
SELECT Customer_ID, COUNT(Booking_ID) as total_rides
FROM bookings
GROUP BY Customer_ID
ORDER BY total_rides DESC LIMIT 5;

#5. Get the number of rides cancelled by drivers due to personal and car-related issues:
Create View Rides_cancelled_by_Drivers_P_C_Issues As
SELECT COUNT(*) FROM bookings
WHERE cancelled_Rides_by_Driver = 'Personal & Car related issue';

#6. Find the maximum and minimum driver ratings for Prime Sedan bookings:
Create View Max_Min_Driver_Rating As
SELECT MAX(Driver_Ratings) as max_rating,
MIN(Driver_Ratings) as min_rating
FROM bookings WHERE Vehicle_Type = 'Prime Sedan';

#7. Retrieve all rides where payment was made using UPI:
Create View UPI_Payment As
SELECT * FROM bookings
WHERE Payment_Method = 'UPI';

#8. Find the average customer rating per vehicle type:
Create View AVG_Cust_Rating As
SELECT Vehicle_Type, AVG(Customer_Rating) as avg_customer_rating
FROM bookings
GROUP BY Vehicle_Type;

#9. Calculate the total booking value of rides completed successfully:
Create View total_successful_ride_value As
SELECT SUM(Booking_Value) as total_successful_ride_value
FROM bookings
WHERE Booking_Status = 'Success';

#10. List all incomplete rides along with the reason:
Create View Incomplete_Rides_Reason As
SELECT Booking_ID, Incomplete_Rides_Reason
FROM bookings
WHERE Incomplete_Rides = 'Yes';



