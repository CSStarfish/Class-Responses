**A. Write a Problem Statement.  Introduce your topic, quantify its significance, and describe the problem as a process.  Identify and quantify significant obstacles to solving your problem.  Demonstrate why your topic is important, and why the obstacles associated with your topic are significant both globally as well as within the context of your selected application. Describe and analyze the complex nature of the process you are investigating, including the system, the environment, agents and networks. Describe and analyze scope, scale and hierarchy of processes and sub-processes. Describe and analyze factors that contribute to quantified obstacles.  Describe and analyze process oriented causes-effect relationships.**
*   For my final project, I would like to create a convolutional neural network (CNN) to produce a model that can read people's emotions.  First, the model would use facial recognition techniques to read the expression of a person's face in the camera.  Then, it would produce an audio and/or text output informing the user of the person's apparent emotional status.  

    This model would be useful for those who are visually-impaired, because the model could help them gauge how the person in front of them is feeling as they interact with each other.  The model could also be helpful for those on the autism spectrum who may have difficulty interpreting facial expressions and need some assistance.  After performing further research on potential applications of this model, I also discovered that this model could be useful for online education platforms.  By detecting frustration or some level of upsetness, the learning platform could alert the teacher/tutor that the student is having difficulty with the assignment and recommend that they provide the student with assistance.  Consequently, I believe this model would be significantly useful for a wide demographic of people, which could improve quality of life by promoting positive social interaction and enhancing the effectivity of education across the globe.
    
    I would first need to setup facial recognition to allow the model to detect key facial features.  Then, I would need to train the model on a set of facial expressions that portray the "seven basic emotions," which include happiness, sadness, surprise, anger, fear, disgust, and neutral.  During this process, I could vary the number of layers and potentially add dropout layers to improve the model's accuracy and prevent overfitting.  I will then add in the ability to classify the seven emotions based on video input from the webcam.
    
    Some obstacles to the accuracy of the model include the fact that, sometimes, people's facial expressions are incongruous with how they truly feel.  People often internalize their feelings and don't let them surface.  For example, people may put on appearances to look cheerful and excited, but really feel unhappy and stressed.  In addition, some people have a neutral expression that makes it difficult to determine whether they are happy or sad.  However, this concern may not prove to be much of a hindrance because the person's tone of voice can help resolve any uncertainty and validate any assumptions made based on appearances.  Another potential obstacle would be trying to detect facial expressions in suboptimal conditions, such as where lighting is insufficient.  In today's pandemic environment, these suboptimal conditions could also include people wearing face masks, which would prevent the model from using mouths in its decision-making process.

**B. Describe your implementation of the cats & dogs exercise.  How did you setup the data?**
   **1. Which optimizer have you selected, and how might it compare to other possible choices?**
    
    
   **2. Describe your selected loss function and it’s implementation.  How is it effectively penalizing bad predictions?**
    
    
   **3. What is the purpose of the metric= argument in your model.compile() function?**
   
   
   **4. Plot the accuracy and loss results for both the training and test datasets.  Include these in your response.  Assess the model and describe how good you think it performed.**
    
    
   **5. Use the model to predict 3 dog images and 3 cat images.  Upload you images and the prediction.  How did your model perform in practice?  Do you have any ideas of how to improve the model’s performance?**
