# Impact of COVID-19 on the US Housing Market
by: Marissa Tan<br>

## Introduction
Over the past decade, US home prices have experience steady growth. Location has been the chief criteria dictating the price and the potential buyer, but where is the location? After the pandemic, has the requirements for the property location changed. <br><br> 
Since March 2020, when COVID-19 virus has raged through the United States and around the world, this deadly virus had left a trail of numerous deaths and lingering effects of illnesses. To contain the spread of COVID-19, our way of life took a drastic turn. Physical presence at and long commute to work have been delegated to remote attendance in a part of the dwelling. A warm hug or a firm handshake have been replaced with six feet distance or a quick fist bump. Now, it seems the period of endemic is at hand. The luxury of working remotely is a possibility. Working from a far distance is not a barrier as long as internet infrastructure is in place. One could be in New York and be working forty hours a week in California. Once, our job dictates where one live which no longer is. <br><br>
The location of the house is an important issue to a home developer, home buyer or seller. The home developer will plan where the community will be. The creation of the community will be based on the demand of the buyer. Being able foresee the needs of the buyers will dictate the price of the property. The more in demand the location of the property is the better the asking price.<br><br>
The goal of this study is to use machine learning with the US county data and the real estate data. It will focus on the correlation of density, rural percentage, and average listing price. <br><br>

## Research Question(s)
1. Has there been a change in house prices since COVID-19? <br>
2. Has there been a change in in-demand house location since COVID-19?<br>
3. Has there been a change in buyers' house buying criteria since COVID-19? <br><br>

## Dataset
<img src = 'https://github.com/tmarissa/marissa_DATA606/blob/main/Images/Data%20Source.PNG'/><br><br>

## Unit of Analysis
- US County is the unit of analysis for this research. This unit is represented by the Federal Information Processing Standard (FIPS) code which is 5 digit code that uniquely identifies counties in the United States.
- Population and land area dataset are joined with FIPS code to use to derive the density.
- FIPS code is also used to joined the density and real estate data which are used for visualization and machine learning.<br><br>

## Merging Dataset Strategy
<img src = 'https://github.com/tmarissa/marissa_DATA606/blob/main/Images/Capstone%20Merges.png' width='750'/><br><br>
1. Population and Land Area dataset are merged in FIPS column. <br>
2. Result 1 merged with rural percentage dataset on FIPS column. <br>
3. Result 2 merged with real estate dataset on FIPS column. <br><br>


## Variables/Measures
<img src = 'https://github.com/tmarissa/marissa_DATA606/blob/main/Images/Data%20Variable.PNG' width='1000'/><br><br> 
- The real estate dataset has 210,602 observations and 40 features.
- Average listing price (counties) will be used as the dependent variable and will be to analyze during 2016 to 2021.
- Density of the area (counties or state) and rural percentage will be used to analyze before COVID-19 (2016 to 2019) and after COVID-19 (2020 to 2021).
- There will be 13 variables used as independent variables, Average Listing Price M/M, Average Listing Price Y/Y, County, Date, Density, FIPS, Median Listing Price, Median Listing Price Y/Y, Median Listing Price M/M, Rural Percentage, Rural Catagory, State, Total Listing Count. <br><br>

## Implementation (Model)
K-means will be used with in this study. It is one of the most popular of these clustering algorithm. Clustering is a technique to find groups of similar objects which is objects that are more related to each other than to objects in other groups. This choice of modeling is implemented to study the relationship among the data items which is unknown. In this prototype based clustering, centroid and silhouette elbow method will be used. Centroid (average) of similar points with continuous features. 
The limitations of K-means is the need to specify the number of clusters, k, a priori. Silhouette elbow method is useful techniques to evaluate the quality of the clustering to help us determine the optimal number of k.<br><br>
The steps are summarized to: (Rascha, 2015, p.142)
1.	Randomly pick k centroids.
2.	Assign each sample to nearest centroid.
3.	Move the centroids to the center of the samples.
4.	Repeat the iteration until the cluster assignment do not change or a user-defined tolerance or maximum number of iterations is reached.<br>

Principal Component Analysis (PCA) is “a projection technique that is used to reduce the number of dimensions for a dataset. It works by finding a lower dimension in the data such that the variance is maximized.” (Chen, 2018, p. 243)
These above processes will be applied to average listing price, rural percentage and density which attempts to understand the correlation of the different clusters.  


## Exploratory Data Analysis
<img src = 'https://github.com/tmarissa/marissa_DATA606/blob/main/Images/Correlation%20Matrix.png' width=1000/><br>
In this matrix, the highest correlation is between average listing price and median listing price which is 83%. The second highest correlation is between average listing price yy (yearly change) and median listing price yy (yearly change) which is 64%.<br><br>

<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/Counties%20Prices%20Increases%20Graph.PNG" width=800/><br><br>
In 2018 and 2019 (Pre-COVID), around 55% to 56% of the counties experience a price increase. However, in 2020 and 2021 (Post-COVID), 60% to 61% of the counties experience a price increase. Comparing between Pre-COVIS and Post-COVID, the counties also experience lower downs on 2018 and 2019.<br><br>

<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/Rural%20Percentage%20and%20Density.PNG" width=1000/><br><br>
Rural percentage and density have a negative relationship. The bigger the density the lower the rural percentage which means a county that has high density will have low rural percentage which makes an urban area.<br><br>

<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/Rural%20Percentage%20by%20States.PNG" width=1000/><br><br>
This scatter plot shows the relationship of states and rural percentage. The blue dots represent urban counties. The green dots represent the rural counties. Every state has different rural percentages and categories. District of Columbia is an urban area and is represented by one blue dot. Connecticut, Delaware, New Jersey, and Rhode Island doesn’t have rural counties. They are urban states with different degree of rural percentage. Hawaii has almost all urban counties except for one rural county.<br><br>

