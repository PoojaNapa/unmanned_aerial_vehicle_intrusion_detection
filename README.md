## Unmanned Aerial Vehicle (UAV) Intrusion Detection
The project focuses on designing an Unmanned Aerial Vehicle intrusion detection system using various machine learning binary classification techniques. The Unmanned Aerial Vehicle(UAV) for Intrusion Detection dataset contains encrypted Wi-Fi traffic records collected to classify the traffic as a UAV or not. This binary classification is useful to detect UAVs that could pose a threat to the security and privacy of the public. In this dataset, 3 UAVs are considered, namely - Parrot Bebop 1, DBPower UDI, and DJI Spark. Overall, there are 6 datasets, 2 in each category of the UAV. A bidirectional and unidirectional traffic flow is considered for each of the UAVs. In the bidirectional traffic flow, there are 54 features in total (i.e., 9 statistical features like mean, median, standard deviation, etc., for 2 sources - packet sizes and packet inter-arrival time for 3 directional flows – uplink, downlink, and the total traffic flow). In the unidirectional traffic flow, there are 18 features (i.e., 9 statistical features for 2 sources).

## Baseline Model
Developed a baseline model with the raw dataset. Considered bidirectional and unidirectional 
datasets separately and included all the features. On these datasets, the following machine learning 
classification techniques were applied:-
1) Logistic Regression
2) K-Nearest Neighbors, with k =3 (KNN)
3) Linear Discriminant Analysis(LDA)
4) Decision Tree
5) Bagging
6) Random Forest, with √54 ~ 7 features in bidirectional dataset and √18 ~ 4 features in the 
unidirectional dataset
7) Boosting
8) Support Vector Machine, with radial kernel (SVM)

## Approach 1: Manual Inspection
After visualizing the dataset, eliminated the features based on their contribution to the 
dataset and the classification output. Initially, the features with low spread of data and many outliers were dropped. Along with these features, features that were present only in bidirectional dataset were also dropped. The bidirectional and unidirectional datasets were combined to form the dataset. This dataset consisted of 6241 datapoints and 11 features. 

## Approach 2: Regularization using Lasso Regression
In this approach the raw dataset was taken and after the uncommon features between bidirectional and unidirectional were eliminated, the datasets were combined. Therefore, the training dataset had 6241 datapoints with 18 features before regularization.

## Approach 3: Principal Component Analysis (PCA)
The Principal Component Analysis is used to reduce the dimensionality of the dataset by forming principal components that are linear combinations of all the features from the dataset. These principal components capture features and the regions where data vary the most. Each principal component is uncorrelated and hence orthogonal to each other. In this way, the dataset is explained efficiently using PCA. After plotting the datasets, the spread of the two classes were easy to interpret. The bidirectional dataset, there is a clear separation between the 0 and 1 class, whereas in unidirectional dataset, the dataset seems to be more correlated. For this approach, the bidirectional and unidirectional datasets were considered separately and PCA was applied on each of them. It was found that the first 4 and first 2 principal components explained 85% variance in the bidirectional and unidirectional datasets, respectively.

## Files
UAV_DD-DV_Pickle.ipynb
	This file will load the dataset , visualize it and carry out preprocessing. Running this will file produce the pickle files needed for running the other files. 
	"f = h5py.File('pub_dataset1.mat')" Kindly mention the dataset paths in this line corresponding to all datasets.
	
UAV_Main_Baseline_ALL.ipynb
	Kindly run the "UAV_DD-DV_Pickle.ipynb" to create the pickle files.
	Running this file will develop models using Logistic Regression , KNN, LDA, Decision Tree , Bagging , Random Forest , Boosting and SVM. The raw dataset with complete feature set is used for training and testing.
	
UAV_Main_App1_v_1.ipynb
	Approach 1: This file combines the unidirectional and bidirectional dataset and then performs the binary classification for features 4, 5, 9, 10, 11, 12, 13, 14, 15, 16, 17 using Logistic Regression , KNN, LDA, Decision Tree , Bagging , Random Forest , Boosting and SVM.
	Kindly run this file after running the "UAV_DD-DV_Pickle.ipynb" as it uses the pickle file to import the dataset.
	
UAV_Main_App2_v_1.ipynb
	Approach 2: This file imports the dataset from the pickle file created after running "UAV_DD-DV_Pickle.ipynb". Lasso regression is used do the feature extraction and then the following models were developed. Logistic Regression , KNN, LDA, Decision Tree , Bagging , Random Forest , Boosting and SVM

UAV_Main_App3_PCA_ALL.ipynb
	Approach 3: This file uses PCA for dimensionality reduction from 54 to  5 in bidirectional dataset and 18 to 3 for unidirectional dataset. As a pre-requistie run the "UAV_DD-DV_Pickle.ipynb" to create the pickle files to be used here.
	

## References
https://www.analyticsvidhya.com/blog/2017/09/understaing-support-vector-machine-example-code/ - Code reference for Support vector Machines(SVM)
https://harvard-iacs.github.io/2018-CS109A/sections/section-5/solutions/ - Principal Component Analysis code reference