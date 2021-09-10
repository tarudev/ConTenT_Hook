# Content_Based_Recommendation_System_TFIDF
An implementation of a Recommendation System using textual processing ability of TF-IDF Vectoriser to draw sense of a 'descriptive text' and provide recommendations

For this program, we will be using 5000 IMdB movies dataset which is in 2 parts:
1. Movies.csv
2. Credits.csv

The program extracts the description of the movies which is under the column 'overview'. The preprocessing involved in this program drops the unnecessary columns, fills the NaN, null entries or NONE,etc. and removes the duplicate titles.
After that we deploy TF-IDF Vectoriser.

TF-IDF: It is a method of finding the relevance of a word wrt a document. It is used find the weighing score of a word in a document as per its significance. 
The term TF-IDF is short form for Term Frequency and Inverse Document Frequency.
Term Frequency: The number of times a term occurs in a document is called its term frequency. ( Number of reputations of a word in sentence/ Number of words in sentence)
Inverse Document Frequency: This factor determines the irrelevance of certain words. Some terms get thrown around a lot but impart little meaning to draw sense.
                 IDF = log( Number of Sentences / Number of sentecnces containing the word ) 
                 
So, as we call the tfidf vectoriser, we set the important parameters:

1. min_df: sets the minimum document frequency threshold to be considered to include a term as a token of vector vocabulary
2. analyser: sets whether to consider 'words' or 'char' n-grams for feature extraction
3. stop_words: it provides the set of stopwords to consider for filtering terms which are inherrently non-sensical, here, we use the english set
4. ngram_range: Often, singular terms don't reflect much of the crux of the entire sentence than combination of words, this parameter sorts this problem by considering a bunch of      words to tokenise and extract numerical meaning out of it in terms of significance
5. token_pattern: It defines the regular expression for defining the structure of a token.

Now, we fit the data of overview on to the tfidf vectoriser and obtain a sparse matrix of values derived from textual processing as mentioned above.
A signoid kernel is called upon which draws the similar features between 2 vectors of the sparse matrix produced (in a pairwise manner) and generates a numeric measure of their similarity in the range of 0 to 1 as a matrix (score matrix)
* Closer to 1 means similar or likely to be recommended
* Closer to 0 means not similar or likely to be ommitted

Finally, we feed the respective index of the movie title to the score matrix and sort the repective scores in descending order to get the most similar or recommended movies.
