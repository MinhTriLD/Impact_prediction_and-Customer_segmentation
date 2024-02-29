# FASHION BOUTIQUE CHAIN
# - How web traffic impacts on business performance?
# - Customer segmentation

## I. Abstract:
A Company has been operated it's business as a fashion boutique chain since the March of 2019. They are possessing stores in each country’s capital: UK (London); FR (Paris); IT (Milan); GER (Berlin). Since the end of 2019, to enhance the business performance, BoDs have intend to invest in applying technical solutions such as website and big data into their business.

This company kicked off a website at the beginning of 2020. This is an experiment for the marketing promotion, thus, they just fund a static web with a few simple functiom for only the display of the boutiques information, product detail, pictures and purchasing contact. The website has not been combined the functions to process the data input by web users to determine web user and collect vital data. This web just has able to count distinct user ('users'), page view ('pageviews') and unique page view based on loading within a certain duration ('uniquePageviews') for each web page of each product.

To make decision for investing the web upgraded to dynamic functions matching for the E-commerce, the board of management requested a coverage of the website traffic's impact on business performance. Another request is to determine personal group of current customers.

The material is supplied to complete this mission, includes the documents in type of Excel file (.xlsx), which record the traffic of each each 2020's month and a compound file containing sheets where data of customers, items and transactions.

Some feature has been encoded or changed to conceal the identification.

Request 1: How web traffic impacts on business performance?
Request 2: Customer segmentation.
## II. Introduction:
This paper provides a full procedure of a data analysis project from 'init' to 'predict' with the great emphasis on business accumen for satisfying the request assigned. Over and above, the result of this project gives the acknowledge about how website application impact on business performance and the classification of customers to establish the business strategic plans. Noticably, this report should be implemented periodically to measure the performance and keep the figures been upto date.

The assigned requests is too general to determine the features which need to be measured and considered for the report output. By the knowledge about business management and digital marketing, I am able to affirm which features relevant to fators and consequence in the question. Below is the discussion and predict identical variables.

Request 1: How web traffic impacts on business performance?

Features relevant to web traffic are the count of users, page view which is the number of times a web page is loaded, unique page view which is the number of unique times a web page loaded within a specific time period, and existing duration.

Business performance is too general,because it includes the whole business's aspects. Business performance would be specified sales performance due to digital marketing only being able to impact on the sale of business. Therefore, it is certainly expressed by the indicators of revenue, avg revenue per unit, sales volume, customer volume, vonversiom rate, etc.

These variables are numerical and datetime, which used respectively to express quantity and timestamp.

Request 2: Customer segmentation:

In addition to segmenting customers by the categorical variables provided in the original dataset such as geography, gender, etc., customer segmentation can also be grouped by numerical and time data. For example, independent variables for grouping are age, relationship time, spending turnover, and some other models like RFM, etc.

The tools that facilitate this analysis are libraries supported by Python and Machine Learning models.

Flow chart:

Determine the contextual situation and understand the requests ---> Determine detail of independent and dependent variable ---> Select sufficient tools ---> Overview data and determine incorrect and feature for conversion or optimization ---> Process and feature data ---> Analyze exploratorily data (EDA) ---> Select feature and model ---> Train model ---> Evaluate model ---> Discuss analysis results and Conclude.

## <b><u>III. Dataset overview:</u></b>

