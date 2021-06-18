# Seattle AirBNB Insights

## Libraries Used

* Python version: 3.8.5
* pandas
* matplotlib
* sklearn
* collections

## Motivation of the Project

AirBNB created a new business case. Renting out private space to travelers and people looking for short- and medium-term stays. As it is booked only via their online presence, a lot of its data is publicly available. Here, I look into the Seattle AirBNB data, mostly for the year 2016. I explore the data and try to answer several questions:

* What is the average price per month and availability per month? (Year 2016)
* What are the biggest factors driving the price? (ex amenities)
* What amenities drive the review score? What should be available, what can easily be added to provide value?

## Files in the Repository

* Project_Blog_Post_Seattle_Airbnb.ipynb: project jupyter notebook
* Pictures (self-explaining by title)
    * availability_of_listings_per_month_in_2016.png
    * average_price_o_available_listings_per_month_in_2016.png
    * importance_of_amenities_in_relation_to_review_score_rating.png
    * importance_of_features_in_relation_to_price.png
* folder data:
    * calendar.csv - including full descriptions and average review score
    * listings.csv - including listing id and the price and availability for that day
    * neighourhoods.csv - maps neighourhoods to neighbourhood groups
    * reviews.csv - including unique id for each reviewer and detailed comments

## Summary of the Results

The Seattle AirBNB data for 2016 shows that it is most expensive to get an AirBNB in July (\$155). This is not surprising. The demand during the summer (good weather conditions, holiday season) should be higher than during the rest of the year. Prices are quite low at the beginning of the year (around \$120) and in November (around \$135). There is a little increase again in December (probably due to the Christmas time and increased travel activities again).

The earliest date of the dataset was January 4, 2016. The provided data was gathered around this date or just before this date. This has to be taken into account when interpreting the results. This has implications especially for the results of the Availability of the Listing per Month. It is at its lowest in January at around 55%. This is understandable because all visitors who book on short notice cause a higher occupancy compared to the same listings on year out, for example. The local peak in March, around 71%, suggests that the effect of those short-term bookings is not that prevalent yet. As with the price, availability in July is quite low at around 62%. This is also understandable since the visitors want to lock in the place for the stay well in advance during high season.

The second question is about the impact of features on the price. After deleting redundant columns (i.e. features) and information that I considered irrelevant, I am down to 43 features that will be examined.

I used the Random Forest Regressor for this task. The model shows an R-squared of 0.914 for the Train data. This is a great result and the model fits the real data quite well. Unfortunately, the R-squared figure for the Test data is not as high with 0.676. It can be concluded that the model does not generalize too well. But the Test R-squared is still reasonably high and the model still does a good job in explaining the importance of the features on the price.

When looking into the feature importance, you that one feature is by far the most important one: the number of bedrooms (37.1%). This is followed by the number of reviews (9.7%), the number of bathrooms (9.3%), and the number of people it accommodates (7,7%). There is certainly a correlation between number of bedrooms, bathrooms, and accommodates. Number of reviews certainly shows that the pricey listings get booked more often and/or as they are well in demand the price might be adjusted accordingly. What you can also see, even though the impact is not really significant (3.1% and less), that the neighbourhoods have also an impact on the price. Downtown, for example, has the highest impact of all the neighbourhoods. The reason could be that it can be considered the city center which offers short distances to many Seattle sights.

The third and last question deals with the amenities and the review scores rating. I try to find out if there are certain amenities that have an impact on the review and that can easily be added to provide value if missing so far (e.g. a first aid kit can certainly provided easily whereas it would be much more difficult if not impossible to add an indoor fireplace in a regular apartment).

The Random Forest Regressor is also used here. The R-squared value of 0.758 based on the Trained data looks promising, but after checking the trained model against the Test data it shows that it does not generalize very well and fits the data really poorly. The R-squared value for Test data is -0.232. The results should probably be dismissed. Perhaps using a different algorithm might lead to better and more significant results.

Nevertheless, when looking into the feature importance, you can possibly still draw a few conclusions (even though you should treat them with some suspicion). Over all, there is not a feature as dominating as the number of bedrooms of question two. The most important feature is Family/Kid Friendly (5.6%), followed by Cable TV (5.0%) and TV (4.8%).

When looking at features with 3% and more, the following might be able to provide value and should be added to the listing if possible: TV, Cable TV, Essentials, Fire Extinguisher, Internet, First Aid Kid, Carbon Monoxide Detector, and Shampoo.

The following features might not as easily be added or not all (all above 3%): Family/Kid Friendly, Free Parking on Premises, Elevator in Building, Indoor Fireplace, Buzzer/Wireless Intercom, and Gym. Here, you should just focus on the ones stated above and try to add those to provide value and that potentially increase your review score instead of adding this Indoor Fireplace for example.

## Acknowledgement

The dataset used is part of AirBNB Inside.