<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20FIPS%20ALP%20Choropleth.PNG" width=1000/><br><br>
In 2021, the color for the whole United States map deepens which means there is an overall increase in average listing price. However, the West Mountain Region's, Arizona, Utah, Colorado, and Montana, colors are more intense.<br><br>

<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20State%20ALP%20Change%20Choropleth.PNG" width=1000 width=1200/><br><br>
In 2019, West North Midwest states, South Dakota, Nebraska, Kansas, and Oklahoma with a West Mountain state, Nevada, experienced a higher increases than the most of the other states. In 2021, the Western region has a better percentage increase than the Eastern region. The West Mountain states, Montana, Idaho, Utah, and Arizona, have the highest increases percentage increase of around 40% compared to around 20% in 2019.

## K-Means Model Execution
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%20FIPS%20K-Means%20Scatterplot.PNG" width='1000' /><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2021%20FIPS%20K-Means%20Scatterplot.PNG" width='1200'/><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20FIPS%20K-Means%20Choropleth.PNG" width='1200' /><br><br>
In 2019, the predominant brown cluster begins from Midwest region going towards East. In 2021, the cluster in the Midwest region is isolated from the other regions. The formerly brown East North Central region onward to east belongs to their own cluster.<br><br><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%20AZ%20K-Means%20Scatterplot.PNG" width='1000' /><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2021%20AZ%20K-Means%20Scatterplot.PNG" width='1200'/><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20AZ%20K-Means%20Choropleth.PNG" width='1200' /><br><br>
In 2019, Greenlee County has a low average listing price of 239K, low density 5, and rural percentage 46.57 and ranked 14th in 15 high priced average listing price counties in Arizon. Greenlee county became 5th most expensive county in Arizona with an average listing price of 687K in 2021. La Paz County, a rural area with 56.33 rural % and a low density of 5, belongs to the same cluster as Greenlee county in 2019. In 2021, La Paz and Greenlee Counties clustered with a higher average listing priced Gila County.<br><br><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%20MA%20K-Means%20Scatterplot.PNG" width='1200'/><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2021%20MA%20K-Means%20Scatterplot.PNG" width='1200'/><br><br>
<img src ="https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20MA%20K-Means%20Choropleth.PNG" width='1200'/><br><br>
In 2019, Berkshire and Hampshire counties belong to one cluster. Berkshire has a lower 139 density and 31.60 rural percentage than Hampshire has a 307 density and 21.44 rural percentage. In 2021, Berkshire is in its own cluster. Its average listing price rose from 631K to 975K. Hampshire clustered with Hampden. Both Hampshire and Hampden counties are more urban and lower density than Berkshire but their average listing price is a lot less than Berkshire.<br>  

## Interpretations and Conclusions:
1. Has there been a change in house prices since COVID-19?<br>
> Both the visualization and machine learning techniques reflect the change in house prices since COVID-19. The pre-pandemic, around the 56% of the counties experience a price increase. The post-pandemic, around 61% of the counties experience price increase.  The [Comparison of 2019 and 2021 United States’ Counties Choropleth Map](https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20FIPS%20ALP%20Choropleth.PNG) shows the deepening of the shades across the United States in 2021 compared to 2019 which meant that average listing price increased. The [Comparison of 2019 and 2021 United States' States Choropleth Map](https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20State%20ALP%20Change%20Choropleth.PNG) shows that the average listing price changed has an increased from 20% to 40%.<br><br> 
2. Has there been a change in in-demand house location since COVID-19?<br>
> There is a change in in-demand house location since COVID-19. The average listing price was used to measure of the demand of house location. Demand being constant, too low of inventory will increase the listing price of the property while too high of inventory will decrease the listing price of the property. The inability to sell the property will result to the decrease of listing price. Before the pandemic, District of Columbia, second to the highest average listing price, is a high urban area with zero rural percentage. During the pandemic, District of Columbia was delegated to the third highest listing price. While many counties enjoyed increased in average listing price, District of Columbia dropped its average listing price. In Arizona, Greenlee County, a low density. There is a demand for low density and high rural percentage in urban areas.<br><br>
3. Has there been a change in buyers' house buying criteria since COVID-19?<br>
> There is evidence that the buyers house buying criteria change because the choropleth map using the K-means clustering for the average listing price, density, and rural percentage shows the partition of the clustered. In 2019, there used to be 2 dominant clusters that separate the west and east region of the US. After the pandemic, the Midwest region has its own cluster and separates the east and the west regions. However, further investigation is needed because the visually seen cluster are made up of many other smaller clusters as shown in the [Comparison of 2019 and 2021 United States' Cluster Choropleth Maps](https://github.com/tmarissa/marissa_DATA606/blob/main/Images/2019%202021%20FIPS%20K-Means%20Choropleth.PNG). <br><br>
### Powerpoint presentation - [The Impact of COVID-19 on the U.S. Housing Market](https://github.com/tmarissa/marissa_DATA606/blob/main/Data_Info/Impact%20of%20COVID-19%20on%20US%20Housing%20Market.pdf)
### YouTube of the Powerpoint presentation - [The Impact of COVID-19 on the U.S. Housing Market](https://www.youtube.com/watch?v=qvV6QUA4NIQ).

## References
Chen, D. Y. (2018) Pandas for Everyone. Boston: Pearson.<br><br>
Raschka, S., Mirjalili V. (2015, September). Python Machine Learning. (2nd edn.) Packt: Birmingham.  
