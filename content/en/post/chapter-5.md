---
date: 2022-03-20T10:58:08-04:00
description: "In this project we were estimating the potential performance of the hotel when applying price optimization, differentiation, and protection levels for the bookings. The project contains a lot of dynamic programming ad probabilistic demand modelling."
featured_image: "/images//kapriz.png"
title: "Applying revenue management methods to the resort hotel Kapriz Issyk Kul" 
---
The [Github Repo](https://github.com/sinkov/Dynamic_programming_revenue) contains presentation, raw historical data  Python code with demand modelling and R code with all the tools. 

**Business context**

Kapriz resort is the leading summer recreation centre in Central Asia, located in the heart of Kyrgyzstan
on the coast of Issyk Kul Lake. It has been hosting guests for over ten years, impressing tourists from
Asia, Europe, the United States, Russia, the Middle East and other places. The unique sand beach, pier,
suitable for parking large boats, amazing green territory, and beautiful infrastructure are its competitive
advantages.

Target guests are:

● Families looking for a peaceful place to rest with their children.

● Professional athletes (the resort is located at 1600 m altitude, making it unique for endurance training).
This category typically arrives during the off-season – September to November and March to June.
Kapriz hosted the Asian Triathlon Cup in September 2021.
● Travellers from all over the world exploring Kyrgyzstan and deciding to spend a few days in Issyk-Kul.

● People from Kyrgyzstan and Kazahstan, trying to escape cities heat and enjoy Issyk Kul’s fresh air.

This segment typically visits a resort for the weekend because it is easily accessible by car.


The total number of rooms is 117, which are distributed in the following way:
● The main building: 67 rooms (standard - 2 person and suits - 4 people)

● Gallery buildings: 11 apartments for 4 people each

● Cottages: 34 for 6 people, 1 for 8 people and 4 for 10 people each.


However, the management faces some difficult challenges that it has been attempting to overcome since
its founding in 2009. First, there's strong seasonality and unpredictability of the weather. On sunny days in
July and August, the hotel is usually full, partially occupied in June and September, and mostly empty the
rest of the year (Figure 1), resulting in a 40% average annual occupancy rate. Prior to the pandemic,
tariffs were fixed and divided into five categories (Table 1), depending on the year period. Management
concentrated its efforts on athletes, giving up the idea of experimenting with other ways to attract tourists
during the relatively cold months.
In order to boost post-covid life of the resort, the board of directors hired the hospitality consultancy firm
JMEG Consulting to assist in the implementation of dynamic pricing instruments, moving from selling
services via telephone to online booking via the website (the resort relied solely on offline bookings). The
expectation of the new pricing strategy is the following: to gain extra profits during extremely busy summer
days (occupancy rate > 80%) and significantly increase average/low-season revenue by offering flexible
pricing based on current occupancy.


**Considerations of different models**

**1. Protection level implementation**
One of the methodologies that JMEG developed was a prototype model allowing to set protection levels
for each price level. The model took into account a typical week in July for twin room bookings and was
based on _5 price levels_ provided by the revenue manager of the resort. The total number of rooms that
can be allocated per week was _350 (50 rooms * 7 days)_ , and the algorithm determined the optimal number
of rooms to protect for each price level. After performing a booking simulation, it was discovered that the
heuristic approach's optimal revenue was very similar to the one obtained with protection levels ($
vs.$44518). We recommended the hotel to revise the price list and run the procedure once again to see if
the revenue increased.
**2. Price Differentiation Model**
The hotel can use different channels in order to reach different types of customers. It can do so based on
people’s location in order to distinguish local guests from abroad ones. The hotel can distribute the leaflets
that give lower prices for the rooms. It can be distributed through local supermarkets, local restaurants or
universities. For other people the original price can be increased by 20%.

In order to calculate new revenue, we estimated the demand first. We used real revenue, real prices and
real revenue distribution among the months.

The steps were the following:
1) From Figure 1 we manually estimated the percentage of revenue per period in Table 1.
2) We distributed the total revenue between two room categories: Hotel residences (first 5) and
Cottages (last 4) according to Figure 1.
3) We calculated maximum possible revenue for both categories.
4) We estimated the occupancy via dividing real revenue by maximal possible revenue.
5) Based on the occupancy we derived the demand for each period and each room type.
6) For this model we used 𝑅𝑒𝑣𝑒𝑛𝑢𝑒 = 𝐷𝑒𝑚𝑎𝑛𝑑⋅𝑃𝑟𝑖𝑐𝑒 and 𝐷𝑒𝑚𝑎𝑛𝑑 = 𝑎 − 𝑏⋅𝑃𝑟𝑖𝑐𝑒 (where ‘a’ and
‘b’ are non-negative numbers). We set ‘ _a_ ’ as a room capability multiplied by a coefficient that
represented the period popularity (its higher for summer periods and lower for winter) and derived
‘ _b_ ’.
7) Now we set two prices: one was 20% upper of the original price and another with a 10% discount.
8) In order to be closer to the real world we set a cannibalization level of 25% (those who were willing
to pay a higher price, but they paid a discounted price).
9) We calculated demand for a higher price, discounting it on cannibalization level.
10) We calculated the desired demand for discounted price, subtract those who were willing to buy
with higher price (except cannibalizationated customers).
11) Finally, we calculated the new revenue.
**The new revenue was higher than the original one by 23% from $1,989,925 to $2,451,856.**

