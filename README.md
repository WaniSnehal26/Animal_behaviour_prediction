# Animal_behaviour_prediction



# Dataset
https://drive.google.com/file/d/1IQ6mPZU-3z0kYYWU7gH0P7Be_qwljsF1/view?usp=drive_link

# Introduction-  
     Monitoring the behavior of livestock is crucial for effective management. Behaviour information can provide insights into the productivity, health, and welfare of animals. Understanding animal behavior is a complex and vital field of study. One of the key challenges in this endeavor is the ability to accurately capture and analyze animal movements in their natural environments. Traditionally, this task was labor-intensive and often limited by human observer’s presence, which can alter the animal’s behavior. Recent advancements in technology have opened up new avenues for studying animal behaviour, particularly through the use of accelerometer. These small, lightweight sensors, capable of measuring acceleration along the X, Y, and Z axes gives us data about animal motion. When combined with timestamps, accelerometer data offers an unprecedented opportunity to gain insights into animal behaviour with a high degree of accuracy and granularity.
       In this project we have raw accelerometer data (x, y, z) axes and timestamp. And our objective is to cluster the data with respect to behavior of cattle and to predict the rumination for encountering early disease using machine learning models. 
      By processing data from the (x, y, z) axes along with timestamp, we aim to decipher patterns, behaviours, and activities exhibited by the animals under study. Machine learning techniques to accelerometer data enables us to shed light on the behavioural patterns and activities exhibited by the animals. Machine learning algorithms can process vast amount of data to derive behavioural metrics, such as activity levels, rest periods, and specific behaviours. By analysing changes in accelerometer data over time, we can identify unusual behaviours or deviations from normal activity, which may indicate stress, illness, or other significant events. By early analysing such effects on cattle we can prevent business losses. From business point of it’s very important. 
     We will dive into the methodology, data preprocessing, and machine learning techniques employed to analyse accelerometer data from animals. 


# Data Pre-processing-   
     Before going for data pre -processing we have to understand the meaning of each axes. X-axes- indicates the forward and backward movement of cattle (Horizontal or parallel to the ground). Y-axes- indicates the vertical movement of cattle (perpendicular to the ground). Z-axes-indicates the movement across the body of animal (perpendicular to the animal body)
    Data preprocessing is a crucial step in any machine learning project, especially when dealing with accelerometer data from the X, Y, and Z axes along with timestamps for an animal behaviour project. Preprocessing involves cleaning, transforming, and organizing the data to make it suitable for analysis. 
    Begin by loading and inspecting the raw accelerometer data to understand its structure and contents. We have (14595853 Rows and 4 Columns). After loading the dataset we will check for missing values. In this data set we don’t have any missing values. 
     Here data is collected continuously over time so creation of time windows is a fundamental preprocessing technique. We can create 3s, 5s, 10s, 20s window but we don’t want to lose a lot of data points so will create 3s time window because we have data available in micro seconds in the timestamp column. A short time window of 3S (30 observations) has been found to be the best fitting to compute a list of metrics to be used in the model. These time windows are non-overlapping. The primary objective of creating these time windows is to facilitate the analysis of data in smaller, more manageable chunks, to extract meaningful insights from complex datasets. We will create 3s time window by taking mean of data points. After creating time window we have (4,83,600 Rows).

# EDA-
      EDA helps us to gain insights into our dataset, understanding characteristics. As we saw in the above subpoint we are having 4 columns namely Timestamp, x , y, z axes. And we have created time window of it. Now we will study statistical measures of each axes. After creating the time window we will check statistical measures (mean, variance, standard deviation (Std), etc.) of each axes. 
     After going through we have tried visualizing each axes, mean, std, etc. Here mean gives us the idea about the average data points in the axes. Also, we have calculated minimum, maximum value and median of each axes. From the statistical measures we can conclude that the variance of x axes is the highest which means the spread of the data if maximum in the x axes. And variance of y axes is lowest.         
    Visualising each axes to get the idea about data spread, pattern, etc

    Correlation for x, y, z axes:
    Pearson correlation measures the linear relationship between two continuous variables. It ranges from -1 (perfect negative correlation) to 1 (perfect positive correlation), with 0 indicating no linear correlation.
    Formula: r = Σ ((X - X̄) (Y - Ȳ)) / (n - 1) * (SX * SY), where X and Y are the variables, X̄ and Ȳ are their means, SX and SY are their standard deviations, and n is the number of data points.


# Feature Extraction-
      After creating the 3S time windows we will go for feature extraction. Within each time window, extract       relevant features that capture the characteristics of interest. These features can be used as inputs for various analysis tasks. In this project we have tried multiple features like mean (x, y, z axes), Std (x, y, z axes), RMS, Magnitude. Here mean and Std are statistical features. And RMS, Magnitude are time domain features. The Magnitude and RMS have been estimated for each observation as the root squared of the sum of the squared tri-axis accelerations (x, y, z)


# PCA & K-Means Clustering-
    We use one of the most commonly used clustering algorithms, k-Means with the usual Euclidean distance and RMS. However, applying clustering as is will result in clusters which will not be characterizable in terms of the chosen features due to the high dimensionality.     
     Principle Component Analysis (PCA) is a technique which is used for dimensionality reduction and data exploration. After a PCA model is created, we have a set of PCs that serve as a mean to reduce the dimensionality of the original variables. Here, we are transforming (x, y, z, RMS, Magnitude) these columns to the two columns namely PC1 and PC2. Our purpose is to make clusters with PC1 and PC2. Objective of applying PCA is to reduce dimensionality so that we can make clusters of the data.
     K-Means Clustering Algorithm is unsupervised algorithm used to group the data points in clusters based on similar data points. In this project we have to identify the activities of cattle that is why we are performing k-means. We have to divide data points into 4 clusters. So, the value of ‘k’ is already known. 
    After getting the clusters the important task is to label the clusters and is the difficult task it requires a lot of statistical analysis and opinion from domain expert. In this task we have to identify the clusters for 4 activities namely Rumination, Standing, Other Activities and Eating. To identify the clusters, we will use the domain knowledge like the detail study of the x, y and z axes. While Ruminating cattle will be in steady position there will be less movement across all axes. While performing other activities like running, walking, etc. movement in all axes will be maximum. In such way we can identify the activities of cattle. By visualizing each axes of each cluster and by observing the median value of each axes of each cluster we can conclude.


# Future scope-
    Future scope of this project is continues going to expand due to advanced technology, increasing awareness about animal welfare, increasing population, increasing demand for dairy products.
    1.	Future projects can explore more sophisticated algorithms, such as deep learning and reinforcement learning, to model complex animal behaviours and interactions. These techniques can improve prediction accuracy and handle larger and more diverse datasets.
    2.	Future projects can combine data from various sources, including GPS tracking, to create a more comprehensive understanding of animal behaviour.
    3.	Predictive analytics can be used to optimize breeding programs by identifying the most suitable time for insemination. Accurate predictions can lead to higher calf production rates and improved genetic diversity.
    4.	As climate change affects weather patterns and temperature fluctuations, predictive models can help cattle farmers adapt by forecasting optimal grazing times, heat stress conditions, and resource allocation strategies.
    5.	Future projects can focus on improving resource efficiency in cattle farming, including optimized use of water, feed, and pasture resources. Predictive models can help reduce waste and enhance sustainability.
    6.	Predictive models can assist cattle farmers in making informed decisions about when to sell their cattle, considering market conditions and pricing trends.
    7.	The future scope includes educating cattle farmers and agricultural professionals in the use of predictive analytics and data-driven decision-making to enhance cattle farming practices.
