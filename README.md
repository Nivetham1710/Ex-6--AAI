<H3>NAME : NIVETHA M</H3>
<H3>REGISTER NO. 212221240034</H3>
<H1 ALIGN =CENTER>Implementation of Semantic ANalysis</H1>
<H3>Aim: 
 To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.

## Program:
```
#importing packages
! pip install nltk
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')

#reading content from file
f = open("/content/samplefile.txt", "r")
sentences = f.readlines()
f.close()

verbs = [[] for _ in sentences]
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)

  # Tokenize the sentence into words
  words = word_tokenize(sentence)

  # Identify the parts of speech for each word
  pos_tags = nltk.pos_tag(words)

  # Print the parts of speech
  for word,tag in pos_tags:
    print(word,"->",tag)

    # Save verbs
    if tag.startswith('VB'):
      verbs[i].append(word)
  i+=1
  print("\n\n")

# Identify synonyms and antonyms for each word
print("Synonyms and Antonymns for verbs in each sentence:\n")
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)
  pos_tags = nltk.pos_tag(verbs[i])
  for word,tag in pos_tags:
    print(word,"->",tag)
    synonyms = []
    antonyms = []
    for syn in wordnet.synsets(word):
      for lemma in syn.lemmas():
        synonyms.append(lemma.name())
        if lemma.antonyms():
          for antonym in lemma.antonyms():
            antonyms.append(antonym.name())

    # Print the synonyms and antonyms
    print("Synonyms:",set(synonyms))
    print("Antonyms:", set(antonyms) if antonyms else "None")
    print()
  print("\n\n")
  i+=1
```
### OUTPUT:
![image](https://github.com/Nivetham1710/Ex-6--AAI/assets/94155183/ded4d674-7b6e-4da5-818f-def0dfb772ed)
![image](https://github.com/Nivetham1710/Ex-6--AAI/assets/94155183/618da614-e931-4120-803e-2d93a705e975)

<H3>Result:</H3>
Thus ,the program to perform the Parts of Speech identification and Synonymis executed sucessfully.
