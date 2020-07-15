**A. Last week you did an exercise where you manually applied a 3x3 array as a filter to an image of two people ascending an outdoor staircase.**  

   **1. Modify the existing filter and if needed the associated weight in order to apply your new filters to the image 3 times.  Plot each result, upload them to your response, and describe how each filter transformed the existing image as it convolved through the original array and reduced the object size.  What are you functionally accomplishing as you apply the filter to your original array (see the following snippet for reference)?**  
   
***The snippet for reference is the following:** 

![Snippet 1](July14Snippet1.PNG)

*   The image below depicts the original version of two people ascending the outdoor staircase.
   ![Original](Original.png)
   
   The next image below depicts the first filter on the image.  I used filter = [ [-1, 0, -2], [0.5, 4.5, -1.5], [1.5, 2, -3]], with weight = 1 because the values in the filter add up to 1.  This filter increased the contrast of the image by brightening lighter colors and further darkening darker colors.  It also sharpened the edges, yielding a much more crisp picture of the staircase. (I will be updating this with more detail on how the image was transformed)
   ![First Filter](FirstFilter.png)
   
   I then applied a second filter to the original image, as shown below.  I used filter = [ [-0.55, 0, -3], [10, 2, -8], [2, 2, -4]], with weight = 2.22 because the values in the filter add up to 0.45.  This filter greatly increased the contrast of the image by heavily brightening lighter colors.  Consequently, the filter effectively converted the image from gray-scale to black-and-white.  Interestingly, this filter also produced wavy lines across the sky.  (I will be updating this with more detail on how the image was transformed)
   ![Second Filter](SecondFilter.png)
   
   Lastly, I applied a third filter to the image and attached it below.  This time, I used filter = [ [-5, 5, 0], [0, -2, 3], [1, -20, 25]], with weight = 0.143 because the values in the filter add up to 7.  This filtered image appears quite similar to the original image, as the third filter only slightly sharpened the picture.  The image's contrast was also increased by lightly brightening the lighter colors in the image.  In addition, the edges were sharpened, which is especially apparent in the leaves of the tree toward the bottom of the image.  (I will be updating this with more detail on how the image was transformed)
   ![Third Filter](ThirdFilter.png)

   **3. Why is the application of a convolving filter to an image useful for computer vision?**  


   **4. Stretch goal: instead of using the misc.ascent() image from scipy, can you apply three filters and weights to your own selected image?  Again describe the results.**


**B. Another useful method is pooling.**
   **1. Apply a 2x2 filter to one of your convolved images, and plot the result.**  
   
   ![Pooled Second Filter](SecondFilter_pooled.png)
   
   **2. In effect what have you accomplished by applying this filter?**  

   **3. Can you determine from the code which type of pooling filter is applied, and the method for selecting a pixel value (see the following snippet)?**  
     
![Snippet 2](July14Snippet.PNG)

   **4. Did the result increase in size or decrease?  Why would this method be useful?**


   **5. Stretch goal:  again, instead of using misc.ascent(), apply the pooling filter to one of your transformed images.**


**C. The lecture for today (Coding with Convolutional Neural Network) compared the application of our previously specified deep neural network with a newly specified convolutional neural network.  Instead of using the fashion_MNIST dataset, use the mnist dataset (the hand written letters) to train and compare your DNN and CNN output.**      

   **1. Were you able to improve your model by adding the Conv2D and MaxPooling2D layers to your neural network?  Plot the convolutions graphically, include them in your response and describe them.**

   **2. Edit the convolutions by changing the 32s to either 16 or 64 and describe what impact this had on accuracy and training time.**  

   **3. What happens if you add more convolution layers?**
