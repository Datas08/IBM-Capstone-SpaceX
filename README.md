# IBM-Capstone-SpaceX
 Space X advertises Falcon 9 rocket launches on its website with a cost of 62 million dollars; other providers cost upward of 165 million dollars each, much of the savings is because Space X can reuse the first stage. Therefore if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against space X for a rocket launch.   In this lab, you will create a machine learning pipeline  to predict if the first stage will land given the data from the preceding labs.


![landing_1](https://github.com/Datas08/IBM-Capstone-SpaceX/assets/140479274/1eeb1dc3-2aa5-4020-9de1-2ef610ca7d79)

Several examples of an unsuccessful landing are shown here:

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DS0701EN-SkillsNetwork/api/Images/crash.gif)

Most unsuccessful landings are planed. Space X; performs a controlled landing in the oceans.

---
### Methodology:
### 1. Data Collection (API)
- Requested data from open source SpaceX API(rocket launches)
- Read the reponse with .json() and converted it into a dataframe with .json_normalize() method
- Applied user-defined functions to extrace specific details required from the endpoints (ID's)
- Created a dictionary to store the values with their respective keys
- Converted this dictionary to a pandas dataframe
- Saved the file in CSV format(dataset_part_1)

### 2. Data Wrangling
 - Read the data from the saved file(dataset_part_1.csv)
 - Number of launches on each site
 - Occurence of each orbit(count)
 - Displayed all the landing outcomes with index (enumarate)
 - Created a 'Class' column from a custom function which classifies bad and good outcomes as 0 and 1 respectively.This Class column is our target variable
 - Saved the file in CSV (dataset_part_2)

### 3. Data Exploration with SQL
 - Installed SQLalchemy
 - Created a connection a connection with a sqlite database(my_data.db)
 - Imported csv file and applied .to_sql method to store the data in the database
 - Applied SQL queries with sql magic function (%sql) for data exploration

### 4. EDA
 - Explored data with different charts like scatter plots, catplots between different columns to gain insight about the correlation between them
 - Encoded the categorical columns with .get_dummies() and changed the data type of all columns to be float

### 5. Visualisation with Folium
 - Used the Folium module to create maps and markers to highlight vicinity of sites to the coastal areas

### 6. Interactive Dashboard
- Used plotly to create dyanmic pie chart with dropdown and a scatter plot with slider

### 7. Predictive Analytics
- Created X and y dataframes from exisiting data
- Dropped column FlightNumber (actually I included it initially, however, since it is sequential it lead to overfitting)
- Applied Train-Test-split
- Applied StandardScalar, fit to X_train and pass this scale to X_train and X_test(.transform)
- Cross Validation and Hyperparameter tuning for Logistic Regression, SVM, DecisionTree and KNN
- Confusion matrix, best parameters, best score and test data accuracy for each algorithm
- Identified the best model based on accuracy ,F1 score and best scores
- Deployed the model on streamlit

 ---

 ### Results
 1. Higher payload mass for flight numbers > 50 have high success rate
 2. As the flight number increased, the chances of success increased(i.e the recent flights had a higher chances of successful landing of first stage)
 3. Orbits ES-l1, GEO, HEO, SSO and TLI have highest success rates while SO has the lowest(0%)
 4. Significant correlation between number of flights and landing success in LEO orbit, weak correlation in GTO orbit
 5. With heavy payloads the successful landing or positive landing rate are more for Polar(PO) , LEO and MEO
 6. Success rate since 2013 kept increasing till 2022
 7. All launch sites are in close proximty to coastal areas, equator and highway. Generally there are a distance away from residential zones
 8. All models performed similarly, with Support Vector Machine and Decision tree classifier performing the best
 9. Successfully deployed the app on streamlit

---
This is a guided project provided by IBM and coursera, since I was facing issues with jupyter lite lab (progress was not saving and the format of
downloaded file was not properly displayed, I had to execute the tasks in the localhost jupyter. The tasks and content are provided by IBM skills
network

