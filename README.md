# Welcome to Machine Learning

## Exercise Response Index
1. [July 7, Response](https://csstarfish.github.io/Machine-Learning/July7Response)
2. [July 8, Response](https://csstarfish.github.io/Machine-Learning/July8Response)
3. [July 9, Response](https://csstarfish.github.io/Machine-Learning/July9Response)
4. [Project 1, Response](https://csstarfish.github.io/Machine-Learning/Project1Response)
5. [Extra Credit 1 (July 10), Response](https://csstarfish.github.io/Machine-Learning/ExtraCreditResponse)
6. [July 14, Response](https://csstarfish.github.io/Machine-Learning/July14Response)
7. [July 15, Response](https://csstarfish.github.io/Machine-Learning/July15Response)
8. [Project 2, T-shirt Entry Draft](https://csstarfish.github.io/Machine-Learning/Project2Response)

---


### Practice Along With Video Lecture #1 - 7/6/20
#### Working with Tensorflow

Today, I worked with Tensorflow to create a relatively "simple" neural network consisting of one neuron within one layer.  I then used this network to create a model representing the relationship between two different lists of numbers, with epochs=500.  From my understanding, "epochs" is a setting that tells the computer how many times to look through the training data to create its best "guess" for a corresponding model.  After running the code, I thought it was neat to see how the loss function kept being minimized after each epoch, as the computer got closer and closer to the best-matching model.

Once I finished working with this example, I ran a similar neural network that also consisted of one neuron within one layer.  However, this time, I used the network to create a model representing housing prices based on the number of rooms in the home.  I then used my model to predict the price of a house with 7 rooms, and it accurately output a price around $400,000 (i.e., ~$401,000).  Interestingly, although the loss values continued diminishing with each epoch, the final epoch's loss was 10x larger for the housing price model than the sample model mentioned above.

### Practice Along With Video Lecture #2 - 7/7/20
#### Working with Tensorflow To Classify Images

Today, I worked with Tensorflow to create a neural network that created a model to classify images of clothing.  In the exercise, I created graphs that displayed the accuracy of the model's predictions.  It was really cool to see how the network was so accurate at predicting clothing items, but it was also interesting to see how the model could be confident in it's classification, even when it was wrong.

### Practice Along With Video Lecture #3 - 7/8/20
#### Working with Tensorflow To Classify Text

Today, I worked with Tensorflow to create a neural network that created a model to classify the text of IMDB movie reviews as either positive or negative.  Similar to yesterday's exercise, I created graphs that displayed the accuracy of the model's predictions.  However, the graphs from today's exercises depicted both the loss and accuracy of the training and testing datasets over time, as opposed to just the final accuracy of the predictions.  It was interesting to be able to find the exact epoch at which the model became overfit to the training data, because you could examine the graphs to see where the training accuracy became greater than the validation accuracy.