**Data Simulation (WTP)**
To use the following two revenue pricing methods (sections 3 and 4) and optimise the company’s revenue,
we simulated the WTP for a number of customers. Because the hotel operated the whole year and has
117 rooms of 9 types, WTP for 150 clients for each day of the year and for each different room type was
simulated.

The size of the simulated data was 1350x367.


To simulate data points that represented the reality as closely as possible, we used the given prices in
table 1 as mean and simulated normally distributed WTP data. Because the demand for weekends was
higher compared to weekdays, we increased the means for the weekends and decreased the ones during
the weekday.

**3. Network Revenue Management using linear Programming**
Here we tried 2 different price points for each type of room per day and optimally allocated the room
based on the demand of these points. The prices chosen were the actual prices along with the same
prices but adding $5. Then we calculated the demand for each day per room type for all the clients by
following the next steps:
1. We used the simulated WTP for all the clients in each room type.
2. We found the surplus of each customer for each type of room for every single day by
subtracting the price from the WTP.
3. We assumed that each client would choose the room that would maximise his/her surplus
each day.
4. We summarised the total demand for each room type per day.

After that, we formulated the arguments of our optimization function. The objective function coefficients
were the two different price points for 9 types of rooms. We set the constraints for the number of rooms
that we allocated based on their total capacity and the demand for each room. 

Lastly, we ran the linear programming function for each day, by using the corresponding demands and we
found the best allocation of resources of the hotel per day, along with corresponding revenue for the day.
This revenue, along with the one created by the fixed price was saved in a matrix to find the total revenue
of the Year.

By using two prices instead of one for each room type and optimally allocating the rooms, the hotel
improved its revenue up to 18% annually. This was a small yet powerful modification that the hotel can
apply without implementing new complex procedures and can significantly improve its revenues.

**4. Price optimization methods**
We used the simulated WTP data mentioned in the previous section in this part, and we focus on
adjusting the weekly optimal price and boosting weekly revenue.
At first, MultiNomial Logit (MNL) model for a single price during a week was applied. After discovering the
model, we found out the majority booking was during Friday to Sunday, and to overcome this issue, we
introduced another price optimization method. See figure below.

We defined a function _OptimalPriceForAWeek_ with room type and week number as input, and the output
was the optimal weekday price and weekend price based on the given room type and week, and the
optimal revenue of this week. For example, we input room type 2 and week 30 (a week in July), as we
knew the occupancy rate in summer was very high, so we had potential to charge higher prices which
would increase revenue. The result of the function gave us 125 for weekday price and 138 for weekend
(compared to the fixed price in the table, which was single price 125), and optimal revenue was 20,966,
which was roughly 15% increased.
The function was designed to present clearer results (weekly revenue instead of yearly) for the manager
since weekly revenue was more preferably convincing.


**5. Testing the dynamic pricing idea suggested by Kapriz management**
‘Dynamic_tariffs.csv’ contains the fares suggested by the revenue manager of Kapriz. ‘Histdata.csv’
contains historical data for summer 2019. The management wanted to introduce the dynamic pricing
model based on occupancy rate of the hotel for each season and wanted to challenge their intuition by
simulating bookings and comparing revenues obtained by fixed and dynamic pricing strategies. Since we
did not have access to granular booking data, JMEG developed a framework to simulate it for 91 days.
The Python notebook ‘Fixed_vs_dynamic.ipynb’ contains all required functions and comments for the
management:
● get_probability_of_day: gets probability of the booking starting at particular day, based on historical
data
● get_random_day_and_length: obtains day of start of the booking and length of the booking (nights,
estimated by Gamma distribution)
● get_random_category: returns category number (1-twin, 2-suit, 3-villa etc)
● get_availiable_rooms: initialises 91 (nights) by 9 (categories) matrix with given availability
● check_availability: checks if requested dates are available or not
● get_price_for_request_and_confirm_booking/fixed_price: functions, that incorporate previous
results (day, length, category, availability), calculate prices based on either fixed or dynamic
settings and confirm booking by updating the availability
● get_occupancy: calculates resulting occupancy for each day
Results of the simulation tell us that suggested pricing differentiation is not leveraging the resort’s revenue
($1,070,685 vs $1,064,470). The differentiation principle should be reviewed.

**Conclusion**
The results of different models:
{{< figure src="/images/conc.png" >}}


**Overbooking**
Allowing overbookings is one of possible ways to increase revenue. Booking cancellations are a problem
that Kapriz has addressed by implementing non-cancellation tariffs with a 15% discount. It helps to protect
against large cancellations, but it is still impossible to fully establish a no-cancellation policy. However, we
will not recommend that the resort allow overbooking because there are no hotels in the region where
guests can swap to acquire similar services and avoid a bad experience with Kapriz.



