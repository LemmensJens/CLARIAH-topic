## Documentation

### Introduction

This repository contains code for the topic modeling pipeline for the CLARIAH-VL digital text analysis dashboard and pipeline (DTADP). 

### Installation

Create and activate a conda python 3.9 environment: 

```conda create -n {name here} python=3.9``` -> ```conda activate {env_name}```

Clone the repository: ```git clone https://github.com/LemmensJens/CLARIAH-topic.git```

Navigate to the repository ```cd CLARIAH-stylo``` and install the requirements with ```pip install -r requirements.txt```. 

Finally, download NLTK's stopwords with ```python -m nltk.downloader stopwords```. 

### Quick start
Set up the configuration file, run ```python create_config.py```, and start the pipeline by calling ```python -u topic_modeling.py```.

### Demo
For a demo, run ```python get_demo_data.py``` to retrieve the 20 NewsGroups dataset, and run ```python -u topic_modeling.py``` with the default config settings.

### Pipeline usage and overview

#### Set up config file
In ```create_config.py```, specify the following:
- which algorithm to use: BERTopic, Top2Vec, LDA or NMDF
- input format (.csv file or .zip containing .txt)
- the directory to the data
- in case of .csv: the column name containing the text data and the delimiter

Then, specify parameters related to the chosen algorithm, and specify preprocessing steps:
- remove NLTK stopwords
- remove custom stopwords
- remove punctuation
- lowercase text
- lemmatize text
- use ngrams

#### Run the pipeline
Create the config file by running ```python create_config.py``` and start the pipeline with ```python -u topic_modeling.py```.

#### Output
```evaluation.csv``` contains diversity and coherence scores

```keywords_per_topic.csv``` shows top n most important keywords per topic

```topic_doc_matrix.csv``` matrix showing how much each document relates to each topic

```topic_term_matrix.csv``` matrix containing the weights of all tokens with respect to the topics

```topic_term_weights``` folder containing visualizations for the most important keywords per topic and their weights

### To do
Implement visualizations for the output of BERTopic and Top2Vec.

