

## Some IDeas

```python

import os
import string

class Word4Word:

    def __init__(self):
        self.worddict = {}
        self.letterdict = {}
        self.lines = []
        self.linecount = 0
        self.wordcount = 0
        self.lettercount = 0

    def print(self,filename):
        with open(filename, 'r') as f:
            for line in f:
                print(line)

    def loadtextfile(self, filename):
        with open(filename, 'r') as f:
            for line in f:
                self.lines.append(line)

    def remove_punctuation(self, input):
        return input.translate(str.maketrans('', '', string.punctuation))
    
#`func wc(String input)`
# commonly called "wc"; count the number of characters in a file, number of words, number of lines.
# Returns an tuple with the number of lines, words and characters.
    def wc(self, input):
        lines = 0
        words = 0
        characters = 0
        for line in input:
            line = self.remove_punctuation(line)
            lines += 1
            spline = line.split()
            words += len(spline)
            characters += len("".join(spline))
        return (lines, words, characters)
        
# `func wordFrequency(String input)`
# word count. words in the string, produce a dictionary with (str word, int numOfTimes).
    def wordFrequency(self, input):
        worddict = {}
        for line in input:
            line = self.remove_punctuation(line)
            for word in line.split():
                if word in worddict:
                    worddict[word] += 1
                else:
                    worddict[word] = 1
        return worddict
    
# `func letterFrequency(String input)`
# letter frequency, write a program that collects the frequency of each letter within the input. 
# produces a dictionary with letters as the key, number of occurences as value.

    def letterFrequency(self, input):
        letterdict = {}
        for line in input:
            line = line.translate(str.maketrans('', '', string.punctuation))
            line = "".join(line.split())
            for letter in line:
                if letter in letterdict:
                    letterdict[letter] += 1
                else:
                    letterdict[letter] = 1
        return letterdict
    
    def frequency(self, word):
        return self.worddict[word]/self.wordcount
    
    def letterfrequency(self, letter):
        return self.letterdict[letter]/self.lettercount
    
    def getMostCommonWordFromDict(self,dictionary):
        return max(dictionary, key=dictionary.get)
    
if __name__ == "__main__":
    # for each file in testdata/ directory, run the following tests
    files = os.listdir('testdata/')
    for file in files:
        w4w = Word4Word()
        w4w.loadtextfile('testdata/'+file)
        print('File:', file)
        w4w.linecount, w4w.wordcount, w4w.lettercount = w4w.wc(w4w.lines)
        print('\t', w4w.linecount, w4w.wordcount, w4w.lettercount)
        w4w.worddict = w4w.wordFrequency(w4w.lines)
        print('\t', len(w4w.worddict),'unique words')
        print('\t[', w4w.getMostCommonWordFromDict(w4w.worddict),'] most common word')
        print('\t', len(w4w.letterFrequency(w4w.lines)),'unique letters')
        print('\t', w4w.letterFrequency(w4w.lines))



        # print(w4w.letterFrequency())
        # print(w4w.frequency('the'))
        # print(w4w.letterfrequency('t'))
```
