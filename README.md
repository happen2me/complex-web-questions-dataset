---
license: apache-2.0
source: https://github.com/KGQA/KGQA-datasets
---

# Dataset Card for Dataset Name

## Dataset Description

- **Homepage:** https://www.tau-nlp.sites.tau.ac.il/compwebq
- **Repository:** https://github.com/alontalmor/WebAsKB
- **Paper:** https://arxiv.org/abs/1803.06643
- **Leaderboard:** https://www.tau-nlp.sites.tau.ac.il/compwebq-leaderboard
- **Point of Contact:** alontalmor@mail.tau.ac.il.

### Dataset Summary

**A dataset for answering complex questions that require reasoning over multiple web snippets**

ComplexWebQuestions is a new dataset that contains a large set of complex questions in natural language, and can be used in multiple ways:

  - By interacting with a search engine, which is the focus of our paper (Talmor and Berant, 2018);
  - As a reading comprehension task: we release 12,725,989 web snippets that are relevant for the questions, and were collected during the development of our model; 
  - As a semantic parsing task: each question is paired with a SPARQL query that can be executed against Freebase to retrieve the answer.

### Supported Tasks and Leaderboards

[More Information Needed]

### Languages

- English

## Dataset Structure

QUESTION FILES

The dataset contains 34,689 examples divided into 27,734 train, 3,480 dev, 3,475 test.
each containing:

```
"ID”: The unique ID of the example; 
"webqsp_ID": The original WebQuestionsSP ID from which the question was constructed; 
"webqsp_question": The WebQuestionsSP Question from which the question was constructed; 
"machine_question": The artificial complex question, before paraphrasing; 
"question": The natural language complex question; 
"sparql": Freebase SPARQL query for the question. Note that the SPARQL was constructed for the machine question, the actual question after paraphrasing
may differ from the SPARQL. 
"compositionality_type": An estimation of the type of compositionally. {composition, conjunction, comparative, superlative}. The estimation has not been manually verified,
 the question after paraphrasing may differ from this estimation.
"answers": a list of answers each containing answer: the actual answer; answer_id: the Freebase answer id; aliases: freebase extracted aliases for the answer.
"created": creation time
```

NOTE: test set does not contain “answer” field. For test evaluation please send email to 
alontalmor@mail.tau.ac.il.


WEB SNIPPET FILES


The snippets files consist of 12,725,989 snippets each containing
PLEASE DON”T USE CHROME WHEN DOWNLOADING THESE FROM DROPBOX (THE UNZIP COULD FAIL)

"question_ID”: the ID of related question, containing at least 3 instances of the same ID (full question, split1, split2); 
"question": The natural language complex question; 
"web_query": Query sent to the search engine. 
“split_source”: 'noisy supervision split' or ‘ptrnet split’, please train on examples containing “ptrnet split” when comparing to Split+Decomp  from https://arxiv.org/abs/1807.09623
“split_type”: 'full_question' or ‘split_part1' or ‘split_part2’ please use ‘composition_answer’ in question of type composition and split_type: “split_part1” when training a reading comprehension model on splits as in Split+Decomp  from https://arxiv.org/abs/1807.09623 (in the rest of the cases use the original answer).
"web_snippets": ~100 web snippets per query. Each snippet includes Title,Snippet. They are ordered according to Google results.

With a total of
10,035,571 training set snippets
1,350,950 dev set snippets
1,339,468 test set snippets


### Source Data

The original files can be found at this [dropbox link](https://www.dropbox.com/sh/7pkwkrfnwqhsnpo/AACuu4v3YNkhirzBOeeaHYala)


### Licensing Information

Not specified

### Citation Information

```
@inproceedings{talmor2018web,
  title={The Web as a Knowledge-Base for Answering Complex Questions},
  author={Talmor, Alon and Berant, Jonathan},
  booktitle={Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long Papers)},
  pages={641--651},
  year={2018}
}
```

### Contributions

Thanks for [happen2me](https://github.com/happen2me) for contributing this dataset.