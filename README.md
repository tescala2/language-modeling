# language-modeling
NLP project for generating text

This project goes through preprocessing datasets as well as creating
and training LSTM models to predict and generate text in pytorch

Preprocessing:
remove/replace characters as needed
create dictionary for word occurences
create dictionary to number top words by occurence (# of your choice)
use new dictionary to index words in text
split indexed words into sequences of chosen length (n)
sequences are of the form:
      x[0] = [w_1, w_2, w_3, ..., w_n]
      x[1] = [w_2, w_3, w_4, ..., w_n+1]
      x[2] = [w_3, w_4, w_5, ..., w_n+2]
      and so on...
      where w_i is an indexed word
split list of sequences into train, val, test and convert to tensors

Model:
The model takes in sequences of a given batch size:
      x[0] = [w_1, w_2, w_3, ..., w_n]
      x[1] = [w_2, w_3, w_4, ..., w_n+1]
      ...
      x[bs] = [w_1+bs, w_2+bs, w_3+bs, w_n+bs]
and labels of the form:
      y[0] = [w_2, w_3, w_4, ..., w_n+1]
      y[1] = [w_3, w_4, w_5, ..., w_n+2]
      ...
      y[bs] = [w_2+bs, w_3+bs, w_4+bs, w_n+1+bs]

These batches are fed sequentially: Embedding -> LSTM -> Linear
two optimizers are available (choose one) for training: SGD and Adagrad

