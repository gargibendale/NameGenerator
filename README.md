## Neural Network for generating names

Through this project I was able to gain a deeper understanding of how neural networks work and perform in general. We start with a dataset of 55K+ Indian names arranged alphabetically:

Here is the link to the original dataset: [Indian Names (Kaggle)](https://www.kaggle.com/datasets/meemr5/indian-names-boys-girls)

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


### Results:

![Screenshot 2024-10-29 121954](https://github.com/user-attachments/assets/7d5373f4-1eee-40a7-92cf-9ffa0edd58fa)

