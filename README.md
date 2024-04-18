
# Customer Risk Analysis

This dashboard helps the he Retention Manager from the PhoneNow telecom with the insights about customer retention.

# Customer Risk Analysis-Dashboard

### Dashboard Link :https://app.powerbi.com/view?r=eyJrIjoiM2MzY2MwYmYtYWVjMy00ZGE3LWFkYjktMDEwMWJlZDYzNzc4IiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9

## Problem Statement

Create a dashboard to reflect customer demographics, insights and Customers who is at risk to prevent losing of customers

### Tools Used - Power BI

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4: The data was good enough to start calculations
- Step 5: Created a new measure table to store all measures inside this table for clarity.
- Step 6: Measures to calculate Churn, Gender, Dependents, Partner, Senior citizens & their Churn percentages.
            
            Churn = CALCULATE(COUNT('01 Churn-Dataset'[Churn]),'01 Churn-Dataset'[Churn]="Yes")
            Churn % = DIVIDE([Churn],[Total Customers])

            Depandents % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[Dependents]="Yes"),[Total Customers])
            Churn Depandents % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[Dependents]="Yes",'01 Churn-Dataset'[Churn]="Yes"),CALCULATE([Total Customers],'01 Churn-Dataset'[Dependents]="Yes"))

            Male = CALCULATE([Total Customers],'01 Churn-Dataset'[gender]="Male")
            Female = CALCULATE([Total Customers],'01 Churn-Dataset'[gender]="female")
            Churn Male = CALCULATE([Total Customers],'01 Churn-Dataset'[gender]="Male",'01 Churn-Dataset'[Churn]="Yes")
            Churn Female = CALCULATE([Total Customers],'01 Churn-Dataset'[gender]="female",'01 Churn-Dataset'[Churn]="Yes")

            Partner = CALCULATE([Total Customers],'01 Churn-Dataset'[Partner]="Yes")
            Partner % = DIVIDE([Partner],[Total Customers])
            Churn Partner = CALCULATE([Total Customers],'01 Churn-Dataset'[Partner]="Yes",'01 Churn-Dataset'[Churn]="Yes")
            Churn Partner % = DIVIDE([Churn Partner],[Partner])

            Senior Citizen = CALCULATE([Total Customers],'01 Churn-Dataset'[SeniorCitizen]="Yes")
            Senior Citizen % = DIVIDE([Senior Citizen],[Total Customers])
            Churn Senior Citizen = CALCULATE([Total Customers],'01 Churn-Dataset'[SeniorCitizen]="Yes",'01 Churn-Dataset'[Churn]="Yes")
            Churn Senior Citizen % = DIVIDE([Churn Senior Citizen],[Senior Citizen])

- Step 7: Measures to calculate the Services and Churn percentage.
            
            Device Protection % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[DeviceProtection]="Yes"),[Total Customers])
            Device Protection Churn % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[DeviceProtection]="Yes",'01 Churn-Dataset'[Churn]="Yes"),CALCULATE([Total Customers],'01 Churn-Dataset'[DeviceProtection]="Yes"))

            Internet Service % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[InternetService]<>"No"),[Total Customers])
            Internet Service Churn % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[InternetService]<>"No",'01 Churn-Dataset'[Churn]="Yes"),CALCULATE([Total Customers],'01 Churn-Dataset'[InternetService]<>"No"))

            Phone Service % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[PhoneService]="Yes"),[Total Customers])
            Phone Service Churn % = DIVIDE(CALCULATE([Total Customers],'01 Churn-Dataset'[PhoneService]="Yes",'01 Churn-Dataset'[Churn]="Yes"),CALCULATE([Total Customers],'01 Churn-Dataset'[PhoneService]="Yes"))


- Step 8: Slicers added for Gender, Multiple Phonelines, Internet Services, Contract type.
- Step 9: - Cards, Multirow card, Donut, bar & line charts are used to present the above data.

# Insights

A Double page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

## Key Findings:

The overall churn rate stands at 26.16%, which calls for immediate attention.
A demographic breakdown reveals that senior citizens have a churn rate of 41.7%, significantly higher than other segments.
Similarly, customers on month-to-month contracts exhibit an identical churn rate of 41.7%.
Services such as Internet, Streaming TV, Streaming Movies, & Phone Services have over 25% churn rate, indicating dissatisfaction or unmet needs.

## Strategic Recommendations:

Yearly Contracts: Encouraging customers to opt for annual contracts could be a game-changer, as they show a lower propensity to churn.
Tech Support: There is a noticeable trend of churn following tech support tickets. Enhancing the quality and resolution of technical issues is imperative.
Our goal should be to create a more stable customer base by addressing these areas with targeted strategies. Implementing these changes could significantly reduce our churn rates and improve overall customer satisfaction.
