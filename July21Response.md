**A. Premade Estimators**

**1. How did you split the labels from the training set?  What was the name of the labels dataset?**

*  I split the labels from the training set by creating a variable named "train_y" to store the values returned by calling .pop() on the training set's labels column.  This column was named "Species."  In other words, I removed the species labels from the training set and stored them in another variable.

**2. List 5 different estimators from tf.estimator and include the base command as you would write it in a script (for example this script used the tf.estimator.DNNClassifier() function from the API).**

   * 1.  BaseLine Classifier - the script uses the tf.estimator.BaselineClassifier function from the API.  To instantiate this estimator for the Iris dataset, you would write classifier = tf.estimator.BaselineClassifier(n_classes=3).  You would then use input functions for training and evaluation, but not prediction.  For training, you call classifier.train on the input function used for training; for evaluation, you calculate the model's loss value by calling classifier.evaluate on the input function used for evaluating.  For prediction, you call classifier.predict on the testing set.
   
       *      baseline_classifier = tf.estimator.BaselineClassifier(n_classes=3)
      
              def input_fn_training:
                pass
              def input_fn_evaluation:
                pass
         
              baseline_classifier.train(input_fn=input_fn_training)
      
              loss_val = baseline_classifier.evaluate(input_fn=input_fn_evaluation)["loss"]
      
              prediction = baseline_classifier.predict(test_set)


   * 2.  BaseLine Estimator - the script uses the tf.estimator.BaselineEstimator function from the API.  To use this estimator for the Iris dataset, you would write estimator = tf.estimator.BaselineEstimator(head=tf.estimator.MultiLabelHead(n_classes=3)).  You would then use input functions for training and evaluation, but not prediction.  For training, you call estimator.train on the input function used for training; for evaluation, you calculate the model's loss value by calling estimator.evaluate on the input function used for evaluating.  For prediction, you call estimator.predict on the testing set.
   
       *      baseline_estimator = tf.estimator.BaselineEstimator(head=tf.estimator.MultiLabelHead(n_classes=3))
      
              def input_fn_training:
                pass
              def input_fn_evaluation:
                pass
         
              baseline_estimator.train(input_fn=input_fn_training)
      
              loss_val = baseline_estimator.evaluate(input_fn=input_fn_evaluation)["loss"]
      
              prediction = baseline_estimator.predict(test_set)


   * 3.  Linear Classifier - the script uses the tf.estimator.LinearClassifier function from the API.  To instantiate this estimator for the Iris dataset, you would write classifier = tf.estimator.LinearClassifier(feature_columns=my_feature_columns, n_classes=3).  You would then use input functions for training, evaluation, and prediction.  For training, you call classifier.train on the input function used for training; for evaluation, you calculate the model's loss value by calling classifier.evaluate on the input function used for evaluating; for prediction, you call classifier.predict on the input function used for predicting.

       *      linear_classifier = tf.estimator.LinearClassifier(feature_columns=my_feature_columns, n_classes=3)
      
              def input_fn_training:
                pass
              def input_fn_evaluation:
                pass
              def input_fn_prediction:
                pass
         
              linear_classifier.train(input_fn=input_fn_training)
      
              loss_val = linear_classifier.evaluate(input_fn=input_fn_evaluation)["loss"]
      
              prediction = linear_classifier.predict(input_fn=input_fn_prediction)


   * 4. DNN Linear Combined Classifier - the script uses the tf.estimator.DNNLinearCombinedClassifier function from the API.  To instantiate this estimator for the Iris dataset, you must first create crossed feature columns for the Estimator's linear settings and embedding feature columns for the Estimator's DNN settings. Then, you would write classifier = tf.estimator.DNNLinearCombinedClassifier(linear_feature_columns=my_feature_columns, dnn_feature_columns=my_feature_columns, dnn_hidden_units=[30, 10], n_classes=3).  
   
        You would then use input functions for training, evaluation, and prediction.  For training, you call classifier.train on the input function used for training; for evaluation, you calculate the model's loss value by calling classifier.evaluate on the input function used for evaluating; for prediction, you call classifier.predict on the input function used for predicting.
   
       *      combo_classifier = tf.estimator.DNNLinearCombinedClassifier(
                                  # wide settings
                                  linear_feature_columns=my_crossed_feature_columns,
                                  # deep settings
                                  dnn_feature_columns=my_embedding_feature_columns,
                                  dnn_hidden_units=[30, 10]m
                                  n_classes=3)
      
              def input_fn_training:
                pass
              def input_fn_evaluation:
                pass
              def input_fn_prediction:
                pass
         
              combo_classifier.train(input_fn=input_fn_training)
      
              loss_val = combo_classifier.evaluate(input_fn=input_fn_evaluation)["loss"]
      
              prediction = combo_classifier.predict(input_fn=input_fn_prediction)   
   

   * 5. Boosted Trees Classifier - the script uses the tf.estimator.BoostedTreesClassifier function from the API.  To instantiate this estimator for the Iris dataset, you would write classifier = tf.estimator.BoostedTreesClassifier(feature_columns=my_feature_columns, n_classes=3).  You would then use input functions for training, evaluation, and prediction.  For training, you call classifier.train on the input function used for training; for evaluation, you calculate the model's loss value by calling classifier.evaluate on the input function used for evaluating; for prediction, you call classifier.predict on the input function used for predicting.

      *       tree_classifier = tf.estimator.BoostedTreesClassifier(feature_columns=my_feature_columns, n_classes=3)
      
              def input_fn_training:
                pass
              def input_fn_evaluation:
                pass
              def input_fn_prediction:
                pass
         
              tree_classifier.train(input_fn=input_fn_training)
      
              loss_val = tree_classifier.evaluate(input_fn=input_fn_evaluation)["loss"]
      
              prediction = tree_classifier.predict(input_fn=input_fn_prediction)- 



