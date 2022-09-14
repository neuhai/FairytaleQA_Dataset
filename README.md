# FairytaleQA_Dataset
## Overview
This is the repository for the FairytaleQA dataset, an open-source dataset focusing on comprehension of narratives, targeting students from kindergarten to eighth grade. The FairytaleQA dataset is annotated by education experts based on an evidence-based theoretical framework. It consists of 10,580 explicit and implicit questions derived from 278 children-friendly stories, covering seven types of narrative elements or relations. 

## Repository Structure
```bash

├── FairytaleQA_Dataset
│    ├── split_by_origin
│    │    └── [origin]-fairybook
│    │         ├── [storyname]-questions.csv 
│    │         ├── [storyname]-story.csv 
│    │         └── ...
│    │
│    └── split_for_training
│         └── [split]
│              ├── [storyname]-questions.csv 
│              ├── [storyname]-story.csv 
│              └── ...
│
└── FairytaleQA_Dataset_Sentence_Split
     ├── split_by_origin
     │    └── [origin]-fairybook
     │         ├── [storyname]-story.csv
     │         └── ...
     │
     └── split_for_training
          └── [split]
          │    ├── [storyname]-story.csv
          │    └── ...
          │
          ├── sentence_level_test.csv
          ├── sentence_level_train.csv
          └── sentence_level_val.csv
```
We provide two different categorizations for the FairytaleQA dataset: 
 - **split by origin**, where the stories are categorized by their cultural origins
 - **split for training**, where the stories are split into train/test/val splits 
     - train split: 232 books with 8548 QA-pairs
     - val split: 23 books with 1025 QA-pairs
     - test split: 23 books with 1007 QA-pairs

Each story has two corresponding files, ```[storyname]-story.csv``` contains the story content where each line is a story section defined by the education experts; and ```[storyname]-questions.csv``` contains experts-generated QA-pairs. 

```[storyname]-story.csv``` has two columns:
 - **'section'**: story section id 
 - **'text'**: story section content. 

```[storyname]-questions.csv``` has 9 useful columns:
 - **'question_id'**: question id 
 - **'local-or-sum'**: 'local' denotes the question is related to only one story section, while 'summary' denotes the question is related to multiple story sections
 - **'cor_section'**: related section id(s), **matching with the 'section' column in corresponding story file**
 - **'attribute1'**: categorized by education experts into seven narrative elements: character / setting / action / feeling / causal relationship / outcome resolution, detailed definition is described in the paper
 - **'question'**: the question content
 - **'ex-or-im1'**: 'explicit' denotes the answer can be found in the story content, while 'implicit' denotes the answer require high-level summarization
 - **'answer1'**: the 1st answer  (available in all splits)
 - **'answer4'**: the 2nd answer by another annotator (only available in storys in test / val splits)
 - **'ex-or-im2'**: similar to 'ex-or-im1', but annotated by another annotator (only available in storys in test / val splits)


In addition to the original FairytaleQA dataset, we also provide stories split by sentences in ```FairytaleQA_Dataset_Sentence_Split```. This sub-folder follow the same structure as the sub-folder for the original dataset, except that it only contains the story csv files.



## Related Papers
1. [```Fantastic Questions and Where to Find Them: FairytaleQA – An Authentic Dataset for Narrative Comprehension```](https://aclanthology.org/2022.acl-long.34/) **(Accepted to ACL 2022)** proposed the FairytaleQA dataset with details about the annotation process and baseline benchmark experiments on Question-Answering as well as Question Generation. The code repository for baseline experiments can be found here: https://github.com/WorkInTheDark/FairytaleQA_Baseline

2. [```It is AI’s Turn to Ask Humans a Question: Question-Answer Pair Generation for Children’s Story Books```](https://aclanthology.org/2022.acl-long.54/) **(Accepted to ACL 2022)** built an automated Question-Answer Generation (QAG) system upon the FairytaleQA dataset. The code repository for the QAG system can be found here: https://github.com/WorkInTheDark/FairytaleQA_QAG_System
