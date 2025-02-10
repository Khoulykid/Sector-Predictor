# Sector Predictor

##### Special thanks for Ahmed Elbarbary for aiding in this project with his contrubitions and finding the dataset.

## Details

This project aims to predict the sector in the dataset https://www.kaggle.com/datasets/ravindrasinghrana/job-description-dataset using basic knowledge models of machine learning from sklearn and tensorflow.

Without getting too much into the info, let's start with the project.

## Cleaning The Data

### First: Understanding

First, I had to filter through the dataset and understand the significant with every column, using the data wrangler extension it was not that difficult

### Second: Seperating Columns

Some columns were joined into one column, such as the last column which actually had my target label and other columns such as Benefit, so I had to seperate them using regex.

######

I had to then seperate every number column, since they had they were mostly ranges of numbers such as experience or salary. When I tried to check the date of posting, it was irrelevant and its scalabity was small so I did not use it, especially in the job posting.

### Third: Preprocessing

First, I had to remove some columns that did not enough unique values and columns that were directly corresponding to the label. Then, I had to standarlize using standard scaling from sklearn for the number columns, then I encoded all my label columns using one hot encoding so their numbers do not affect the weight calculation in the model, as well as being able to use these information as numbers for correlation matricies and models.

######

After that, I created a correlation matrix and compared all the numbers with the label and removed any column which had a correlation of an absolute value of 0.7 (there were none). Directly after that, as an attempt to save some memory for the RAM I converted all columns to smaller sizes of their format.

######

Finally, I preprocessed the text columns by first removing all stop words and then lemmetizing instead of stemming as in my opinion they did a better job at simpling down text. Then used Word2Vec for embedding them and then flattened the text. I did not use a huge embedding size nor TFIDF for memory issues as this was done on my personal computer.

### Fourth: Building the Model

I split the data first because of the issue of my PC's RAM. I then split the training data accordingly for cross-validation and built it depending on the accuracy.

######

In the course, We already tried all the other models using a stronger computer, and we ended up with the conclusion that neural network would be the best practice.

######

I built a Neural Network model using tensorflow. I made it so that it has two hidden layers with dropout to reduce complexity of the model. I used random search to search for the best hyper parameters possible for only 20 trials, and then finally build it

### Fifth: Limitations

The dataset was incredibly huge especially after preprocessing, so part of the problem was the limited resources. Therefore, I had to cut down on the dataset and not produce a reliable product. Because of this, I did not intend for this project to be used in any other way than just educational, that is why the one hot encoder is not properly saved. Nevertheless, it is noticeable that before producing a project like this, we should preprocess the data THEN encode it for users' input.
