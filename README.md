# CNN approach to distinguish different voices.
### Introduction
As every semester, the data-lab and process course at Politecnico of Turin start a new competition among the students to establish part of their marks. This summer, the problem is a classification task: we should develop a method to distinguish the audio of ten different speakers.  


# Files
The dataset comes from LibriVox, a website providing free public domain audiobooks. The dataset is comprised of 30,281 recordings extracted from different audiobooks. Each recording lasts approximately 0.5 seconds and is sampled at 24 kHz . The recordings are collected from a total of 10 speakers, identified by the labels a,b,c,d,e,f,g,h,i,j. Each recording is identified by a unique id, a 64-characters hexadecimal string. The development set is characterized by 24,449 recordings as WAV files compressed in a single ZIP file while the evaluation set is comprised of 5,832 WAV recordings compressed in a single ZIP file.


## Some preprocess steps

Since I'm not an expert to analyse this kind of problems I have done only some basic preprocessing steps. I have seen that around 99.9% of the recordings have approximately 12,000 samples. So, the shortest ones were padded with 0 the longest were cut in the final part. For all the records I have also saved it in two different forms:

-   Time series
-   Fourier Transform

## The model

> **Note:** Not available now

## Perfomances



|                |Best Loss|Best accuracy score|
|----------------|-------------------------------|-----------------------------|
|Time|`1.40`            |`97.25%`           |
|Fourier|`1.35`            |`97.46%`             |
|Time + Fourier         |`1.20`|`97.59%` |

> **Note:** All the results are approximated.


