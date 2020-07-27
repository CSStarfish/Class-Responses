# Project 3

## Predicting Population Based on Aerial Photography

  For this project, I trained a dense neural network (DNN) and convolutional neural network (CNN) model to predict the population of regions shown in aerial pictures taken of Accra, the capital of Ghana. To do so, we were provided with .zip files that contained 10,000 pictures of Accra taken from an airplane, as well as a .csv file containing the population of the regions in each picture.  I decided that 10% of these should be used for model validation, so I first extracted 9,000 of the pictures into a training dataset folder and I extracted the remaining 1,000 into a testing datset folder.  Next, I sorted the files to ensure they followed the same order as the .csv file containing the corresponding population labels.  I then opened each picture in a NumPy array and stored the array as my training dataset.  The testing dataset was created in a similar manner, by sorting the files in the testing dataset folder, opening each picture in a NumPy array, and storing this array as my testing set. 
  
  I then created a NumPy array out of the population data in the .csv file, extracted the first 9,000 entries as training labels, and extracted the final 1,000 entries as testing labels.
  
  Since the full-size training and testing datasets were so large, I first created a "toy" training and testing set to determine if my first DNN model was functional.  My first toy training set contained the first 12 training pictures and my first toy testing set contained the first 8 testing pictures. Then, I extracted their respective population labels to create "toy" training and testing population sets.  I also rescaled the toy image datasets by dividing by 255.  This was an important step to take to improve the model's performance because it converts the bytes to values between 0 and 1, which makes it easier/more efficient for the computer to process and make calculations.  The "toy" training sets used across the model fittings that I discuss below all contained 1,000 pictures and the testing sets used all contained 100 pictures.  I tried to use more pictures, but my computer produced memory allocation errors and would terminate the program each time this occurred when I tried to use more pictures (I even had memory allocation errors with 1,000 pictures in the training set).
  
  After processing the data, I constructed a DNN that contained 7 layers (I may be adjusting this later).  The first layer flattened the input into a one-dimensional array and the remaining layers were dense layers.  Each of the first five dense layers used the ReLU activation function, which prevents negative neural outputs from skewing results in subsequent layers by changing negative values to zero.  These five layers began with 128 units and steadily decreased by a factor of 2.  The last layer contained one unit, as this layer was used to output the model's prediction. 
  
  The next step involved selecting a compiler, and I tested two throughout the project: one that used the Adam optimizer funtion and one that used the RMSProp optimizer with an initial learning rate of 0.001.  I started out by running the RMSProp-optimized model for the first seven model fittings, using the mean absolute error (MAE) and mean standard error (MSE) metrics.  I also used MSE as the loss value that the model sought to minimize.  To help visualize the loss values over time, I created plots of the training and testing loss values across each epoch.  I have attached the first seven plots below, as well as descriptions of each.
  
**DNN, RMS Prop Optimizer** 

![First Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/First%20Model%20Fit.png)

* For the first model fitting, I arbitrarily selected 5 epochs, 2 steps per epoch, and a batch size of 10.  The model was highly overfit, as the training loss was only approximately 359, while the testing loss was much higher at approximately 4,359.  This also didn't seem to be the best fit, as the training loss actually began increasing.  Consequently, I decided to change the batch size for the next fitting.

![Second Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Second%20Model%20Fit.png)

* In the second fitting, I kept the 5 epochs and 2 steps per epoch, but I decreased the batch size to 8.  Not only was this model still highly overfit, but the testing loss increased to approximately 5,843.  However, the training loss values more consistent across epochs, so I deduced that changing the batch size allowed this to happen.  Consequently, I decided to try increasing the batch size for the next fitting.

![Third Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Third%20Model%20Fit.png)

* For the third fitting, I again kept the 5 epochs and 2 steps per epoch, but I increased the batch size to 12.  Doing so provided, thus far, the lowest testing loss (about 4,083).  This fitting also seemed to be strong because the testing loss curve appears to be decreasing, overall.

![Fourth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Fourth%20Model%20Fit.png)

* Since increasing the batch size seemed to be a good choice, I kept the 5 epochs and 2 steps per epoch for the fourth fitting, and I also increased the batch size to 14.  Unfortunately, this increased the testing loss to over about 6,604.  I realized that a batch size of 12 was probably most optimal, so I decided to try altering the steps per epoch for the next model fitting.

![Fifth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Fifth%20Model%20Fit.png)

*  In the fifth fitting, I kept the 5 epochs and batch size of 14, but increased the steps per epoch to 5. Unfortunately, this increased the testing loss to over about 6,604.  I realized that a batch size of 12 was probably most optimal, so I decided to try altering the steps per epoch for the next model fitting.  This proved to be the most optimal model fitting out of all fittings I performed (both on the DNN and CNN), with a testing loss of about 2,457.

![Sixth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Sixth%20Model%20Fit.png)

*  Because 5 steps per epoch worked so well, I kept the 5 steps per epoch and batch size of 14, but tried increasing the number of epochs to ten. However, this lead to a lot of fluctuation in the testing and training loss, so I decided to try one more fitting.

