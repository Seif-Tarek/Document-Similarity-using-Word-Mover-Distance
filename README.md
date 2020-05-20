# Document Similarity using Word Mover's Distance and Cosine similarity
Document similarity is a very needed task. it used to determine how close two documents to each other in lexical and meaning. Here are some examples of why document similarity is needed:

- Summarization, check how the summary is close to the main article that was input to the summarization module
- Search engines need to bring the articles that are similar to the query and also on question and answer websites like Quora need to - know a similar question or whether the question is duplicate or not.
- Plagiarism conditions, if a university or an institute wants to test the students' documents if they are similar or not
- ChatBot should be able to understand semantically similar queries from users and provide a uniform response.

## Dataset
The dataset used is inspired by CNN/Daily Mail Data from the paper "Get To The Point: Summarization with Pointer-Generator Networks" and it is consists of articles and their summaries. So, the final dataset as mentioned in figure 1 consists of some articles, their summary and labeled by 1 and some articles, summaries of other articles, and labeled by 0 as they aren't similar. you can get the final dataset from here: https://drive.google.com/file/u/4/d/1CUPi6nri5u21DbVYr0MfHSOVOLS2TlYs/view?usp=drive_open.

## Feature Engineering
#### 1. Cosine Similarity
Cosine similarity is a measure of similarity between two non-zero vectors of an inner product space that measures the cosine of the angle between them.

![Alt Text](https://i.imgur.com/HqKjGoQ.jpg)


#### 2. Word Mover's Distance
Word Mover's Distance (WMD) uses the word embeddings of the words in two texts to measure the minimum distance that the words in one text need to travel in semantic space to reach the words in the other text.
The WMD is measured by measuring the minimum euclidean distance between each word in the two documents in word2vec space. if the distance is small then words in the two documents are close to each other.
So, If I have the same two sentences:
sentence 1: "Obama speaks to the media in Illinois"
sentence 2: "The president greets the press in Chicago"
After removing stopwords, The word mover distance is small as mentioned in the figure.


![Alt Text](https://imgur.com/L1QNfPK.jpg)


## Model Building
My team and I implemented this model as part of our graduation thesis in single document summarization and evaluation, where we give the generated summary a similarity score
We use the two features mentioned above as we knew that cosine similarity fails a lot and WMD is doing great alone. but together the model is making the best result.
Logistic regression is used for two reasons. First, the dataset has two classes as output 0 or 1 (similar or not). Second, Logistic regression outputs probability which is the main task to produce similarity score.
The coefficient of the model is -6 for WMD which makes sense as the documents are similar when the WMD is small, and 9.2 for cosine similarity which also makes sense as cosine similarity has a bigger effect. when there are some similar words then the documents tend to be similar.

## Result
The logistic regression model is trained through 1200 data entry in the dataset and then tested through 400 data entry. It showed very promising output as it get accuracy of 
