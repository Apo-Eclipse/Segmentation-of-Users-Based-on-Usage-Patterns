# Abstract
This paper explores mobile application usage patterns in three French cities—Lyon, Marseille, and Montpellier—using data from the NetMob 2023 Challenge dataset. The paper seeks to determine when and where individuals interact via popular social media and entertainment apps (Instagram, Twitter, and YouTube) to determine the most effective times and locations for marketers to advertise. The data collected represents instances of network traffic varying with time and location. The best time and locations for advertising are evaluated based on the manipulation of the data which includes preprocessing, visualization, clustering, and classification. The final results and discussion provide useful information to app owners and advertisers to enhance their ad pricing strategies and increase marketing reach.

# Keywords
Data Analysis - Usage patterns -Data Traffic - Clustering – Classification - Outlier Detection

# Methdology 

This research aims to analyze and draw conclusions about the advertising field. The target is to manipulate data from 3 cities in France (Lyon, Marseille, and Montpellier) to reach a statistical and visual analysis to assist people investing in the advertising field.

# *Data Collection*
Those cities were selected due to their diversity in population and difference in age demographics. The data used is from NetMob’s 2023 Challenge, which has been collected using open-source geospatial data and measurements from Orange, a major company in the mobile network field. Originally, it was collected utilizing coverage information from a commercial radio-frequency signal propagation tool. Its computation involves probabilities and applying Bayes’ theorem. For each city, there will be an analysis of the following applications: Instagram, Twitter, and YouTube. The apps were specifically chosen due to their widespread popularity in France. Per each application, there is a statistic of its network traffic every 15 minutes for 77 days (about two and a half months) starting from March 16, 2019. 

# Data Variables 
The main variable in the data is the network traffic concerning time. Each application will be analyzed separately and record the observed difference between all of them for each city. After deciding on the peak hours of each application for every city, a comparison between different cities per application will be made.

# Data Preprocessing 
Handling null values
The data has been preprocessed to determine and detect outliers before drawing any conclusions. For each given day, scanning has been done to find the null values or non-numerical traffic values that could lead to crashing the program. Then all of them were replaced, with the average traffic for the rest of the day. That was found only on 31 March 2019 for four consecutive slots with a total duration of one hour from 11 pm to midnight. 

# Handling outliers
Further, as there is a possibility to find outlier values that are very different from the rest of the data, the average traffic value for each day’s hour was calculated and then all outliers were excluded using The Interquartile Range (IQR) method. IQR is the range between the first quartile (Q1) and the third quartile (Q3) of a dataset. The first quartile (Q1) is the value below which 25% of the data points lie, and the third quartile (Q3) is the value below which 75% of the data points lie. The IQR measures the spread of the middle 50% of the data. 
IQR = Q3 - Q1 
LowerBound:Q1-1.5×IQR 
UpperBound:Q3+1.5×IQR 

# Data Reduction
The data was manipulated using data frames and the NumPy library in Python methods. After removing all values that do not belong in the Interquartile Range and fixing the miswritten data, a new data frame was created. All the remaining days were grouped, each according to their respective day of the week (e.g., all Mondays together, all Tuesdays together, etc.). Consequently, all days were reduced into a list of seven groups representing the average network traffic of their respective day of the week.
Data Segmentaion and Visulaization 
Utilizing the previous steps the users have been divided into segments based on the following:

# Data Visualization using HeatMap
After the data cleaning and reduction part, a heat map was created to visualize the average traffic for each day of the week. This assisted in identifying patterns and variations across different days, providing a clear and intuitive understanding of traffic distribution. 

After, the average hourly traffic for each day of the week has been visualized using a heatmap. It was easy to extract information like the hourly traffic patterns, and daily summaries and plot the peak hours for the entire city. 

# K-Mean Clustering 
The K-Means clustering technique was used to group geographic areas based on their daily average traffic patterns. 
The average traffic of all days was calculated to represent a single average traffic of each tile. Then the K-Means algorithm was applied to partition the areas into clusters with similar traffic patterns. 
K-Means Clustering:   d(x_i,c_j ) = √(∑_(m=1)^M▒(x_im - c_jm )^2 )
 c_j = _|C_j |^(  1 ) ∑_ ^ ▒x_i  ϵ C_(j ) |(|x_(i )-c_j |)|^2
To determine the optimal number of clusters (K) for the K-Means algorithm, the elbow method was used. It plots the sum of squared distances (inertia) from each point to its assigned cluster center for different values of K. The optimal K is the point where the plot shows a sharp bend (elbow), indicating a little decrease in clustering performance with increasing K. 
Inertia = ∑_(j=1)^K▒∑_(x_(i ϵ C_j ))^ ▒|(|x_i-c_j |)|^2 
After the average traffic for each tile for all days was determined using the K-Means Clustering technique, it was compared later to the population density map of the city.

# Classification

After computing the average traffic network of each tile in the city, a classification technique was applied to divide the city into sectors. The sectors ranged from very low to very high traffic. The classification was made using the percentile technique, where the city was diverged into five percentiles only. This provided insight into the diversity of the traffic of all city locations.

〖Class〗_i  = np.percentile(tilesofcitylist,20*i)
Where: 
“tilesofcitylist” is a list containing the average traffics of all locations.
i range from 1 to n where n is the number of percentiles
 np.percentile() is a function from the NumPy library in Python that computes the nth percentile of the provided data. The nth percentile is the value below which n percent of the data falls.

# Tools and Programming languages used
Every step was programmed by Python and its libraries such as NumPy, pandas, scikit-learn, matplotlib and seaborn. They were used for computations and data manipulation, visualization and clustering models. Jupyter Notebook was utilized for interactive analysis, and Excel/CSV for initial data handling. 
# Conclusion
Each of the previous methods was repeated for all three cities’ applications, and the results and findings are compared and discussed in the attached paper.
