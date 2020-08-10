# A Machine Learning Perspective 
Lets first begin by understanding the Machine Learning Perspective on Geology data and how can it help us to predict mineral deposits.

> Note - You can skip to the next page if you already are familiar with the problem statement. Though, we recommend you to ready this through as well. 

## Why Machine Learning ?
We first need to understand why we need Machine Learning for this task in the first place. 

Traditional Algorithms that run on big data are hard coded to find certain patterns or anomolies to predict an event. 

Let's take an existing example -
![](https://www.geologyforinvestors.com/wp-content/uploads/GravitySurveys.jpg)

If you want to use the Gravity Method to find Mineralization. Through hard-coded algorithms, you would have to manually specify anomalies or/and add filters to check irregularizations. 

> Note - You can read about terminologies & other words explained simply [here]()

Also, you would need to have an extremely strong background in Geology so as to create a algorithm to encode everthing. And even still, encapsulating more than one geophysical method would be extremely cumbersome.

### Don't worry, Machine Learning is here to Rescue!

![https://cdn.analyticsvidhya.com/wp-content/uploads/2020/02/meme1.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2020/02/meme1.png)

With Machine Learning, you don't have to explicitly write rules for anomalies and patterns, but rather allow the Computer to figure it by itself by training on a lot of examples.

![https://www.kdnuggets.com/wp-content/uploads/trad-vs-ml-prog-paradigm.jpg](https://www.kdnuggets.com/wp-content/uploads/trad-vs-ml-prog-paradigm.jpg)

Coming back to the example of Gravity, *if we use Machine Learning*, we would only have to give the machine learning model these two things ->
- Gravity data of a few thousand points (the more the merrier) &
-  The features at those points which we want to learn such as *'if there a heavy mineral or not?'*

The model will automatically find all the underlying relations between the data and the features and there you have your program to find **ALL THE GOLD IN THE WORLD!**

![](https://media.giphy.com/media/xThta8UkUaoqJoJQC4/giphy.gif)

Now that we know why we need to use Machine Learning, let's take a glance at our solution.

## An overview of our solution
We tried to create 3 different models stacked over each other to predict mineralization in different regions of Gawler. 

### 1. Model 1 - "Wh're Art Thee Min'ral?"
Our 1'st model **"Wh're Art Thee Min'ral"**  tries to perform a naive, though a very crucial task, of simply predicting if, given the Geophysical features (such as Gravity, Elevation) of a pair of `Latitude`, `Longitude`, *is there a Mineral of Not?*

> Note - In the next chapter, I'll be thoroughly explaing the data used including Geophysical features. So don't worry if you are having trouble understanding these terms.

> TODO: Add the folium pics of mineralization (yes/no)

This is a binary classification problem and we trained [h2o's AutoML Algorithm](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/automl.html) to attain a whopping *AUC of  **~0.99*** & an *accuracy of **~96 %*** on testing data. (You can find everything about it here.)

> Note - To obtain insight about what AUC & other metrics are, you can check out this amazing tutorial [here](https://heartbeat.fritz.ai/evaluation-metrics-for-machine-learning-models-d42138496366).

### 2. Model 2 - "Bid Me Thy Nameth!" 

The second model **"Bid Me Thy Nameth"** is trained to find out about which mineral/metal is present at the location for which the geophysical data is fed.

This is a multi-class problem and so we needed a more powerful tool for the same. And after trying tons of state-of-the-art solutions including `Sklearn`, `Keras`, `Pytorch`, `Autokeras`, `MLBox`, the best results were obtained using [h2o's Driverless AI](https://www.h2o.ai/products/h2o-driverless-ai/) *(p.s - No coding necessary here!)*

> Note - H2o's Driverless AI is a licensed product though you can obtain a month's trial for this purpose!

> ToDo - Include the Conf Matrix here.

The model had an AUC of ___ & an accuracy of around __ !

### Model 3 - "How Big Are You?"

The third and final model **"How Big Are You?"** is created to find out about how big is the size of deposit. Its a multiclass problem as it classifies mineral deposits into either `low`, `med`, `high` or `very high` on the basis of an estimate of its amount in ppm.

> ToDO - Add a folium map with diff sizes of mineral deposits. 

This was also trained using **H2o's Driverless AI** and had an outstand _____.

### Combing all the models

If we combine the results of all the three models, we can very easily find out that given a location and its GeoPhysical features ->

- *Is there Any Mineralization?* (`Yes/No`)
- *Which is the predicted Mineral Deposit?* (`N Classes`)
- *How much is the predicted amount?* (`Low/Med/High/Very High`)

![](https://media.giphy.com/media/cJGUysXcCcyN9sJGDg/giphy.gif)


Alright, that's a lot to take in. Let's take a break and meet again at the next chapter.

