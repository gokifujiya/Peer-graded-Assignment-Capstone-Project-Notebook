## Capstone Project - The Battle of Neighborhoods

## Segmenting and Clustering Neighborhoods in Scarborough, Toronto

## 1.	Introduction

These days a new type of industry has been born and grown up dramatically and is demanding more prominent professionals, including data scientists for cutting-edge technologies, such as artificial intelligence. It is also often observed that many professionals are seeking for a new job with better working conditions than those of their current position. Then it must be noted that these job seekers must be concerned not only about the working conditions of the new position, but also about the environment of new life because of changing the job. Generally, changing jobs requires moving to a different residence that is close to the place of work.

In this capstone project, a person lives on the West side of the City of Toronto in Canada. This area provides great amenities, including gourmet fast food joints, pharmacies, parks, grad schools, and the like. This person obtains a good job offer from an attractive company, which is, however, located on the East side of the city. Considering the great distance between the West and the East sides in Toronto, changing the job will require moving to the East side of the city. This person is caring about the possibility to live in a neighborhood having a similar environment.

Scarborough is a main area in the East side of the City of Toronto. Thus, Scarborough is a great candidate for the job seeker to live in for the new life and job. Therefore, it is desirable to search neighborhoods in Scarborough as to each characteristics and amenities to find out the best new residence for this person. In addition, it is preferable and interesting to compare Scarborough with the City of Toronto as well as Manhattan in New York City to analyze the findings about Scarborough more objectively.

## 2.	Description and the Source of Data

In this project, two data were used: Wikipedia and Foursquare API. Wikipedia provides various kinds of information on each page, including postal codes of Canada about each borough and neighborhood. The relevant Wiki page for this project was obtained by using read_html.Link. : https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M

To refine the data, cells were removed in which "Borough" is Not assigned. Then, the data were grouped by "Postal Code" and "Borough" and rows were combined that share the same Postal Code and Borough. If a cell has a borough but a Not assigned neighborhood then the neighborhood was assigned as the same as the borough.

Next, geocoder was used to get data for information as to longitude and latitude for each area. After checking the data type and the size of the two data, the two data frames were combined because they share information about postal codes. Then, the index column was removed and “Neighbourhood” was renamed to “Neighborhood” to avoid confusion.
![](13.png)

On the other hand, Foursquare API provides information as to various matters and events in different venues in different neighborhoods in a specific borough. The information includes venue name, location, category, menus, photos, and so on. This provider produces information of venues within a certain distance from a specific place with the determined longitude and latitude. Thus, this Foursquare location platform is extremely convenient to explore information that is necessary for this project.

## 3.	Methodology Consisting of the Main Component of the Report, Description of Exploratory Data Analysis, Inferential Statistical Testing, and Choice of Machine Learning

### Create a Map of Toronto and Scarborough

First, geopy library is used to obtain the latitude and longitude values of Toronto city and to create a map of Toronto with neighborhoods superimposed on top.
![](17.png)

Second, the original data frame was sliced to create a new data frame of the Scarborough data. geopy library is used to obtain the latitude and longitude values of Scarborough and to create a map of Scarborough with neighborhoods superimposed on top.
![](20.png)

Third, Foursquare Credentials and Version were defined to extract the neighborhood's latitude and longitude values from the Scarborough data. The number of extracted venues was limited to 100 and the radius for the geographical scope was set as 500 meters. This was exactly the same condition as the previous searches in Toronto and Manhattan in New York for the comparison purpose.

After request and examination of the results, the get-category-type function was borrowed from the Foursquare lab and the json was cleaned to transfer the information into a pandas data frame.
![](26.png)

### Explore Neighborhoods in Scarborough

A function was created to repeat the same process to all the neighborhoods in Scarborough. Then, a new data frame was created called “Scarborough venues” from “Scarborough data.” The size of the resulting data frame was confirmed.
![](29.png)

Next, the number of venues and categories was counted for each neighborhood. There were 59 unique categories.
![](30.png)

### Analyze Each Neighborhood

One hot encoding was used to create a new data frame. After examination of the new data frame, rows were grouped by neighborhood to find the mean of the frequency of occurrence of each category. After confirmation of the new size, each neighborhood was printed along with the top 5 most common venues. The returned data was put in a pandas data frame to sort the venues in descending order. Then, a new data frame is created to display the top 10 venues for each neighborhood.
![](38.png)

### Cluster Neighborhoods

In this project, a k-means clustering algorithm was employed. K-means is one kind of unsupervised machine learning to enable explore, segment, and group neighborhoods into clusters to find neighborhoods having similar characteristics in a big city, such as New York and Toronto. Here 5 clusters of neighborhoods were created to generate a new data frame that includes the cluster as well as the top 10 venues for each neighborhood.
![](40.png)

Next, the new data was combined with Scarborough data to add latitude/longitude for each neighborhood before the resulting clusters were visualized and the 5 clusters were examined.
![](41.png)

## 4.	Results

The visualized and examined 5 clusters were presented below.

Clusters in Scarborough
![](43.png)
Cluster 1
![](44.png)
Cluster 2
![](45.png)
Cluster 3
![](46.png)
Cluster 4
![](47.png)
Cluster 5
![](48.png)

There were 16 neighborhoods observed in Scarborough. The 16 neighborhoods were classified into 5 clusters. Cluster 2 included 12 neighborhoods. The other clusters: Cluster 1, 3, 4, and 5 only included 1 neighborhood, respectively. As compared to the West side of Toronto and Manhattan in New York, the number of found neighborhoods was much smaller. Furthermore, almost every neighborhood in Scarborough had similar characteristics and was lacking diversity.

## 5.	Discussion

Considering the results in this project about neighborhoods in Scarborough, it makes little difference for the new life which neighborhood is chosen as the new residence near the new place of work. The job seeker might not be able to find a new residence in Scarborough that provides the same lifestyle as that the person can experience in the current residence. The West side of Toronto shows more diversity. Thus, it might not be better to move to the East side of Toronto, if the person thinks much of private life. If the person owns a car, it is not indispensable for the person to move to the East side of Toronto. As a residence the West side looks more attractive than the East side. It is quite possible to commute by car between the residence and the company.

Clusters in Toronro
![](To.png)

With regard to Manhattan, one borough in New York City, has more neighborhoods as well as diversity of the neighborhoods than Scarborough. Manhattan is one of the wealthiest areas in the world. It is natural to be able to have a greatly comfortable and enjoyable life in Manhattan, although it is extremely expensive to live there. Living in Scarborough would be considerably boring for a person living in Manhattan. Thus, it also depends on the amount of salary of the person which area should be chosen as the residence. It is preferable to analyze such differences between the current residence and the new residence as well as to consider the lifestyle and economic status of the person before making a decision to move to the new place.

Custers in Manhattan
![](Ma.png)

## 6.	Conclusion

Unfortunately, it is not guaranteed that person can enjoy the same lifestyle in the East side of Toronto as that experienced in the West side of Toronto.

## Main Libraries

Folium to visualize clusters of neighborhoods in a map\
Geocoder to collect location data\
JSON to handle JSON files\
Matplotlib to plot data in a figure\
Numpy to handle data in a vectorized manner\
Pandas to create and analyze data frames\
Request to carry out http request\
Scikit Learn to import a K-means clustering algorithm\
XML to separate and to store data\