**3. What are the purposes of input functions and defining feature columns?**

*   Input functions provide training, testing, and prediction data.  One input function (i.e., input_validation_set()) first does this by returning a dataset object that outputs a feature dictionary, which contains features mapped to their respective values, as well as an array of label values.  Another function (i.e., input_fn()) then places this data into a dataset, shuffles the data in the dataset during model training, and returns batches of the shuffled data for training.  This same function then gets used with a lambda when training and evaluating the model to store arguments.  During evaluation, input_fn runs just one epoch.  After this, input_fn places batches of input into a datset without labels and is again used with lambda in the prediction stage of the model.  

*   It is important to define feature columns because these objects describe the features the model should use from the input functions' features dictionary.  The features data are placed in these columns and provide the identifying characteristics of the classes, which the model uses as the basis for its classification predictions.  In the case of this program, the feature columns include the sepal length, sepal width, petal length, and petal width; each of these can be used to identify the type of iris (i.e., Setosa, Versicolor, and Virginica).  These columns represent each feature as a 32 bit, floating point integer for the model.  Depending on the Estimator selected, the feature columns will also be passed to the feature column argument when instantiating the Estimator.

**4. Describe the command classifier.train() in detail.  What is the classifier and how did you define it?  Which nested function (and how have you defined it) are you applying to the training and testing sets?**

*   The command classifier.train() is a command from the tf.estimator API that is used to train the model using the data from the nested input function.  This input function is combined with a lambda to take arguments into a function that doesn't accept arguments.  I used the DNNClassifier and defined it by creating a variable called "classifier" and providing it with an instance of the DNNClassifier.  The instance was provided with the dataset's feature columns, a dense neural network (DNN) containing 30 hidden nodes in the first layer and 10 hidden nodes in the second layer, and the specification that there are three potential classes (one for each species of Iris).  The feature columns were provided as the "feature_columns" argument, the DNN with hidden nodes was provided as the "hidden_units" argument, and the three classes were provided as the "n_classes" argument.  I have included the code for this below.  A nested input function is also used to apply the testing set to the classifer.evaluate() command.  Similar to when training the model, the input function is combined with a lambda to take arguments into a function that doesn't accept arguments.

    *     classifier = tf.estimator.DNNClassifier(
              feature_columns=my_feature_columns,
              hidden_units=[30, 10],
              n_classes=3)

**5. Redefine your classifier using the DNNLinearCombinedClassifier() as well as the LinearClassifier().  Retrain your model and compare the results using the three different estimators you instantiated.  Rank the three estimators in terms of their performance.**

*   I have included the results for the DNNLinearCombinedClassifier() and LinearClassifier() below, as well as the original results with the DNNClassifier for reference.  Based on these results, the DNNLinearCombinedClassifier and LinearClassifier both achieved the highest accuracy of approximately 0.967.  While they both share the same accuracy value, the average loss for the LinearClassifier was significantly lower than the average loss for the DNNLinearCombinedClassifier, which indicates that the LinearClassifier should be selected as the most accurate classifier for this situation.


*   **LinearClassifier Results:**
      Testing Accuracy: 0.967
      Average Loss: 0.069


*   **DNNLinearCombinedClassifier Results:**
      Testing Accuracy: 0.967
      Average Loss: 0.327

*   **DNNClassifier Results:**
      Testing Accuracy: 0.733
      Average Loss: 0.587

---
---

**B. Build a Linear Model**

**1. Using the dftrain dataset, upload an image where you used the seaborn library to produce a sns.pairplot().  Also include a histogram of age using the training set and compare it to the seaborn plot for that same feature (variable).  What interpretation can you provide of the data based on this plot?**

*   When plotting the pair plot of the dftrain dataset in the PyCharm IDE, the scale of the y-axis prevented the plot of the "parch" variable's probability density distribution from being seen.  To resolve this issue, I replotted the pair plot in Google Colaboratory.  This allowed the plot of the "parch" probability density distribution to be visible, but the necessary y-axis scaling to do so caused the datapoints on the remainder of the plots in this row to be difficult to read.  Consequently, I have attached links to both plots below so that all plots can be more easily seen (I couldn't directly include the images because GitHub couldn't render the page with file sizes this large).

    **PyCharm version:**
    
    [PyCharm Pair Plot](PyCharm_seaborn.png)
    
    
    
    **Google Colaboratory version:**
    
    [Google Colaboratory Pair Plot](Colab_seaborn.png)
    
    
*   Below, I have also attached links to the seaborn plot of the age probability density distribution and the histogram of age from the training set.

    **Seaborn Distribution (Age):**
    
    [Seaborn Plot of Age](AgePairplot.PNG)
    
    
    
    **Histogram (Age):**
    
    [Histogram of Age](AgeHist.png)
     
    
 *  I will be adding more detail about these plots shortly.

**2. What is the difference between a categorical column and a dense feature?**

*   Dense features identify the absence of a feature and provide the specific space where that feature is missing by populating the dataset with zeroes.  (I will be adding more detail about this shortly).

**3. Describe the feature columns that have been input to your LinearClassifier().  How would you assess the result from your initial output?  What is the purpose of adding a cross featured column?  Did your attempt to capture the interaction between age and gender and incorporate it into your model improve performance?  Include and interpret your predicted probabilities and ROC curve plots.**

*   I would assess the result from my output by analyzing the ROC curve plot.  (I will be adding more detail about this shortly).

