## Neural Network for generating names

Through this project I was able to gain a deeper understanding of how neural networks work and perform in general. We start with a dataset of 55K+ Indian names arranged alphabetically:
Here is the link to the original dataset: [Indian Names](https://www.kaggle.com/datasets/meemr5/indian-names-boys-girls)
To make the model efficient and not just follow the alphabetical pattern, I had the names shuffled, changed to lowercase and also removed the space (" "), hypen ("-") and dot (".") symbols to achieve simplicity in training.

The model layout it as follows:
Embedding : (32, 8, 24)
FlattenConsecutive : (32, 4, 48)
Linear : (32, 4, 128)
BatchNorm1d : (32, 4, 128)
Tanh : (32, 4, 128)
FlattenConsecutive : (32, 2, 256)
Linear : (32, 2, 128)
BatchNorm1d : (32, 2, 128)
Tanh : (32, 2, 128)
FlattenConsecutive : (32, 256)
Linear : (32, 128)
BatchNorm1d : (32, 128)
Tanh : (32, 128)
Linear : (32, 27)

The list of names is first converted into blocks of 8 consecutive characters, which will predict the 9th character. This results into a 505323 * 8 matrix of characters.
This will be divided into batches of 32 with each block embedded into a vector of length 24, resulting in a Embedding layer of (32, 8, 24). This is passed into subsequent layers to give the final output of (32, 27) which will contain the predicted embeddings for each block in the blocksize, on which softmax will be applied to get the next character. 
While making predictions, the algorithm will initialize a block of size 8 with all dots, and continuously shift the context window over the block to predict the next character. During prediction, the algorithm will sample continuously from the distribution of probabilities obtained from the model for each context and stop when the next character is a dot (".") to indicate the end of the name, resulting in names of varying lengths, not just 8 characters. 

