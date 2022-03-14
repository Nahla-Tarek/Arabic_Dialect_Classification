# Arabic_Dialect_Classification
<img src="/map.png" alt="My cool logo"/>
This project is about classifying Arabic tweets into 18 Arabic dialects covering 18 different countries in the Middle East and North Africa region.
The dataset and the dialect identification problem were addressed in this paper https://arxiv.org/pdf/2005.06557.pdf
The geographically adjacent countries have similar dialects such as:
- Maghreb, Tunisia, Libya, and algeria are in Meghreb region as shown in the above image 
- Egypt , Sudan are in nile basin region
- Jordan, lebanon, palestine, and syria are in levant region
- kuwait, Saudi Arabia, Arab Emirates, Oman, Bahrain, and Qatar are in gulf region
    
To faciliate the process and to have more efficient results. I divided the process into 2 stages:
- first stage: predict to which region the tweet belongs 
- second stage: predict to which country in this region the tweet belongs

## Model Archectiture
<img src="/model_arc.png" alt="My cool logo"/>

## Data Preprocessing
- Remove any non-word characters from the text
- Remove any number in the text
- Remove any non-Arabic characters from the text
- Remove stop words
- Remove Common words between all Arabic countries such as لا اله الا الله، استغفر الله العظيم
- Stemming
### Two models were trained Machine Learning Model, Deep Learning Model
## ML algorithm
I used 3 TFIDF-Vectorizers to extract features, combined their outputs using featureunion.
-The parameters of the first one: analyzer is “word” and the ngram_range is “(1,3)”.
-The parameters of the second one: analyzer is “char_wb” and the ngram_range is  “(2,5)”.
-The parameters of the third one: analyzer is “char” and the ngram_range is “(2,4)”.
I used a Voting classifier that trains on linearsvc, multinomialNB, BernoulliNB

## DL model
- Fasttext skigram model is trained on the corpus, to create an embedding matrix that contains embedding words each one represents a word in the corpus.
- The tokenizer converts each sequence of words to a sequence of their indices in the tokenizer
- Assign every word embedding with its index in the tokenizer.
- Padding sentences to maximum words length
- Building Model consists of embedding layer, lstm with 128 units, dropout, and dense layer of 5000 units
## Deployment
Flask is used 
<img src="/app.png" alt="My cool logo"/>














