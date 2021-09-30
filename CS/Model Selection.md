- split the data into *training*, *validation* sets
	- avoids *overfitting* ; by keeping some of the data unseen during the training phase we can evaluate our model on the validation set **while we adjust the hyperparameters**
	- we can also hold some more data, the *test* set, for testing the final tuned model
- the simples metric is just to find the percentage of corrected predictions, i.e the *accuracy*

# Todo

- [ ] are there other metrics besides correctly predicted/total ?
- [ ] why shuffle the data? why K-cross validation? Isn't sampling from different parts of the data with same distribution give very similar results such that the cost of training and evaluating the model K times wouldn't be warranted?