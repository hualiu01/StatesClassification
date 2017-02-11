# classification of PLC instruction

## Description
* This program extracted frquency features of input data(EM emission of PLC's running Instruction loop. The five classes of them are stored in `./data/[JMP,LN,SIN,SQI,XPY]`), by slidingwindow and DFT/pwelch. 
* And, after applying pca to the data features, it used machine learning algorithm to train a model (stored in stored in `./tmp/classifier_windowed.mat`)
* It calculated the confusion matrix(stored in `./tmp/confusionMatrixTest.mat`) after a certain number of trails.
* And it predicts realtime testing data (stored in `./data/testCases`) classes against time.
* After getting the raw realtime states swithing data serial A[n], it applied a sliding window to compare the statistical attributes of A[n], i.e. distribution histogram, against the training data and deside whether there is an abnormal state, i.e. `Euclidean Distance` is big. 

## Run in matlab R2016b
1. trail to compute confusion matrx
> runExperiments_
2. predict realtime state transition
> stateDetection

- Output figure 1 is the raw prediction (comming right out of classifier), in forms of `<class index>` against `time`.

- Output figure 2 is the Distribution within sliding window(represented as classes instances count) against time.

- output figure 3 is the abnormal states detection result. When the Euclidean Distance from template is large, we found an abnormal state.
