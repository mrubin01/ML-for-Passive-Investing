
The project has been subdivided into four stages

DATA GATHERING AND PREPROCESSING
* NYSE and NASDAQ stocks active over the whole period between the first quarter of 2000 and the last quarter of 2014. The other stocks have been excluded.
* Data have been transposed so to have the tickers as the indexes and it has been used a multiIndex format
* Technical data (adjusted price and volume) and fundamental data are merged
* Gaps are filled, empty or duplicated features dropped
* Scale and standardize data
* Store dataframe into dataset_full.csv (1555 stocks, 21 features, 40 quarters, 3 classes)
 

DIMENSIONALITY REDUCTION
* Use PCA to create a compressed dataframe (1555 stocks, 18 features, 3 classes), df_full_pca
* Use LDA to create a compressed dataframe (1555 stocks, 3 features, 3 classes), df_full_lda


ALGORITHM EVALUATION
* Use df_full_pca and df_full_lda
* First test cycle with cross-validation: PCA + LR, RF, MLP (without and with Label Powerset) 
* First test cycle with cross-validation: LDA + LR, RF, MLP (without and with Label Powerset) 
* Second test cycle with cross-validation: LDA + SVM, SGD, KNN, NB, DT
* Third test cycle with cross-validation: LDA + VotingClassifier(3) with (LR, RF, MLP, SVM, SGD, KNN, NB, DT)
* Third test cycle with cross-validation: LDA + GradientBoostingClassifier


DEMO
* This demo uses only the class 3 (ie. the stock price after 5 years)
* Load the data from dataset_with_classes.csv
* Create a multiindex dataframe with a balanced number of stocks (735 + 735)
* Scale and standardize the data
* Run the LDA to reduce dimensionality and separate x and the three Ys
* Run the three best algorithms (RF, SVM, KNN) and print the metrics
* Run the best ensemble method (Voting Classifier with RF, SVM, MLP) and print the metrics 
* Using the ensemble method, print the forecast and the actual output for 100 stocks as well as the increase %
