1. In Laurence Maroney’s video, What is ML, he compares traditional programming with machine learning and argues that the main difference between the two is a reorientation of the rules, data and answers. According to Maroney, what is the difference between traditional programming and machine learning?

*Traditional programming brings in rules and data that the programmer determines are necessary to produce specified answers. However, machine learning almost reverses this
process, as the programmer must have a concept of the answer they're looking for. Then, the programmer will provide the data necessary to reach this answer and the machine/computer will generate the rules necessary to reach that answer. In short, traditional programming yields answers based on rules and data, while machine learning
yields rules based on answers and data.*

2. With the first basic script that Maroney used to predict a value output from the model he estimated (he initially started with 10 that predicted ~31.
   Modify the predict function to produce the output for the value 7. Do this twice and provide both answers. Are they the same? Are they different? Why is this so?

*For the first prediction, the output was 21.99994. The loss on the final epoch (i.e., 500/500) was 1.3511e-09. For the second prediction, the output was 21.999409. The loss on the final epoch for this second prediction was 1.2854e-07. While the predictions were extremely close at approximately 30, they were still slightly different. In addition, while the losses were both extremely small, the loss was 100X larger for the second prediction. These differ because (to be completed).*

3. Using the script you produced to predict housing price, take the provided six houses and train a neural net model that estimates the relationship between them. Based on this model, which of the six homes present a good deal? Which one is the worst deal? Justify your answer.
