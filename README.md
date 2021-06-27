# Twitter-CoronaVirus-Sentiment
# NLP text classification sentiment using LTSM model
# For Dicoding Submission Project

* Dataset is provided by Kaggle uploaded by Aman Miglani
* Link to File : https://www.kaggle.com/datatattle/covid-19-nlp-text-classification
* The dataset can be fetch using kaggle library on colab 
* But i also provided the extracted dataset (train and tes csv)
* 40.000 samples
* 80:20 train test split

## Library Used
* Tensorflow
* Keras
* Scikit learn
* NLTK
* tweet-preprocessor from https://pypi.org/project/tweet-preprocessor/
* matplotlib
* Numpy
* Pandas

## Data set composition
* Feature used : OriginalTweet, Target Label : Sentiment
* Data Shape : (41157, 2)


## Step by Step Model Building
### Target Cardinality Reduction
* Sentiment has 5 Ordinal Category (['Neutral', 'Positive', 'Extremely Negative', 'Negative', 'Extremely Positive'])
* Reduce to 3 Cardinality by converting 'Extremely' parts into its regular counterparts (extremely negative becomes negative)
### Cleaning Tweet
* make functions for cleaning tweets for reproducibility purpose. function body:
* clear any tweets related tags such as #, @, http, etc using twitter-prepocessing library
* remove any punctuation
* remove any string digits
* remove any stop words using NLTK library
* remove any trailing white space
* remove any empty rows in tweet column as a result of above operations, if any
 
### Perform Train-Test Split (80:20)
### Tokenizing


### Build LSTM model
* 2 hidden layer (perceptron 512 units and 128 units)
* output layer 'Softmax'
* model = keras.Sequential([
*    layers.Embedding(input_dim=25000, output_dim=32),
*    layers.LSTM(256),
*    layers.Dense(256, activation='relu'),
*    layers.Dense(128, activation='relu'),
*    layers.Dense(3, activation='softmax')
* ])
### Adding Loss Function and Optimizer
* loss : categorical cross entropy
* optimizer adam
* metrics accuracy
### Adding Early stop function using EarlyStopping from tensorflow keras callback
* Minimum change : 0.01
* Number of epoch before stop : 5
### Training the model
* epoch : 30
* steps per epoch : 20
* verbose : 2
* validation steps : 10
* callbacks
 
## Results
* Overfitting and need further tweaks
* Best Validation Loss: 0.57
* Best Validation Accuracy: 0.81

* Loss

![](/img/download.png)

* Accuracy

![](/img/download%20(1).png)
