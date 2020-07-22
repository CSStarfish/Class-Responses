**A. Premade Estimators**

**1. How did you split the labels from the training set?  What was the name of the labels dataset?**

**2. List 5 different estimators from tf.estimator and include the base command as you would write it in a script (for example this script used the tf.estimator.DNNClassifier() function from the API).**

**3. What are the purposes of input functions and defining feature columns?**

**4. Describe the command classifier.train() in detail.  What is the classifier and how did you define it?  Which nested function (and how have you defined it) are you applying to the training and test detests?**

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

