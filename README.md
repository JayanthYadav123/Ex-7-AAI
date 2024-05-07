#### G .Jayanth.
#### 212221230030.
#### EX. NO.7

## Implementation of Text  Summarization</H1>
### Aim: 
To perform automatic text summarization using Natural Language Processing (NLP) techniques.

### Algorithm:
#### Step 1:
Import necessary libraries for natural language processing tasks.<BR>
#### Step 2:
Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
#### Step 3:
Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
#### Step 4: 
Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
#### Step 5: 
Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
### Program:

```
!pip install nltk
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize,sent_tokenize
from nltk.stem import PorterStemmer
nltk.download( 'punkt' )
nltk.download( 'stopwords' )
def preprocess_text(text):
	# Tokenize the text into words
	words = word_tokenize(text)
	# Remove stopwords and punctuation
	stop_words= set(stopwords.words( 'english'))
	filtered_words= [word for word in words if word. lower() not in stop_words and word.isalnum()]

	# Stemming
	stemmer = PorterStemmer()

	stemmed_words= [stemmer. stem(word) for word in filtered_words]
	return stemmed_words
def generate_summary(text,num_sentences=3):

	sentences= sent_tokenize(text)
	preprocessed_text = preprocess_text(text)
	# Calculate the frequency of each word
	word_frequencies =nltk. FreqDist (preprocessed_text)

	# Calculate the score for each sentence based on word frequency
	sentence_scores ={}
	for sentence in sentences:
		for word, freq in word_frequencies.items():
			if word in sentence.lower():
				if sentence not in sentence_scores:
					sentence_scores[sentence] = freq
				else:
					sentence_scores[sentence]+= freq
	# Select top N sentences with highest scores
	summary_sentences= sorted(sentence_scores, key=sentence_scores.get,reverse=True) [ : num_sentences]

	return ' '. join(summary_sentences)
if __name__=="__main__":
	input_text ="""
	Natural language processing (NLP) is a subfield of artificial intelligence.
	It involves the development of algorithms and models that enact NLP.
	NLP is used in various applications, including chatbots, language Understanding, and language generation.
	This program demonstrates a simple text summarization using NLP"""
summary = generate_summary(input_text)
print("Origina1 Text: ")
print (input_text )
print( " \nSummary : " )
print(summary)
```

### Output

<img width="767" alt="image" src="https://github.com/JayanthYadav123/Ex-7-AAI/assets/94836154/e330e1ed-9e33-4050-a8bf-3d4b27789d15">
<img width="452" alt="image" src="https://github.com/JayanthYadav123/Ex-7-AAI/assets/94836154/afaab599-f132-4e01-9a32-e4be8ad31832">
<img width="871" alt="image" src="https://github.com/JayanthYadav123/Ex-7-AAI/assets/94836154/809fad9c-46fc-4411-a215-47249f1d8c0a">





### Result:
Thus ,the program to perform the Text summarization is executed sucessfully.


