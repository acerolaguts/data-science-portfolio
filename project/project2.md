## Does the Amount of Electric Vehicles in a Washington State County Increase with Median Income?

For this project I found a dataset that caught my interest containing the electric vehicle (EV) records of Washington State. The dataset contains the VIN, make, model, electric vehicle type, clean alternative fuel vehicle (CAFV) eligibility, electric range, legislative district, DOL vehicle ID, vehicle location as a point object, electric utility, and the 2020 GEOID of each vehicle on record with about 300,000 records in total. I was interested in 2 questions stemming from this dataset: 1, "is there a positive financial correlation for Washington State counties that have more EVs?" and 2, "Is there a difference in the type of EVs that populate counties in the higher and lower count range?" To answer those questions I am focusing on the total count of EVs per county, electric range, and a median income per county that I read in from a separate census dataset.

Disclaimer: AI was used in streamlining syntax for a portion of the functions, with a comment in each cell of the notebook where it was used.

After reading in both datasets using pandas read_csv function, I subset the EV dataset to contain only records for Washington State, and created a value counts variable for both total records per county and only the records where the vehicle is CAFV Eligible, meaning a purely electric viable vehicle, and added both of them to a county only dataset with the assistance of AI.

<img width="843" height="870" alt="image" src="https://github.com/user-attachments/assets/7cbbfabc-09a0-49b7-b49d-90f4ccb45adf" />

I was then left with a subset of 39 records at the county level, with value counts for both total EV per county and CAFV Eligible EV per county, to which I then merged the median income dataset into for the purpose of creating a linear regression model, as well as a density heat map of the state of Washington for both EV count and income. 

<img width="762" height="867" alt="image" src="https://github.com/user-attachments/assets/99397adc-dd7b-4d57-92de-1e3a01cd1ddb" />

I only kept 2020 median income values to keep it consistent with the EV dataset, which I am assuming was updated in 2020 from the 2020 GEOID variable. I also ran a correlation test on these variables to answer another one of my questions of if there was a notable difference in the type of electric vehicle found in different counties; e.g. if pure electric vehicles were found more in high population counties with presumably better EV infrastructure vs hybrids that might be found more primarily in middling or lower-end counties with lesser infrastructure and lower incomes. However, this train of thought was proven wrong, as the values for pure vs total EVs were almost completely proportional, with the caveat that many of the EVs are marked as unknown due to a not-at-the-time researched battery, such as those in the Tesla model 3 for example.

<img width="718" height="259" alt="image" src="https://github.com/user-attachments/assets/54dbd835-e837-4144-a578-6ea0323e78fb" />

'2020' is the 2020 median income variable

After, I made an average electric range for vehicles found in each county for use in the linear regression model.

<img width="936" height="871" alt="image" src="https://github.com/user-attachments/assets/6f4f4afc-a296-4073-a9f5-f78a251bbcf5" />
<img width="1012" height="673" alt="image" src="https://github.com/user-attachments/assets/f93fa76d-6e33-4bcb-96f5-12e44d0dc2dd" />

While the average electric range fails the p-value test, being statistically insignificant, income is seen to be very significant to the amount of EVs per county. Both R^2 and Adj. R^2 are around .45 - .49, explaining a good amount of the variance within EV count using those 2 predictor variables.

Also visualized is the density heat maps I made of Washington State for both EV counts and median incomes:
<img width="623" height="407" alt="Washington_EV_Map" src="https://github.com/user-attachments/assets/28f78a9d-15d1-434a-8b4c-b2126a2ff0ae" />
<img width="625" height="407" alt="Washington_Median_Income_Map" src="https://github.com/user-attachments/assets/27abaece-c710-4c24-ac94-acb9c65e4a9f" />

In conclusion, by modeling the variables it can be suggested that there is a statistically significant positive relationship between the amount of EVs in a county and the median income of the county, and that there is not a discernible difference in the proportion of CAFV vs non-CAFV vehicles in different counties depending on median income or location, answering both of my original RQs.
