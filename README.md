
## Train
Trains CNN + LSTM hybrid model with BERT embeddings.
> python Train/train_words_dl_model.py -a 1 -w 1 -p "/homedtic/hkavas/SemEval" 

## Get Tweets
Obtains tweets for given username and timespan. This command runs periodically in our NiFi implementation.
> python Exporter.py --username "cnn" --since 2020-09-01 --until 2020-09-15

## Scrape Full Article
Checks news tweets whose author name has not been entered, uses link from database to scrape full article and the author.
> python fullArticle.py

## Get Comments
Checks database for new tweets and then finds replies to them.
> python getComments.py 

## Predict Bias
Checks database for comments or tweets whose bias has not been assigned. If there is any, it makes predictions and inserts into database.
> python dynamic_bias.py

# THE BIAS EFFECT OF NEWS MEDIA SOURCES ON SOCIAL MEDIA USERS
This repository contains the source code for detecting dynamic bias as it is described in our paper.
In this project, we aim to detect the possible effects of media bias by newspapers on public opinion. Our purpose is to create a system that dynamically detects bias in media and the comments.

## Installation
1. Clone this repository
2. Install dependencies
> pip install -r requirements.txt

## Training
- `cd Train`
- Download BERT embeddings from:
  > (https://github.com/google-research/bert)
- `cd data/Articles`
- Add your data here(should be in xml format or could be replaced with other file formats by changing in [train_words_dl_model.py](https://github.com/hmtkvs/MastersThesis/blob/master/Train/train_words_dl_model.py)
- `cd ..`
- `cd ..`
- Run the code
  > python train_words_dl_model.py -a 1 -w 1 -p "/homedtic/hkavas/SemEval"
  - Use `-a` argument to train a different model:
    i. `-a 1` hybrid CNN-LSTM model or
    ii. `-a 2` LSTM model.
  - Use `-w` argument for embeddings

* To evaluate the model, use -e option. This will run the script on evaluation mode, which loads the trained model from disk and runs it against the validation data to get  the model's evaluation metrics. The metrics will be printed in a log file.
    








