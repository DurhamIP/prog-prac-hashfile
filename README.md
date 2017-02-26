#Introduction to Programming

##Practical: HashMaps and File Handling

## Instructions

This practical focuses on file handling and using HashMaps

### Word  frequency

Relative word frequency in texts is a simple way of identifying the type of text
involved.

First of all we need to be able to calculate the word frequency for a piece of
text by counting the number of times each word occurs.

E.g. in the previous sentence there were 3 “of”, 2 “the”, 2 “word”, 2 “to”, 1
“calculate” etc.

Define a Java class _WordFrequency_ with a HashMap field with keys as String
and values as Integer. The constructor should take a piece of text to analyse.

Include methods to

* return a set of all the words included (all lower case and without
whitespace at beginning or end).
* add more text to be included in the word frequency count.
* find the frequency of a given word i.e. the number of times it appears in
the text. The word should be passed as a parameter and the method
should return 0 if the word does not occur.
* find the relative frequency of a word i.e. the frequency divided by the
total number of words in the text.
* create an object of type _WordFrequency_ from a file with a name specified in a parameter. Rather than a constructor, this should be a static method called `makeInstance` which returns an object of type _WordFrequency_.


###Word frequency by document type

Different types of documents tend to have different relative frequencies. Next
we are going to try to guess the type of document based on the relative
frequencies. First of all you need to choose two similar but different types of
documents e.g. song lyrics by Coldplay and The Beatles, or it might be two
different poets, articles from different newspapers or whatever you like. You choose, but make sure you have access to the texts of range of
the documents.

We want to record the overall word frequencies of the two types of documents
and store them in the class. Define a static variable `typeFrequency` which is
a map from document type (represented as a String e.g. `Coldplay`) to
_WordFrequency_. Add a method `classifyAs` which takes the document type
as a parameter and updates the `typeFrequency` variable.

Write a static method which includes a range of examples of each document
types, creates the corresponding _WordFrequency_ object and classifies them 
appropriately. Load the sample texts from files whose names apear in a statically defined list.

Once youʼve done all this you can try to identify the type of a document by its
relative word frequencies. Define a method `distanceFrom` which works out
the "distance" between two _WordFrequency_ objects, one of which is `this`
object, the other given as a parameter. The more different the relative word
frequencies, the larger the distance. A simple way to do this is to go through
all the words which occur in each of the documents and add together the
absolute value of the differences between the relative frequencies. You may
have a smarter idea. Once you can find the distance between two
WordFrequency objects you can try to guess the type of a piece of text by
finding the WordFrequency in the `typeFrequency` map which is closest to the
given text. This should be wrapped up in a static method which takes a String
(the text to be guessed) and returns an ordered list of `String` (the types of the text ranked according to similarity of word frequency). The quickest way to do this is to use the `Comparator` interface and the `sort` method from the `Collections` class.

Try this out and see if your program can guess what type if text it is looking at.
Does it matter how many example texts you give it? Can it tell between three
or more types of text? Is there a better implementation of `distanceFrom`?
