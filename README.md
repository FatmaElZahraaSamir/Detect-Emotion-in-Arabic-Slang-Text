# Detect-Emotion-in-Arabic-Slang-Text

## OVERVIEW
If emotion is happy then the customer is satisfied with the service and if it is love then they are extremely satisfied or if it is angry so he is unsatisfied with it and so on.
1. Input Text (user input)
2. Preprocessing
3. Embedding Vectors
4. Feature Extraction (CNN)
5. Emotion Classification

## DATA
Balanced Arabic text Twitter dataset, The dataset has more than 10,000 tweets annotated with eight emotions [1]


## PREPROCESSING
* Convert some characters like ( أ , آ , إ ) to ا as they are implicitly the same.
* Removing repeated characters like changing “ مبروووك ” to “ مبروك ”
* Stemming: Reduce words into their linguistic roots مسافر >>> سفر


## EMBEDDING
* For tweets using embedding model aravec [2]
  Method: Aravec word embedding skip-gram
  * If the word isn’t in vocabulary not recognized by embedding model.
  * Then applying stemming to the word.
  * If stemming word not recognized try using the Google search API to obtain the corrected Query.
  * If not recognized the word is rarely used so not included in the vocabulary of the embedding model.
  Aravec embedding vectors (140, 300) (maximum no. of words, vector length)
* For the labels, converted them into one hot encoded


## FEATURE EXTRACTION
CNN Architecture: two convolutional layers and one max pooling layer, the convolution, and pooling layers were repeated several times, then added a dropout layer followed by a Flatten layer to convert the feature maps resulting from convolution into a one-dimensional vector, finally added a softmax layer with 8 neurons as we have 8 classes.

## REFERENCES
1. Amr Al-Khatib, Samhaa El-Beltagy. "Emotional Tone Detection in Arabic Tweets". In proceedings of the 18th International Conference on Computational Linguistics and Intelligent Text Processing (CICLing 2017);Budapest, Hungary, 2017.
2. https://github.com/bakrianoo/aravec
