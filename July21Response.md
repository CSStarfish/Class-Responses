**A. Premade Estimators**

**1. How did you split the labels from the training set?  What was the name of the labels dataset?**

*  I split the labels from the training set by creating a variable named "train_y" to store the values returned by calling .pop() on the training set's labels column.  This column was named "Species."  In other words, I removed the species labels from the training set and stored them in another variable.

**2. List 5 different estimators from tf.estimator and include the base command as you would write it in a script (for example this script used the tf.estimator.DNNClassifier() function from the API).**

*   1. BaseLine Classifier (I will be adding how it would be written in a script, shortly)

*   2. Estimator

*   3. Linear Classifier

*   4. DNN Linear Combined Classifier

*   5. Boosted Trees Classifier


**3. What are the purposes of input functions and defining feature columns?**

*   Input functions provide training, testing, and prediction data.  One input function (i.e., input_validation_set()) first does this by returning a dataset object that outputs a feature dictionary, which contains features mapped to their respective values, as well as an array of label values.  Another function (i.e., input_fn()) then places this data into a dataset, shuffles the data in the dataset during model training, and returns batches of the shuffled data for training.  This same function then gets used with a lambda when training and evaluating the model to store arguments.  During evaluation, input_fn runs just one epoch.  After this, input_fn places batches of input into a datset without labels and is again used with lambda in the prediction stage of the model.  

*   It is important to define feature columns because these objects help the model use the input from the input functions' features dictionary.  The feature data are placed in these columns and provide the identifying characteristics of the classes, which the model uses as the basis for its classification predictions.  In the case of this program, the feature columns include the sepal length, sepal width, petal length, and petal width; each of these can be used to identify the type of iris (i.e., Setosa, Versicolor, and Virginica).

**4. Describe the command classifier.train() in detail.  What is the classifier and how did you define it?  Which nested function (and how have you defined it) are you applying to the training and test detests?**

*     I defined the classifier as (I will be adding more detail about the classifier shortly)

**5. Redefine your classifier using the DNNLinearCombinedClassifier() as well as the LinearClassifier().  Retrain your model and compare the results using the three different estimators you instantiated.  Rank the three estimators in terms of their performance.**

---
---

**B. Build a Linear Model**

**1. Using the dftrain dataset, upload an image where you used the seaborn library to produce a sns.pairplot().  Also include a histogram of age using the training set and compare it to the seaborn plot for that same feature (variable).  What interpretation can you provide of the data based on this plot?**

*   When plotting the pair plot of the dftrain dataset in the PyCharm IDE, the scale of the y-axis prevented the plot of the "parch" variable's probability density distribution from being seen.  To resolve this issue, I replotted the pair plot in Google Colaboratory.  This allowed the plot of the "parch" probability density distribution to be visible, but the necessary y-axis scaling to do so caused the datapoints on the remainder of the plots in this row to be difficult to read.  Consequently, I have attached both plots below so that all plots can be more easily seen.

    **PyCharm version:**
    [PyCharm Pair Plot](PyCharm_seaborn.png)
    
    **Google Colaboratory version:**
    [Google Colaboratory Pair Plot](Colab_seaborn.png)
    
*   Below, I have attached the seaborn plot of age along with the histogram of age from the training set.

    **Seaborn Distribution (Age):**
    [Seaborn Plot of Age](AgePairplot.PNG)
    
    **Histogram (Age):**
    [Histogram of Age](AgeHist.png)
    
 *  I will be adding more detail about these plots shortly.

**2. What is the difference between a categorial column and a dense feature?**

**3. Describe the feature columns that have been input to your LinearClassifier().  How would you assess the result from your initial output?  What is the purpose of adding a cross featured column?  Did your attempt to capture the interaction between age and gender and incorporate it into your model improve performance?  Include and interpret your predicted probabilities and ROC curve plots.**

