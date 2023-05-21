# Arrythmia Detection 

## Table Of Contents: 
* [Requirements](#Requirements)
* [Dataset Description](#Dataset_Description)
* [Methodology](#Methodology)
* [Type & Shape Of Data](#Type_&_Shape_Of_Data)
* [Steps](#Steps)
* [Results & Conclosion](#Results&Conclousion)


## Built With:
* [Python](#Python)

### Requirements:
* pip install numpy
* pip install matplotlib
* pip install pandas
* pip install sklearn
* pip install csv
* pip install seaborn
* pip install os
* pip install scipy
* pip install wfdb

### Dataset_Description:
* The MIT-BIH Arrhythmia Database has different types of arrhythmias present in the recording. The recordings were obtained from 47 patients, with one recording containing two leads. the sampling rate of 360 Hz and a resolution of 11 bits
* it is described by a text header file (.hea), a binary file (.dat) and a binary annotation file (.atr).
* The header file (.hea) is a short text file that describes the contents of the signals (including the name of signal file, number of samples, signal format, type of signal and the detailed clinical information)
* all records include a binary file (.dat) containing digitized samples of one or more signals stored in 212 format and most records include one or more annotation files (.atr).

### Methodology:
* Firstly, we read the signal from a .dat file which was a 2d array for 2 channels and we got the annotations of them from the atr file which represents the annotations of each beat also in it there's a representation for each beat as it is starting and ending where in the signal 
* Secondly, we separated this data channel alone and got the time domain and frequency domain features for each one of these channels and for each beat (we got the features for each channel and then combined them together so we can say each channel contributes with some features as both of this channel and then we saved them in a CSV file 
* Thirdly, after that, we started the preprocessing and feature selection and we found that the data had no null and all of the data was good so we went to feature selection, at first we started by finding which of these features are constant and has no variation with the output and we found that none of these features had this after that we got the heat map we got the correlation between these features and we found 15 features related to each other with a threshold of 0.9 so we decided to drop them from the main features which resulted in having 23 features, then we used LDA as dimensionality reduction technique them

### Type_&_Shape_Of_Data:
*  at first, we need the new data to represent a signal of a 2d array which would be the signal which represents the beat that we want to detect, one of them represents the first channel and the second channel for the second element of the 2d array, then we would get the features of this signal and this channel each one alone, by another meaning we would get all of signal of the first channel 
*  then getting the features of this channel and then getting the second channel in the same way as the first one and then getting the feature of it
*   the selected features we need are MIN, MAX, MEAN, RMS, VAR, PEAK, P2P, CREST FACTOR, SKEW, KURTOSIS, VAR_f, MIN2, MAX2, MEAN2, RMS2, VAR2, STD2, POWER2, PEAK2, CREST FACTOR2, SKEW2, KURTOSIS2, VAR_f2 and Then after getting these features we just need to do the LDA to the features (you can write our code part )
   
   ```
      LDA = LinearDiscriminantAnalysis(n_components=5)
      X_train_LDA = LDA.fit_transform(X_train, y_train)
   ```
 ### Steps:
 ![repo 1-1](https://github.com/Ms850446/beats-arrythmia/blob/main/bandicam%202023-05-21%2013-12-50-489.jpg)
 * we make pre processing (notice that no none values)
 * then make feature extraction using statistical feature (time domain & frequency domain)
 * then applied correlation and LDA (feature selection & reduction) 
 * finally applied cross validation and make our classification (training and testing)
 * we use some models such as Random forest, Decision tree, Support vector machine, KNN, Logistic regression
 
 ### Results&Conclousion
 * KNN & Random Forest have the best accuracy 
 * The RF, DT, and SVM have the limitation of overfitting problems in the training
 * Various existing methods such as feature extraction and machine learning methods were applied for the arrhythmia classification.
  
