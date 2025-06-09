---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Normalizzazione - NLP
---

Word Normalization Putting words/tokens in a standard format: • USA or U.S.A. • Uhhuh or uh-huh • Fed or fed • am, is, be, are Case folding, in applications like IR, where all letters are reduced to lower case, because users tend to use lower case. A possibile exception might be upper case in mid-sentence (e.g., General Motors; Fed vs. fed; SAIL vs. sail). For sentiment analysis, MT and Information extractioncase is helpful (e.g., US versus us is important).

## Lemmatization
Lemmatization is the task of determining that two words have the same root, despite their surface differences. Lemmatization, represent all words as their lemma (a set of lexical forms having the same stem, the same major part-of-speech, and the same word sense), their shared root, in dictionary headword form. For example: • am, are, is → be • He is reading detective stories → He be read detective story Lemmatization is done by morphological parsing. Morphology is the study of the way words are built up from smaller meaning-bearing units called morphemes. Two broad classes of morphemes can be distinguished: stems, the core meaning-bearing units, and affixes, parts that adhere to stems, often with grammatical functions. A morphological parser would parse cats into two mophemes cat and s. Lemmatization algorithms can be complex, sometimes we make use of a simpler method, which consists of chopping off word-final affixes. This process is called stemming, that can be seen as a naïve version of morphological analysis. For example, the Porter stemmer, a widely used stemming algorithm, The Porter stemmer is based on a series of rewrite rules run in series, a cascade, in which output of each pass fed to next pass. Some sample rules: • ATIONAL → ATE (e.g., relational → relate) • ING → / if stem contains vowel (e.g., motoring → motor) • SSES → SS (e.g., grasses → grass)