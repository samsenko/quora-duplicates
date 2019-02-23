# quora-duplicates

## Summary
This repository contains code to train and utilize a neural network to predict if two questions on the website quora are duplicates. 
The model currently consists of first passing the questions through a pretrained word embedding model and then passing these embedded 
questions through a siamese neural network containing a single recurrent layer and a single dense layer. The model was trained on a 
dataset consisting of 50000 question pairs. 5000 of these were used as test data and not used in the training of the model. The best
accuracy achieved on the test data is 99.02%. 

## Files in this repository
This repository contains two Jupyter Notebooks. The one entitled quora_duplicates_embedding contains code to read the data and use the 
pretrained model to perform the word embedding and then write the results to a .npz file. The other one is entitled quora_duplicates_model
and contains code to train the model as well as code to save the model and code to utilize the model to make a prediction. Both of these
SHOULD ideally be run using Google TPU's (I have been running them using Google Colaboratory). Both of them MUST be run on a machine with
at least 10GB of RAM (8GB is insufficient to store the post-embedding training data). This repository additionally contains the original 
data (questions.csv), the data after the embedding (quora_embedded.npz) and a fully trained model (quora_duplicates_feb19.h5).

## Future improvements
Due to the model's size, it is currently very slow to load (to the point where it is almost quicker to train it again from scratch). In
the future, it would be ideal to find a way to quickly load the model so it can easily be used. Additionally, only about an 8th of the 
original data is being used due to memory restrictions. This is something which ideally would be fixed in the future.

## External Links
The data is from https://www.kaggle.com/quora/question-pairs-dataset.

Much of the code for the siamese network was copied from the following tutorial: https://towardsdatascience.com/one-shot-learning-with-siamese-networks-using-keras-17f34e75bb3d
