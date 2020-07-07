## Welcome to Machine Learning

# Exercise Summaries

## Practice Along With Video Lecture #1 - 7/6/20
### Working with Tensorflow

Today, I worked with Tensorflow to create a relatively "simple" neural network consisting of one neuron within one layer.  I then used this network to create a model representing the relationship between two different lists of numbers, with epochs=500.  From my understanding, "epochs" is a setting that tells the computer how many times to look through the training data to create its best "guess" for a corresponding model.  After running the code, I thought it was neat to see how the loss function kept being minimized after each epoch, as the computer got closer and closer to the best-matching model.

Once I finished working with this example, I ran a similar neural network that also consisted of one neuron within one layer.  However, this time, I used the network to create a model representing housing prices based on the number of rooms in the home.  I then used my model to predict the price of a house with 7 rooms, and it accurately output a price around $400,000 (i.e., ~$401,000).  Interestingly, although the loss values continued diminishing with each epoch, the final epoch's loss was 10x larger for the housing price model than the sample model mentioned above.

## Exercise 1 - 7/7/20
### Working With Tensorflow To Predict Housing Prices