Repository for Machine Learning Challenge

Thesis:
1)	The purpose of this data study is to create a Machine Learning model to predict exoplanets, based on data harvested from the NASA Kepler space telescope.

Data Cleaning (Assumptions):
1)	For the x-values, 13 features were selected, including planet radius, orbit period, transit duration, stellar temperature, and stellar gravity.  
2)	For the y-values, we selected the KOI Disposition (Planetary Status) to be the control group against which to run the supervised models.  The KOI Disposition can be 1 of 3 values and refers to whether a given object in the data has had its suspected “planethood” confirmed.  The 3 values are as follows. 
a.	“Confirmed” assumes that the object in question has been confirmed to be an exoplanet.  
b.	“False positive” assumes that the object in question has been confirmed to not be an exoplanet.
c.	“Candidate” assumes that the object in question has not yet been confirmed or refuted to be an exoplanet.
3)	Since “Candidates” have not had their “planethood” confirmed or denied, we removed the rows for “Candidate” data, and used only the “Confirmed” and “False positive” exoplanets to test against.  
4)	This process was followed for cleaning the data for both models (SVM and Logistic Regression).  
5)	Also, findings indicated a wide range for the data points in the “Planet radius” column (the “koi_prad” column in the original data set.  Exploratory analysis on the first model (SVM) suggested that the model performed better when outliers were removed.  Consequently, objects with a planet radius of 10,000 or more were removed from the data set.  
6)	Finally, columns listing the margin of error (columns with names ending in “_err1” and “_err2” in the original data set) were not included in the analysis.  

Test Methods:
1)	Testing for both models consisted of 3 runs:  Run 1 for 13 features selected; Run 2 for 6 features selected; and Run 3, a grid search for the purpose of tuning the hyperparameters of the original 13 features.  
2)	The models were then saved based on the grid search parameters and exported to the Saved Models folder.  

Performance:
1)	Both the SVM model and Logistic Regression models performed similarly in the first and second runs.  See the table below for a high-level summary of scores; the full reports are included in the Images folder.  
a.	Both models achieved the same accuracy score on Run 1, with most precision and recall scores remaining within a margin of 1 percentage points.  
b.	Both models scored within a point of each other in terms of accuracy on Run 2.  For some reason, the SVM model did not register precision or recall scores for the “False positives” on Run 2.  This requires further investigation.  

	SVM Model	Logistic Regression
Run 1 Score	0.72	0.72
Run 2 Score	0.65	0.66
Run 3 Score	0.76	0.72

2)	Where the models differed was in Run 3, the grid search.  For this run, the Logistic Regression model scored the same as on its initial run.  However, the SVM model scored 0.76, showing an improvement of 4 percentage points over its Run 1 score.  This suggests that the SVM has greater performance potential on this set of data.  
3)	On Run 3 the SVM achieved an f1 score of 0.81 for “Confirmed” planets, but a score of 0.68 on “False positives.”   

Conclusions:
1)	With an accuracy rate of approximately 70-75% each, neither model proved to be a strong predictor of planethood for the Kepler data.  While the hyper tuned SVM model returned an f1 score of 0.81 for “Confirmed” planets, it fared less well on “False positives.”  This leaves room for further refinement in both categories.
2)	Possible areas of further study to improve prediction of exoplanets include the following:
a.	Further cleaning of data to remove outliers from other features (as was done for the “Planet Radius” feature).  
b.	Training the data by means of a more recent ML model, such as a neural network.  
