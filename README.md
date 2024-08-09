# How to run the code
The code consists of several functions, with only two main blocks. Before the training and testing blocks, run all of the function cells as well as the import cell. This will create the structure that the rest of the code will run on. In order to simply train the model, we just need to run all of the cells above the test block. In order to test a model, only that cell needs to be run. In order to change the hyperparameters of the model, the values just beed to be altered in the hyperparameter block.

# Preprocessing Methodology
The preprocessing pipeline is as follows: the two different languages are combined into a single list, separated by ‘special tokens’ that denote the start, break and end of a sentence. 

For example: for input language a b c and output language x y z, we convert it to <spl> a b c <spl> x y z <spl>

This corpus is tokenized and padded. The corpus is then separated into train_in, train_out, val_in and val_out; out of which train_in and val_in are robbed of their last element and the train_out and val_out are moved forward by one digit and one-hot vectorized. This is in order to train the model to predict the next token in the series. These datasets are compiled together into a single tensor dataset and separated into batches. 

# Model Methodology
The model chosen for this project is a transformer decoder, whose function is to take in a series of tokens and predict the next token. Towards this end, we have processed the data in such a way that the input language is staggered backwards by 1 token and the output is staggered forwards by 1 token. The model has 8 decoder and intermediate layers, with an embedding layer in the beginning to help the model process the data. Each transformer layer has 4 attention heads. The last layer is a dense layer utilizing the softmax function.  These values can be altered by simply altering the values in the hyperparameter code-block. 
# Code Outputs
Once the entire code file is run, it generates the following results in the home directory:
I. A folder called plots that contains the plots for the train/validation accuracy, train/validation loss and the variation in the learning rate of the model per epochs.
II. A folder called outputs that contains the resulting tokenizer file and the model weights file.
