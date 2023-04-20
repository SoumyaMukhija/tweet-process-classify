# tweet-process-classify
Our aim is to classify Tweets as either “positive”,
“neutral”, or “negative” by using logistic regression classifier and pipelines for pre-processing
and model building.

The program has the following parameters -

1. Path of the input file on a public location such as AWS S3.

2. Path of the output file on a public location such as AWS S3.

## 1. Loading: 

First step is to load the text file from the path specified in argument 1. After that,
we remove rows where the text field is null.

## 2. Pre-Processing: Stages:

• Stop Word Remover: Remove stop-words from the text column

• Tokenizer: Transform the text column into words by breaking down the sentence into
words 

• Term Hashing: Convert words to term-frequency vectors

• Label Conversion: The label is a string e.g. “Positive”, which we convert to
numeric format.

We create a pipeline of the above steps and then transform the raw
input dataset to a pre-processed dataset.

## 3. Model Creation

We create a logistic regression classification model. We create a ParameterGridBuilder for parameter tuning and then use the CrossValidator
object for finding the best model parameters. More details can be seen here:
https://spark.apache.org/docs/2.2.0/api/scala/index.html

## 4. Model Testing & Cross Validation

Next, we train and test our model on
the given dataset and output classification evaluation metrics, such as accuracy, etc. We can
see details of multi-class evaluation metrics at
https://spark.apache.org/docs/2.2.0/mllib-evaluation-metrics.html.

## 5. Output: 

Finally, we write the output the classification metrics to a file whose location
is specified by the second argument.
