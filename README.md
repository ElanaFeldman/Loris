# Loris


Loris Data Challenge - Elana Feldman
 
For the challenge, I took some time to get familiar with the data in the corpus.  The corpus is billed as a set of ‘natural’ interactions, though many of them were not natural and I think this led to some of the plots of the emotions over time returning odd results.
I also looked at the parser that was provided but decided to build my own for each problem so that I had just the features I wanted from the data.
 	For the first problem, I split the conversation into speaker 1 and speaker 2 and plotted their emotions on a graph.  I tried 3 different way of determining which conversations had the biggest change in emotions.  
The first is just to subtract the max emotion from the min in the sentence.  This proved to not be useful because that will return a score of six for any conversation where the speaker was both surprised and had no emotion.  This method would work better if the emotions were really scaled and each sentence was labeled some emotion.
The next method I tried was to measure the amount of different emotions felt in a conversation over the total number of emotions felt.  I figured that having many different emotions (ie a lower percentage) would show a conversation with more emotional volatility.  This didn’t work out well because there were many conversations where at least 1 speaker had no emotion over the course of the conversation.  
The final method I developed was to measure the amount of changes the speaker went through from one sentence to the next. This proved to be a good indicator of a conversation with a lot of emotional volatility.  It is still biased towards longer conversations, so I would like to modify the function to control for that.
The conversations that were identified to have the highest emotional volatility all had many jumps from some emotion (usually surprise) to ‘no emotion’. I don’t know if they had higher occurrences of ‘no emotion’ than other conversations, but I found it interesting that they didn’t didn’t stay constant or on a similar emotion.  I would like to be able to dig into how the emotions were assigned and parse out the words that were driving the emotions to find the reason behind the labels.
	I did not get a chance to finish the predictive model in the time allotted, but I was able to build a simple Naive Bayes classifier that takes in the sentences in a conversation and outputs a sentiment score as defined by the NLTK Vader classifier.
I tried to build a model that took an emotion score and the next sentence and outputted the next emotion score, but the scoring seemed too rough to make this work consistently.
Then, I was hoping to use the sentiment classifier to take in the first set of sentences in a conversation and output the final emotion score, but I got stuck on having the sentiment classifier take in a whole conversation.  For the future, I would like to get this working and also use it to predict the upcoming sentiments of the opposite speakers.  For now, there is just a model trained on the sentences in a single conversation and their corresponding sentiment compound score that can predict the sentiment of a single other sentence.

