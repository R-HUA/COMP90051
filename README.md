# COMP90051

### Statistical Machine Learning (2022_SM2)  

#### Project  2  

This task is to come up with test predictions for an authorship attribution problem given a training set and test inputs.  
You will participate as part of a group of students in a Kaggle competition, where you upload your test predictions.  
Your mark (detailed below) will be based on your test prediction performance and a short report documenting your solution.  
The training data is a set of academic papers published in a time period (spanning 19 years), the given paper information includes the year it was published, the words in the title and abstract, the venue it was published in, and its authors. All the information in the discrete data has been given randomly assigned IDs, except year of publication. The test data is a list of 800 papers, all published in the year after the training period. Your task is to predict for
each of the test papers, which of a set of 100 prolific authors were involved in writing the paper. The correct answer may be zero, one or many of these authors.

##### train.json 
 contains 25.8k papers. This file is in JSON format as a list of papers, where each paper is a dictionary with keys:
* authors: a set of the IDs of the authors of the paper, with values in {0, . . . , 21245};
* year: the year the paper was published, measured in years from the start of the training period;
* venue: the publication venue (name of journal/conference series), mapped to a unique integer value {0, . . . , 464} or “” if there is no specified venue;
* title: the sequence of words in paper title, after light preprocessing, where each word has been mapped to an index in {1, . . . , 4999}; and
* abstract: the sequence of words in paper abstract, proceessed as above, using the same word-integer mapping.
Authors with IDs < 100 are the prolific authors, the target of this classification task. Many of the papers in train.json don’t include any prolific authors; you will have to decide whether (and how) to use these instances in training. Note that we include some papers in the test set (described below) which have no prolific authors (no more than 25% of papers), so you will need to be able to handle this situation.


##### test.json 
 contains 800 papers, stored in JSON format with the fields year, venue, title and abstract as described above, along with one additional item:
* identifier: The unique identifier of the paper, used to ensure your predictions are aligned correctly in Kaggle;
* coauthors: The IDs of the co-authors of the paper, with values in {100, . . . , 21245} (profilic authors with IDs < 100 are excluded). This field may be empty if there are no co-authors.
