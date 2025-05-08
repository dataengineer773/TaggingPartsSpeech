We have text data and want to tag each word or character with its part of speech, Use NLTK’s pre-trained parts-of-speech tagger, The output is a list of tuples with the word and the tag of the part of speech. NLTK uses the Penn
Treebank parts for speech tags. Some examples of the Penn Treebank tags are Once the text has been tagged, we can use the tags to find certain parts of speech. For example, here are
all nouns, A more realistic situation would be that we have data where every observation contains a tweet and we
want to convert those sentences into features for individual parts of speech (e.g., a feature with 1 if a
proper noun is present, and 0 otherwise), Using classes_ we can see that each feature is a part-of-speech tag, If our text is English and not on a specialized topic (e.g., medicine) the simplest solution is to use
NLTK’s pre-trained parts-of-speech tagger. However, if pos_tag is not very accurate, NLTK also gives
us the ability to train our own tagger. The major downside of training a tagger is that we need a large
corpus of text where the tag of each word is known. Constructing this tagged corpus is obviously labor intensive and is probably going to be a last resort.
All that said, if we had a tagged corpus and wanted to train a tagger, the following is an example of how
we could do it. The corpus we are using is the Brown Corpus, one of the most popular sources of tagged
text. Here we use a backoff n-gram tagger, where n is the number of previous words we take into
account when predicting a word’s part-of-speech tag. First we take into account the previous two words
using TrigramTagger; if two words are not present, we “back off” and take into account the tag of the
previous one word using BigramTagger, and finally if that fails we only look at the word itself using
UnigramTagger. To examine the accuracy of our tagger, we split our text data into two parts, train our
tagger on one part, and test how well it predicts the tags of the second part
