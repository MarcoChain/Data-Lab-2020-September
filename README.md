# CNN approach to distinguish different voices.
### Introduction
As every semester, the data-lab and process course at Politecnico of Turin start a new competition among the students to establish part of their marks. This summer, the problem is a classification task: we should develop a method to distinguish the audio of ten different speakers.  


# Files
The dataset comes from LibriVox, a website providing free public domain audiobooks. The dataset is comprised of 30,281 recordings extracted from different audiobooks. Each recording lasts approximately 0.5 seconds and is sampled at 24 kHz . The recordings are collected from a total of 10 speakers, identified by the labels a,b,c,d,e,f,g,h,i,j. Each recording is identified by a unique id, a 64-characters hexadecimal string. The development set is characterized by 24,449 recordings as WAV files compressed in a single ZIP file while the evaluation set is comprised of 5,832 WAV recordings compressed in a single ZIP file.


## Some preprocessing steps

Since I'm not an expert to analyse this kind of problems I have done only some basic preprocessing steps. I have seen that around 99.9% of the recordings have approximately 12,000 samples. So, the shortest ones were padded with 0 the longest were cut in the final part. For all the records I have also saved it in two different forms:

-   Time series
-   Fourier Transform

## The model

As already said, I am not a master for this kind of problem, so my idea to solve this problem is to develop a Cnn. Why a Cnn? Cnns are often suggested when the knowledge of the problem is not so in-depth because they can learn on their own personalized filters for that kind of task. Only a good design and a clever hyper-parameters tuning approach are required. Moreover, Cnns as Rnns are particularly powerful to analyze time series, so this approach looks immediately the right to face this problem. To implement all the algorithms I have used mainly Keras, Numpy and Scipy.
At first, I use a sequential model and I start to stack Convolutional layers with ReLU activation function and batch normalization layers followed by MaxPooling layers. Finally, I add two fully connected layers with ReLU and softmax activation function. I have also used some regularization techniques, to try to reduce overfitting, such as (spatial/gaussian) drop out, normalization, and activity regularizer.
The input of this model was the audio in the time domain before and the Fourier domain later. Using SGD with momentum as the optimizer and categorical cross-entropy as loss the result overcomes 97% in both cases.
The final idea was to implement a multi-input CNN to learn features in both domains. The structure of the network was the same as before but with two branches instead of one. The result improves but not as much as expected.

## Perfomances



|Domain               |Best Loss|Best accuracy score|
|----------------|-------------------------------|-----------------------------|
|Time|`1.40`            |`97.25%`           |
|Fourier|`1.35`            |`97.46%`             |
|Time + Fourier         |`1.20`|`97.59%` |

> **Note:** All the results are approximated.


 Written by [MarcoChain](https://www.linkedin.com/in/marcogullotto/).