![Sixth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Sixth%20Model%20Fit.png)

*  Since I had previously tried increasing the steps per epoch, I then decided to decrease the number of epochs to 2 and returned the batch size to its original 10, as well as the number of epochs to 5. However, this lead to a lot of fluctuation in the testing and training loss, so I decided to try one more fitting.  This led to even more fluctuation, so I stopped here and decided that the fifth fit was the best for this version of the model.


**DNN, Adam Optimizer**

![Eighth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Eighth%20Model%20Fit.png)

![Ninth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Ninth%20Model%20Fit.png)

![Tenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Tenth%20Model%20Fit.png)

   After using these compilations of the DNN model, I decided to try a CNN model so that the model could make better predictions based on the key features highlighted by the convolving and pooling layers.  The CNN contained 10 layers, with the first layer being a data preprocessing layer that rescaled the images by dividing the bytes by 255 (similar to the division performed prior to implementing the DNN model).  The next six layers consisted of pairs of Conv2D and MaxPooling2D layers (i.e., there were three Conv2D and three MaxPooling2D layers).  The first Conv2D layer contained 16 filters, which were 3x3 arrays, and the number of filters doubled in each of the next two Conv2D layers.  All three of the Conv2D layers utilized the ReLU activation function, and the first Conv2D layer set the input image size to 480x480 for consistency (the input images are already this size, but it's good practice to include this argument in the initial layer).  Each of the MaxPooling2D layers reduced the image to a quarter of its previous size.  The next layer, after these six convolutional layers, is a Flatten layer.  This "flattens" the input into a one-dimensional array before passing the data into the final two Dense layers.  The first dense layer contained 512 units and also used the ReLU activation function, while the final dense layer only contained one unit because this layer output the model's final prediction.
   
   The first nine fittings to the CNN model again used the RMS Prop optimizer (with an initial learning rate of 0.001) in the compiler.  I tried to complete ten fittings with this first compiler, but I encountered errors about difficulty with memory allocation, so I stopped at nine.  I have attached plots of the loss values for the fittings below, but none of these proved to be more effective than the fifth fitting of the DNN, so I disregarded them.  Interestingly, the fitting that yielded the lowest loss value among the CNN model fittings shared the same arguments as the fifth DNN model fitting (I have described this further under the fourth plot below).
   
**CNN, RMS Prop Optimizer**

![Eleventh Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Eleventh%20Model%20Fit.png)

![Twelfth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twelfth%20Model%20Fit.png)

![Thirteenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Thirteenth%20Model%20Fit.png)

![Fourteenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Fourteenth%20Model%20Fit.png)

*  While still having a higher loss value than the fifth fitting of the DNN, the fourth CNN fitting proved to be the most accurate of the CNN models I tested.  The loss value for this fitting was approximately 4,226.  I used 5 epochs, 5 steps per epoch, and a batch size of 14.  Interestingly, these were the same arguments provided to the fifth fitting of the DNN.  Likewise, the fifth DNN fitting also used the RMS Prop optimizer.

![Fifteenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Fifteenth%20Model%20Fit.png)

![Sixteenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Sixteenth%20Model%20Fit.png)

![Seventeenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Seventeenth%20Model%20Fit.png)

![Eighteenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Eighteenth%20Model%20Fit.png)

![Nineteenth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Nineteenth%20Model%20Fit.png)

   
   I was able to complete ten fittings to the CNN model when I used the Adam optimizer (with the default initial learning rate of 0.01) in the compiler.  I have attached plots of the fittings' respective loss values below, but these again proved to be less effective than the fifth fitting of the DNN, so I disregarded them.
   
**CNN, Adam Optimizer**

![Twentieth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twentieth%20Model%20Fit.png)

![Twenty-First Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-First%20Model%20Fit.png)

![Twenty-Second Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Second%20Model%20Fit.png)

![Twenty-Third Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Third%20Model%20FIt.png)

![Twenty-Fourth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Fourth%20Model%20Fit.png)

![Twenty-Fifth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Fifth%20Model.png)

![Twenty-Sixth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Sixth%20Model%20Fit.png)

![Twenty-Seventh Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Seventh%20Mode%20Fit.png)

![Twenty-Eighth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Eighth%20Model%20Fit.png)

![Twenty-Ninth Fit](https://github.com/CSStarfish/Machine-Learning/blob/master/Project%203%20Plots/Twenty-Ninth%20Model%20Fit.png)
   
   
   Interestingly, the lowest MSE loss value on the testing set occurred with the DNN model.  Considering the input dataset consisted of images, I had assumed the CNN model would prove to be the most accurate model.  The lowest MSE loss for the DNN occurred with the fifth fitting (using the RMS Prop-optimized compiler), which yielded a loss of approximately 2,457.  On the other hand, the lowest MSE loss for the CNN occurred with the fourth fitting (also using the RMS Prop-optimized compiler), which yielded a loss of approximately 4,226.  Overall, the DNN and CNN model seemed to be pretty consistent with each other in their predictive power.
