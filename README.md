# Prediction-of-skills-and-recommendations-on-professional-certification

### To run the model 

## Web Scraping

1-Go to "web_scraping_links.ipynb" then run the code to collect ("Job Name", "Date", "Link") in this code each site will be dealt with separately


![1](https://user-images.githubusercontent.com/132696346/236584777-97a3df43-5be2-4604-a1f8-5a3ab896caeb.png)

![2](https://user-images.githubusercontent.com/132696346/236592674-fab0d6ab-25e8-49b8-a8ff-670316dbd376.png)

In this code, you only need to pay attention to the number of functions in the code and the location, so as not to cause collection time problems.

![3](https://user-images.githubusercontent.com/132696346/236633111-8c29408d-666c-43f2-b652-1c7518f52798.png)


After complete run this code will be create two file ("Bayt_Data_final.xlsx", " Wadhefa_Data_final.xlsx") this file moved tow next step 


## Analysis

2- Analysis code " Job_description.ipynb" in this code first read file coming from web scraping then collect job description, and cleaning dataset.

![4](https://user-images.githubusercontent.com/132696346/236633132-cfc26ce3-75b0-4919-844d-abb510c7a841.png)


![5](https://user-images.githubusercontent.com/132696346/236633165-d1cf17ca-3f89-46a4-9174-a8da76ed6a23.png)


![6](https://user-images.githubusercontent.com/132696346/236633187-8acbd847-a39c-4401-b175-56667ff66aae.png)


Import SKILLNER 

![7](https://user-images.githubusercontent.com/132696346/236633197-61557257-7a03-4e4e-b883-6e1086d40343.png)


After that reading (skills.xlsx) file 
Skills file content all keyword for IT skills (collecting from https://lightcast.io/open-skills/categories)
In case need more skills put more keywords can edit of excel file

![8](https://user-images.githubusercontent.com/132696346/236633315-e2056b41-2681-4229-8742-53eaa7181fc6.png)

Matching between job description and stop words.

![9](https://user-images.githubusercontent.com/132696346/236633357-f18472b6-56b9-49b9-ae62-d130f21c8f2e.png)

Skills list and create ("Wadhefa_for_Prediction.csv", "Bayt_for_Prediction.csv") files for moved to next step (each site create separately file). 

![10](https://user-images.githubusercontent.com/132696346/236633380-13cca550-7de0-467f-bb77-05beb5f6e5b4.png)

Put skill type.

![11](https://user-images.githubusercontent.com/132696346/236633390-081236b4-c6ca-45cd-9ecc-ea2c2b0f2de2.png)

Skills list 

![12](https://user-images.githubusercontent.com/132696346/236633762-86a1603c-73aa-4f31-bc97-1cd2c340b9b6.png)


And after end Wadhefa.com data go to Byte.com data and applying same steps (The code is built to handle each site separately)

After that Marge result with other and create "Merge Data_final.xlsx" file content final result analysis (Result are skills required today in the market)

![13](https://user-images.githubusercontent.com/132696346/236633781-5cb47c15-50b4-419f-85e0-ffc5809b33df.png)



## Pre-processing
3- Pre-processing before machine learning read each file ("Wadhefa_for_Prediction.csv", "Bayt_for_Prediction.csv").

![15](https://user-images.githubusercontent.com/132696346/236633825-11781e0e-7032-4387-8cfb-6a92ffbec398.png)
![16](https://user-images.githubusercontent.com/132696346/236633841-96bcd87c-f234-4dcc-8c19-3e3db22e571d.png)


Delete column not necessary to predict and concatenate all row.

Then separation data into two array soft_skills = [], hard_skills = [] (depending on soft skills keyword)

[In order to obtain better results in prediction because if they are not separated, soft skills always take the highest rate because they are the most visible compared to hard skills and affect the prediction results].

![17](https://user-images.githubusercontent.com/132696346/236633868-25075906-b8f2-49f8-b9bc-28a1da707bb9.png)

Added the counter, determined the lowest and highest value, calculated the rate, added the label coding tool, and created a final prediction file ("hard_final.csv", " soft_final.csv") are moveing to next step. It contains ("skills_list", "count", "rate", "skills_list_catogrised")

![18](https://user-images.githubusercontent.com/132696346/236633879-46b42700-61e1-48d7-bd38-a3096a05911e.png)


## Prediction (Model Machine Learning)
4- Model Machine learning " Model.ipynb" in this code first time determined 'How many skills do we want to predict?'

![19](https://user-images.githubusercontent.com/132696346/236635450-a7428b35-8539-48ab-b166-092b85d17cd0.png)

Then read finals files ("hard_final.csv", " soft_final.csv") in each time read one file, after that delete unnecessary columns and fit X and Y 

![20](https://user-images.githubusercontent.com/132696346/236635475-db34dd40-0381-458c-9b0d-489a3d627d17.png)

Then Splitting the data for training and testing the model

![21](https://user-images.githubusercontent.com/132696346/236635497-64ac09b5-fdbe-4075-a461-0f15d8ca9695.png)

Then calculated score and D2 absolute error score for each model.

![22](https://user-images.githubusercontent.com/132696346/236635542-457c68ac-20cd-46d9-b5ac-479e68898cce.png)

Then create file content list of predicted skills.

![23](https://user-images.githubusercontent.com/132696346/236635586-4c4eb51a-f7d4-4924-aded-e77157d21e44.png)

This CSV file create moved to next step.



## Recommendation

5- Recommendation for professional certificates " recommendation.ipynb " 
This code has two mine array ["main_skill_category "," main_certificates "] each one has many small arrays.

The idea of the recommendations is that the Information Technology (IT) Sub-Categories in Information Technology are grouped according to a classification EMIS database, small arrays are Sub-Categories name in "main_skill_category " is contains skills name keyword in each one, in "main_certificates" contains professional certificates in each one.

![24](https://user-images.githubusercontent.com/132696346/236635649-4ed9aac4-b8db-4a31-a585-7e4be8f34355.png)


![25](https://user-images.githubusercontent.com/132696346/236635662-9543d1a2-d90d-4857-bd61-3f5c515c8097.png)


Then read file have result prediction. 


![26](https://user-images.githubusercontent.com/132696346/236635671-cbd6da9e-4845-4908-a8eb-0d9d2d9b9ca4.png)

It matches skills, prediction outputs, and arrays to find which ones are within which Sub-Categories to select appropriate professional certificates.

![27](https://user-images.githubusercontent.com/132696346/236635695-eb6464ac-3c18-4f15-acc9-0f46cd90d79e.png)








