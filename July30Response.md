**A. Using NLP to build a sarcasm classifier**
  
  **1. Pick two or three news sources and select a few news titles from their feed (about 5 is likely enough).  For example you could select CNN, Fox News, MSNBC, NPR, PBS, Al Jazeera, RT (Russia Today), Deutsche Welle, Facebook, BBC, France24, CCTV, NHK World or another source you wish you analyze.  Run your sarcasm model to predict whether the titles are interpreted as sarcastic or not.  Analyze the results and comment on the different news sources you have selected.**
  
* I decided to try out news titles from a range of political viewpoints, so I selected five titles each from MSNBC (more liberal), Fox News (more conservative), and PBS (more independent).  I then decided to try out another set of five titles from a satirical news source, The Onion, to see how accurate the model would be on titles I knew were meant to be sarcastic.   (I will be adding more detail shortly).
  
**B. Text generation with an RNN**

  **1. Use the generate_text() command at the end of the exercise to produce synthetic output from your RNN model.  Run it a second time and review the output.  How has your RNN model been able to “learn” and “remember” the shakespeare text in order to reproduce a similar output?**
  
*  Aside from using "Romeo: " as the output starter in the TensorFlow link exercise, I also used "Juliet: " and "Benvolio: " to continue with the Romeo & Juliet theme.  (I will be adding more detail shortly).
  
**C. Neural machine translation with attention**

  **1. Use the translate() command at the end of the exercise to translate three sentences from Spanish to English.  How did your translations turn out?**
  
* Coincidentally, like the example from the TensorFlow link, the first two sentences I selected were correctly translated and the last sentence was incorrect.  The first sentence I used was "Me gustan galletas," which the program correctly translated to "I like cookies."  On a similar note related to sweets, I then used "También me gustan pasteles," which was also correctly translated to "I also like cake."  Lastly, I used "Me gusta tarta, pero no tanto como pasteles."  This should have translated to something similar to "I like pie, but not as much as cake."  However, it instead was very incorrectly translated to "I like life as big meat." (I will be inserting the attention plots soon.)  
