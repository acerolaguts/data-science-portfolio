## How much does bed availability affect the quality of service and overall satisfaction with care that nursing home residents in NC receive?

[NC Nursing Home Quality Rating Exploration](https://github.com/user-attachments/files/32446570/DTSC2301.Portfolio.Project.1.ipynb)

[Dataset](https://data.cms.gov/provider-data/dataset/4pq5-n9py#data-table)

For this project, I wanted to explore the bed-to-resident ratio of hospitals and nursing homes and see if and by how much the rating that facility receives is determined by said metric. Intuitively, I would expect a dramatic decrease in rating for facilities that frequently have a shortage of beds, in turn increasing wait times and patient dissatisfaction. However, in my findings, that metric matters very little, and instead the target variables of overall_rating and staffing_rating are impacted much more by how safe the facility is for a resident by inspection, the number of times the facility has been fined, and the average amount of time per day that each resident has dedicated for them by the nursing staff.

Starting with a disclaimer, parts of the code for this project have been AI assisted which I used to fetch records with the CMS API and work out certain pieces of syntax. Along with this disclaimer, I want to acknowledge the limitations of the dataset and potential biases present. This is a dataset containing general provider information about active nursing homes across the country consisting of almost 15,000 records with 99 columns of variables. To make analysis more streamlined and precise, I have limited the dataset to only nursing facilities in North Carolina, reducing the record count from ~15000 to 419. While the analysis of that removed data could lead me in a different direction than what I have found with NC specific facilities, I feel that scope of data would've been much too broad to examine with confidence.

Onto the exploration itself, after fetching the dataset I filtered it to only keep records for North Carolina:

<img width="565" height="205" alt="image" src="https://github.com/user-attachments/assets/79fc4c0c-6f7c-41bb-a91e-ab34cd8c4247" />

I then looked through and kept the main variables that I believe would be useful for my analysis, along with demographic data like city, zip code, and the name of the nursing home:

<img width="1362" height="270" alt="image" src="https://github.com/user-attachments/assets/01abe04f-eb83-4b77-9038-fda378c8d3a1" />

After checking my variables and seeing that all of my numerics were typed as strings, I converted them and made my bed-to-resident ratio by dividing the average number of residents listed by the number of certified beds:

<img width="1138" height="378" alt="image" src="https://github.com/user-attachments/assets/15c6d88c-120e-4dff-bf34-9077a4e3e330" />

I further narrowed my independent variables down after running a correlation test with a few visualizations, determining that other variables present were better suited for the purpose, leaving me with 8 out of the initial 14.

With my finalized dataset, I was able to make a few insightful visualizations:<img width="574" height="438" alt="Nursing Staff Turnover to Overall Rating" src="https://github.com/user-attachments/assets/8e4de42c-8d9b-4a11-b939-d88c6c0932d8" />
<img width="624" height="463" alt="Staff Rating to Staffing hours per resident per day" src="https://github.com/user-attachments/assets/c16564ee-fd5f-4471-8e67-b5ba079212ba" />
<img width="490" height="490" alt="Health Survey Score to Overall Rating" src="https://github.com/user-attachments/assets/6e03a95a-5645-490e-93bd-2f20f07d5673" />

The first shows how nursing staff turnover correlates with the overall rating of the facility. As nursing staff turnover lowers, the rating rasises - suggesting the importance of maintaining a satisfied nursing staff that is eager to hold their position long-term.

The second visualization goes hand in hand with the first, describing another relationship between residents and nursing staff. There is a significant effect on how residents rate the staff based on the amount of hours per day that nursing staff can dedicate to each resident. If I were to speculate, a possible reason behind this is that a nursing staff spread thin over the residents they are responsible for not only leaves the resident dissatisfied because of the perceived lack of care given to them, but also that the strain put on an overburdened nursing staff can reflect poorly in behavior towards residents. This visualization suggests further on the importance of maintaining a satisfied nursing staff, with an emphasis on having an adequate number of nursing staff who are able to dedicate more time in the day toward each resident.

The third visualization shows the relation between the health and safety of the facility and the overall score given to the facility. The weighted health survey scores had the most dramatic impact on overall rating by far, requiring that highly rated facilities have a thorough and dedicated service and nursing staff to minimize the potential harm present towards residents.

To finish off the exploration, I made a linear regression model with the variables I found to be most statistically significant and correlated with the target variable of Overall Rating. Health survey score and nursing staff turnover have already been explained with the visualizations, but I found through exploring the corr values between overall rating and the rest of the independent variables that the number of fines incurred by the facility had a significant relation and determined it would be a useful variable in ethical reputation of a facility when rated by a resident; seeing as the 2 other variables covered other areas of performance in health/safety and nurse-resident relations.

<img width="1210" height="699" alt="image" src="https://github.com/user-attachments/assets/7a3e27f9-51ce-4c83-81be-e47909ef1b5b" />

