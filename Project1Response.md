For this week's project, I implemented a social distance detector with two different videos - one taken from a bird's eye view and one taken from the horizon.  Due to the large video sizes, the videos have trouble rendering on this page, but the output corresponding to the bird's eye view is currently saved as my_output.mp4 and the output for the horizon angle is saved as my_second_output.avi in the repository.  I will be updating this page with these videos shortly.

**1. Was your social distance detector effective at detecting potential violations?**

**2. Do you think this approach would be effective for estimating new infections in real time?  How would you implement such an approach in response to the COVID-19 pandemic we are currently experiencing?**

**3. What limitations or improvements might you include in order to improve your proposed design?**


After accomplishing this task, I also decided to implement a mask detector using the image below.  The detector very confidently assessed that the man to right is not wearing a mask - in fact, it predicted with 100% confidence that there wasn't a mask on his face.  The detector was also very confident in its prediction that the man to the left is wearing a mask.  However, it was approximately 2.67% less confident in this prediction than in its prediction for the man to the right.  Perhaps this slight decrease in confidence is due to the fact that the man on the left's mask is slightly crooked and is not fully covering his nose.  Another direction to take with this face mask detector would be to adjust for different positions of the mask and to be able to detect masks on people outside of the foreground of the image.

![](mask.jpg)  ![](mask_detected.PNG)

**Do you think implementing a face mask detector could add value to a social distancing detector?**
