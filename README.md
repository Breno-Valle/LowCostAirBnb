# LowCostAirbnb

                                              "LOWCOST SOUTH AMERICA DREAMS"

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

If you are getting trouble to acess this notebook on github, try here: https://nbviewer.jupyter.org/

All you need to do is copy/paste the notebook URL on it.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1-IDEA OF THE PROJECT

This project is product of a Data Analysis and Machine Learning models with a very unique purpose: Help an imaginary travel agency ("Lowcost South America Dreams") to plan low cost travels to South America, in this cases, to Brazil, for thier clients. As part of that work we need to analyze some AirBnb locations in Rio de Janeiro and find the best possible places in city to indicate to the clients.

Our main objetives here are:

    -Find an avarege profile of the best possible places to find that is cheap and also with high quality (it means: great review scores)

    -Create a Machine Learning model who could predict if a new places, with no (or few) reviews, could be a good location for the clients, if its enjoyable, and if it's worth it..
 
 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
 2-ABOUT THE DATASETS
 
 Our Dataset comes directly from AirBnb site and can be founded here: http://data.insideairbnb.com/brazil/rj/rio-de-janeiro/2020-10-25/data/listings.csv.gz
 
 This Dataset is a real data come from the AirBnb open Databank. That means is a real world dataset, with a lot of missing values, strange data types and hard to handle features. Because of this, this datset was one of the best sources that i have founded to pratice Data Cleaning and Data Engineering
 
 About the shape of the dataset:

    -Number of Columns: 74

    -Number of Rows: 24030

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 3-ABOUT THE PROJECT
 
 What is going to be our steps on this project? 
  
    -Exploratory Data Analysis
   
    -Report Rio de Janeiro 
    
    -Prepair Data to Machine Learning
    
    -Training the model
    
    -Hyperparameter Tuning
    
Take a look in what are you going to find here:

- Exploratory Data analysis:

A a first step of this project i focous on understand the main features and specificities of that Dataset.   My main goals at this point were:
  
  > Deal with different Data Types: Data transformation and Data Type Selection  shinies here
  
  > Missing values: Choosing wich data to input, drop columns or lines
  
  > Find possible outliers: cutting data who are unrealistic based in statistics and business background 
  
  > Understanding features importance: Creating new features, finding new metrics and organizating next steps
  
  
A additional step that cross all these pipeline is a simple Data Cleaning work. this process is relevant to create a clean dataset for our analysis. However a depp data processing and data cleaning will be done in nexts sections.

- Report Rio de Janeiro

Here i used the cleaned data from the last section to analyse the main questions asked for the client: "What are the best possible profile to be rented using our business model?". To be able to do that I used a previously created feature that is a relationship between review score rating and price of each apartment for rent (Review Score % Price). That is a good metric to track wich location have a good Price and Quality Tradeoff. Higher values means better locations, and Low values have worst locations. 

Main discoveries: Locatons near to the beach have usually lower values, that means these locations tend to have higher prices but lower reviews, and are prone to be a frustrating experience to the clients. In the other hand, places near to the forest and mmountains, far from the beach, have hear scores, bringing more satisfaction to the clients. However, they are usually far from the main attractions in the city. More reserch wth "best price-review_score tradeoff and distance from the see, with tarvel cost could be a great job in the future. Take a look on these places in the map and the best average profile founded in the city:

Ploting the best location in the city:
  ![rio_benefit_cost](https://user-images.githubusercontent.com/80376071/113203626-a5ace380-9242-11eb-8625-a40d9ae5d86c.PNG)

Best profile founded on that dataset

![image](https://user-images.githubusercontent.com/80376071/113218456-ee21cc80-9255-11eb-9a68-01b2d1d0351a.png)

(Inside of the notebook you can find the list of the 100 best locations to be rented)


- Prepair Data to Machine Learning

At this point I splited the DAtaset into two sections, the Train and the Test section, needed to create and evaluate a model.

AS this dataset were extract from the AirBnb databank, a lot of Data Cleaning were requeired. This was one of the most exceting and hard parts of this project. Here it is what have i done on this section and some code examples:

> Data Cleaning: 

![image](https://user-images.githubusercontent.com/80376071/120335999-53328680-c2c8-11eb-8fa6-964147299aff.png)

> Deal with categorical Features:

![image](https://user-images.githubusercontent.com/80376071/120336395-aefd0f80-c2c8-11eb-93cf-8f9c6c39a424.png)


> Encoding data with Label encoder and OneHotEncoder:

![image](https://user-images.githubusercontent.com/80376071/120336655-ef5c8d80-c2c8-11eb-8703-1594db4d0f3f.png)

(Scaling will be done in a later section for the sake of the pipeline)

- Training and evaluating the mdodel:

This sections is used to build an regression Machine Learing model that could predict the ratio of Review_score/Price of new rentable locations. To be able to do that I trained three main models, the First one was a Linear Regression, the second was DecrionTreeRegressor and the last one was RandomForesRegressor. The sucess metric used is the Root Mean Square Error, mainly because i prefere to penalize the extreme errors, beacause that would impact directly in the client satisfaction in case of renting a high price apartment with a really bad experience, who could decrease the clients retention in the service. 

> The Linear regression, even using scaling and encoded data, was the one with the most poor results comparing with the two following models, as you can see in this figure:

![image](https://user-images.githubusercontent.com/80376071/120338327-8413bb00-c2ca-11eb-9c46-b58b9ce4a270.png)

> As expected, the DecionTree model made some good results with a non-scaled and hot encoded dataset:

![image](https://user-images.githubusercontent.com/80376071/120339961-f2a54880-c2cb-11eb-9a68-f1de5490e6bf.png)

> The RandomForest did a even better results, but just took a very long time to run:

![image](https://user-images.githubusercontent.com/80376071/120340143-1ec0c980-c2cc-11eb-9421-afcc29f13366.png)

- Hyperparametter tuning

In this final Section i did some hyperparameter tuning with GridSearch in the DecisionTree and the Randomforest models. Here is an example:

![image](https://user-images.githubusercontent.com/80376071/120340515-7bbc7f80-c2cc-11eb-8dc3-d7e75f14e673.png)

AS you can see inside the notebook, the DecisionTree and the RandomForest methods did a very good job in that dataset, getting a pretty siimilar results. With this i prefered to use the DecsionTree model to be used as the mfuture deploy model to the client. It has a smaller running time, requering less computaion and being easier to maintain in the future.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

4- FINAL THOUGHTS:

This project were one of the most challenging projects that i've done, due to the structure of the data and this maiin golas that i proposed. Because of this i pushed my self hard to achieve th best results that i could find. This Dataset it's cretainly one of the bests cases to do some Data Cleaning and Data Engineering, i recomend to every one use this dataset for data science and data analysis. The machine learing section was the hardest part for be, finding the best parameter and transforming the dataset, but also taught my a lot. A lot can be done with this data in the future. If you have anything to add, contact me: breno_valle@outlook.com 






 
 