![Data structure](https://i.imgur.com/Rx0tNx0.png)

The Entity Ralationship Diagram (ERD) of the material dataset is conducive to regcognize the relationship among tables or entities was expressed obviously as well as the feature detail in each table. 

Currently, the dataset has possessed three dim tables showing the figures of three entities, include items, customers and web traffic. Additionally, the dataset has had one fact table which contains the real-time historical events relevant to the success transactions with customers. It is a striking feature that the dim table of web traffic could be integrated into products table, meanwhile the fact table, transaction, could be split into 2 tables being the dim table order and the fact table transaction by the key being order ID with the relationship respectively being one-to-many. Below is the references of entity relationship in this dataset:

* Ref: traffic.product - item.Product // one-to-one

* Ref: customer.ID < transaction.CustomerID // one-to-many

* Ref: item.ItemID < transaction.ItemID // one-to-many

The description of feature names is not too intensive to conceive the definition of them. However, there is some technical feature which need the explaination in this dataset, are page URL, users, pageviews and unique pageviews, below is their dictionary:

* Page URL ('Page_URL') is the link leading to the product's web page.
* Users ('users') is the number of distinct viewers accessing the page URL.
* Page views ('pageviews') is the count of the web page's loading.
* Unique page views ('uniquePageviews') is the count of the access in the page URL by an user in a specific period.

#### To determine the existing issues in the material dataset to establish the strategy of data processing, a statistical table which gives information about the number of the common issues in each feature, was created below. Additionally, the detail of features is also expressed. Moreover, it is no doubt that the value samples in each feature should be also observed to reacg the insight.

By observing the values sample, the coversion could be applied for the correct feature. The gained insight includes:

1. Firstname and lastname are stored in customer can be concatenated to full name.
2. 'Birthday' and 'DateJoined' of customers with the'Posted On (DD/MM/YYYY)' of traffic are date categorical feature, are not time series, and could be converted to time duration, which is numerical type, and simplifies the measurement.
3. The dim table 'traffic' is able to to connect with the dim table 'products' by the fourth string of each 'Page_URL' value split by '/', which is equal to each product's encoded name. Moreover, the number of distinct values in 'traffic' is also equal to the figures in products. In conclusion, each instance in 'traffic' is matching with that in 'products'.
4. The identificational features of the customers and the products has been encoded to protect customer security and trade secret.
This table is conducive to penetrating dataset and intending to process data by combining the description of columns. The findings are obtained, include:
        <ol>
            <li>The numeric indicators of web traffic are the count, which are 'uniquePageviews','pageviews' and 'users', would be set the form of positive integer.
            </li>
            <li>The 'transactions' dataset is the fact dateset which store the transactional information with the customers of the store.
            </li>
            <li>There are three columns which own binary values (0 and 1), are respectively 'Gender','Newsleett','Channel'. 
            </li>
            <li>There is not any duplicated row.
            </li>
            <li>The unique keys of each dataset are not duplicated.
            </li>
            <li>There are 251 missing values in 'Gender' of 'cust' dataset taking a large portion of this dataset. This has been a sensitive personal information in the current time. So they will be replaced by 'bisexual'.
            </li>  
        
With the above judgements about the dataset, the following will be implemented respectively to solve the issues for earning the useful dataset.

## <b><u>IV. Data preprocessing:</u></b>
### 1. <b><u>Convert data:</u>   
### <b><u> FirstName and LastName:</u></b> convert to 'FullName'.
### <b><u>'Birthday', 'DateJoined' and 'Posted On (DD/MM/YYYY)':</u></b> convert to integer.
### <b><u>'Page_URL':</u></b> convert to product.
### <b><u>'uniquePageviews', 'pageviews' and 'users':</u></b> convert to integer.
### 2. <b><u>Process missing values:</u></b>
## <b><u>V. Exploratory Data Analysis (EDA):</u></b>
​
EDA in this project will be executed by data visualization - charts, which are depended on data type, and serves materially the observation 
of numerous instance by two or more dimensions for gaining their correlation. It assist effectively  to inspect smoothly the direction of each feature by others. 
​
The analysis will be initiated by observing the data distribution which intents on the sight of the standard deviation, the percentile and the outline  of the values in each feature for attaining the data dispersion to  evaluate the sufficiency of each feature. The following is the correlation between the features and the research objects for figuring out the proper fearures vitally of the predicted models. 
​
It is a striking feature that EDA should be implemented by the fact tables to determine the elements of frequency, recency, quantity, quality, trendy and etc. In addition, the features with the same data type could be transformed to the same graph. The project's data set has three data types.
​
However, in terms of the design and function of this dataset, it's fact table is the transaction table which express the information of a sold item. This data could be ranked ordinally.
​
it assists identify the vital feature affect to research object.
​
​
Object1 : Customer volum (y1)
Object2 : Product sales volume (y2)

## <b><u>1. Data distribution</u></b>
### A. <b><u>Datetime feature:</u></b>

This dataset has four columns data, include 'TransactionDate','DateJoined','Posted On (DD/MM/YYYY)' and 'Birthday'.

However, These columns are used to store the categorical value of the objects. 

They record the date that instances of the object added to itself. Particularly, they help determining the existing time duration of object sufficiently.

* 'TransactionDate' give information about the timestampt when each transaction on a product item was done. It records events in the time series

* 'DateJoined' give information about the timestampt when customers perform the first purchasing order. by each customer.

* 'Birthday' give information about the timestampt when customers begin breathing.

* 'Posted On (DD/MM/YYYY)' show the date when each web page of  each product is published by the website of the store. 

#### <b><u>Transaction date</u></b>
This scatter expresses that the business activity of the store had maintained sustainability during the period of 2020. 

The main reason is that during the period of 2020, the data is distributed stationary commonly inside a cluster from above 60 unit to under 90 units with min and max respectively just under 50 and 110 units. There are some timestamp when the sale witnessed the breakthrough indicators of the business operation. However, most points have the mean and the extent of variance and covariance be remained less the difference during this period. 

In conclusion, the datatime feature is stationary, it means the models could be established easier with high accuracy follow this feature.
#### <b><u>Date joined</u></b>
This chart shows the number of the sold items that customers with the same date joined paying for. During this time series, the data distribution had less the varied. Because, the instances had been scateered followed a inline gap with a split duration, and existed a few outliners during the period.

The mean, variance and covariance of each instances are too different to build a good model easily. This should not be used as a time series feature. 
#### <b><u>Birthday</u></b>
This is the date which provides the persoanal information, it is used to group individual object by their age - a demographic object.

In addition, during the period of 2020, the data is distributed stationary commonly inside a cluster from 1 unit to just above 60 units with min and max respectively at 1 and 90 units. There are some timestamp when  the number of values witnessed the breakthrough customer feature. However, most points have the mean and the extent of variance and covariance be remained less the difference during this period.

In conclusion, the datatime feature is stationary, it means the models could be established easier with high accuracy follow this feature.
#### <b><u>Posted On (DD/MM/YYYY)</u></b>
During the period of 2020, the data is distributed stationary commonly inside a cluster from 1 unit to 5 units with max at 9 units. There are some timestamp when the number of values witnessed the breakthrough of web page. However, most points have the mean and the extent of variance and covariance be remained less the difference during this period.

In conclusion, the datatime feature is stationary, it means the models could be established easier with high accuracy follow this feature.

These charts show that the products were posted on the store's website, have tend to be sold more than others and also have caught more customers and orders than the others.
During the period of 2020, the data is distributed stationary commonly inside a cluster from 1 unit to 5 units with max at 9 units. There are some timestamp when the number of values witnessed the breakthrough of web page. However, most points have the mean and the extent of variance and covariance be remained less the difference during this period.

In conclusion, the datatime feature is stationary, it means the models could be established easier with high accuracy follow this feature.

These charts show that the products were posted on the store's website, have tend to be sold more than others and also have caught more customers and orders than the others.
These histograms count the quantity of instances and in the categorical features and express the data distribution in each feature.

The data distribution of categorical in this dataset has not the striking variation. Exception is the feature 'Country', which is a geographic description, and contains the obvious differences between the values. It means excepting 'Country' feature, the others could be used to divide the dataset for mitigating the noise more readily than 'Country'.
These above charts show the number of customers who performed shopping by two means and with or without the suggestion. It poited out the number of sold items will be higher if the customers receive the newsletter of the update. There are no evident to determine the receiving newsletter will lead to shopping online. Because the number of customers who bought products online by newsletter, take just above 50% customers (6.778 customers). However, website assisted the online shopping immediately for approx 50% customers received newsletter. And another half of shopping online for the ones no received newsletter expectedly. Noticeably, the whole transaction of the offline shopping is just minimally above that of the online shopping (respectively 12.644 customers and 12.569 customers).  

### <b><u>Revenue</u></b>
### <b><u>Item sales volume</u></b>
### <b><u>Customer volume</u></b>
### C. <b><u>Numerical feature</u></b>
Regarding the data distribution, the findings were collude by these above graphs, include:

1. There are three out of eight numerical feature which has been skewed nearly total to the left due to the numerous long upper wick, are 'uniquePaperviews','Paperviews', and 'Users' features illustrating the web traffic object. It means the majority of data cluster at the cap, but the minority scattered at the very higher volume. Notably, these three features share the same distribution pattern and illustrate the "web traffic" object.
2. The relationship duration illustrate the object has been also skewed totally to the left, but the majority distributed during large extent under the middle with many upper outliners and poor lower outliners. The others have the moderately equal distribution for each part numerical value serie.


In terms of the correlation between each pair feature collaborated, these graphs show that there correlational impact between each feature with the others. The findings were concluded by these above graphs, include:

1. The numerical features which illustrates the 'customer' object, divide data at the others by obvious constraint. They express no trendy, the ambiguous interaction, reversely, the classification is expressed clearly. In addition, they also express the almost non-correlation with others. A similar pattern was witnessed in the numerical features of 'Product' object.

2. The numerical features of 'web traffic' witnessed a small variation. Their values show a stronger correlational impact between it and the other objects.

## <b><u>VI. Feature selecting & Modeling</u></b>
### 1. <b><u>How web traffic impacts on business performance? </u></b>
To deal with this request, firstly, we have to determine the proper features illustrate obviously the material and consequent objects, which will be used to model the correlational impact.
​
In this request, the matter is 'web traffic' object and the outcome is the number of issue being relevant to transaction. The detai is below:
​
* Material features : x = 'uniquePageviews', 'existing_duration' and 'users'.
​
* Outcome features: y = 'item_sales_volume', 'customer_conversion_rate' and 'customer_volime'.
​
**Note:** The material features are all features of 'traffic' object. However, the consequent features are the new feature are depended on their value and the value united by material feature of the fact table. Moreover, there are many features which describe one object, would be use intermittently to evaluate sales performance, but are depended meticulously on each other. Thus, this project just focus on features that are the least depended to reduce complex and optimize performance, are 'item_sales_volume', 'customer_conversion_rate' and 'relationship duration'. A similar pattern was applied for material features, the choices are 'uniquePageviews', 'existing_duration', 'Posted On (DD/MM/YYYY)','Channel','Newsletter'.
​
**Method:** Visualization the correlation between each depended feature with each the independed one.
​
#### A. **Users:**
* **<b><u>Item sales volume**
This chart points out am ambigious interaction between the number of product's sold items and webpage's users. 

However, all items are on stock of the company, were sold at least once time. The products approached upper 40.000 webpage's users, frequently, reach more than one transaction. 

Maybe, this is the effort of company to deal with the inventory.
* **<b><u>Customer conversion rate:**
