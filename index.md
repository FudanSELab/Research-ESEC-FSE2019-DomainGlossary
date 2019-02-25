# Domain-specific Glossary Construction

We post the result of our approach and the data used in empirical study of paper in this page.


## 1. Selected Domains
The two subject domains that we choose for the study represent two kinds of technical domains. Deep learning domain includes software libraries that are written in different languages and provide similar functionalities for the development of deep learning applications. Hadoop domain is a software ecosystem that consists of interdependent software systems. 

The subject projects we choose for the deep learning domain are three popular deep learning libraries:

Deeplearning4j 1.0.0-beta3 (https://deeplearning4j.org/, https://github.com/deeplearning4j/deeplearning4j/)<br>
Tensorflow 1.12 (https://www.tensorflow.org/, https://github.com/tensorflow/tensorflow)
PyTorch 1.0.0 (https://pytorch.org/, https://github.com/pytorch/pytorch)

The subject projects we choose for the Hadoop domain are:

Hadoop 2.9.2 (http://hadoop.apache.org/, https://github.com/apache/hadoop)<br>
HBase 2.1.0 (http://hbase.apache.org/, https://github.com/apache/hive)<br>
Hive 2.3.4 (http://hive.apache.org/, https://github.com/apache/hbase)<br>

## 2. Results of Approach
The results of our approach are devided into 4 parts: term extraction, alias merging, relation identification and explanation extraction.

#### Deep Learning

Term Extraction: [term.txt](./Result/DeepLearning/term.txt), each line in this file represents a term.

Alias Merging: [concept.txt](./Result/DeepLearning/concept.txt), each line in this file represents an alias set of a concept (separated by ",").

Relation Identification: [relation.json](./Result/DeepLearning/relation.json), in the json file, each element of the list has 4 fields. "start_concept" and "end_concept" represent alias sets of concepts, "type" means relation type. ("start_concept", "type", "end_concept") means the triple of a relation.

Explanation Extraction: [explanation.json](./Result/DeepLearning/explanation.json), each element in the list has a key and value mean the concept and its corresponding explanations.

#### Hadoop

Term Extraction: [term.txt](./Result/Hadoop/term.txt), each line in this file represents a term.

Alias Merging: [concept.txt](./Result/Hadoop/concept.txt), each line in this file represents an alias set of a concept (separated by ",").

Relation Identification: [relation.json](./Result/Hadoop/relation.json), in the json file, each element of the list has 4 fields. The fields "start_concept", "end_concept" and "type" represent an relation like ("start_concept", "type", "end_concept"). Note that the "start_concept" and "end_concept" are alias sets of concepts.

Explanation Extraction: [explanation.json](./Result/Hadoop/explanation.json), each element in the list has a key and value, which mean a concept and its corresponding explanations respectively.

## 3. Evaluation
There are three rearch questions in our paper.

### RQ1: How accurate are the extracted domain concepts, relations, and explanations? Can the approach outperform existing approaches for domain glossary extraction?

#### 1) Accuracy of key steps of our approach.
We evaluate the accuracy of term extraction, alias merging, relation identification, explanation extraction, for each step we select 384 samples. We invite three master students who are experts in the domain to examine the accuracy. For each examination two experts independently make the decision based on the related contexts and their agreement on the decision is checked. When there is disagreement on a decision, the third expert gives an additional judgement.

The annotation results after arbitration are shown in following files:

##### Deep Learning

Term Extraction: [term_extraction.json](./RQ1/DeepLearning/term_extraction.json), each element in the list has two fields. The field "term" represents a term. The field "correct" is annotated by experts and means whether the extracted term is correct or not.

Alias Merging: [alias_merging.json](./RQ1/DeepLearning/alias_merging.json), each element in the list has three fields. The fields "term1" and "term2" mean two extracted terms. The field "correct" is annotated by experts and means whether the two terms are merged correctly.

Relation Identification: [relation_identification.json](./RQ1/DeepLearning/relation_identification.json), each element in the list has four fields. The fields "start_concept", "end_concept" and "relation" mean a relation triple like ("start_concept", "relation", "end_concept"). The field "correct" is annotated by experts and means whether the relation is correct.

Explanation Extraction: [explanation_extraction.json](./RQ1/DeepLearning/explanation_extraction.json), each element in the list has three fields. The fields "concept" and "explanation" represent an extracted concept and its explanations. The field "useful" is annotated by expert and means whether the explanations are useful to understand the concept.

##### Hadoop

Term Extraction: [term_extraction.json](./RQ1/Hadoop/term_extraction.json), each element in the list has two fields. The field "term" represents a term. The field "correct" is annotated by experts and means whether the extracted term is correct or not.

Alias Merging: [alias_merging.json](./RQ1/Hadoop/alias_merging.json), each element in the list has three fields. The fields "term1" and "term2" mean two extracted terms. The field "correct" is annotated by experts and means whether the two terms are merged correctly.

Relation Identification: [relation_identification.json](./RQ1/Hadoop/relation_identification.json), each element in the list has four fields. The fields "start_concept", "end_concept" and "relation" mean a relation triple like ("start_concept", "relation", "end_concept"). The field "correct" is annotated by experts and means whether the relation is correct.

Explanation Extraction: [explanation_extraction.json](./RQ1/Hadoop/explanation_extraction.json), each element in the list has three fields. The fields "concept" and "explanation" represent an extracted concept and its explanations. The field "useful" is annotated by expert and means whether the explanations are useful to understand the concept.

#### 2) Comparison with Arora et al.’s Approach.

Arora et al.’s approach extracts glossary terms and their related terms (i.e., the terms that belong to the same categories), but does not identify concept aliases or relations. Therefore, we can only compare the accuracy of the extraction of glossary terms with the approach. For each target domain we use the same sampling method to randomly select 384 sentences from the corpus of technical documents and ask the experts to annotate the glossary terms that are included in these sentences. For each sentence two experts independently identify the glossary terms in it and their agreement on each identified term is checked. When there is disagreement on an identified term, the third expert gives an additional judgement. These identified terms are used as the golden set. We implement Arora et al.’s approach and use the implementation to extract glossary terms from the corpus of each domain. We then identify the extracted terms that are included in the sampled sentences and treat these terms as the result set of the approach. The result set of our approach is produced in a similar way. Based on the result sets of the two approaches and the golden set, we calculate the precision, recall, and F1-measure (the harmonic mean of precision and recall) of glossary term extraction for the two approaches.

The annotation results are shown in following files:

Deep Learning: [comparison.csv](./RQ1/DeepLearning/comparison.csv)<br>
Hadoop: [comparison.csv](./RQ1/Hadoop/comparison.csv)<br>
There are five columns in the csv files. The field "sentence" means the selected sentences for this evalution. The field "our approach" means the concepts extracted by our approach (each concept is an alias set surrouded by "<" and ">"). The field "Arore's approach" means the concepts extracted by Arore's approach. The field "human annotation" means the concepts labelled by experts.

### RQ2: How does the extracted domain glossary fuse the knowledge from different projects and documents? How does the extracted concepts complement general knowledge base such as WikiPedia?

We further analyze the complementarity with Wikipedia based on the 384 terms sampled in each domain for the evaluation of term extraction (see Section 4.3). For each term confirmed in RQ1, we manually examine Wikipedia to check whether it is included with the same meaning.

The checking result are shown in following files:

Deep Learning: [Wikipedia.txt](./RQ2/DeepLearning_Wikipedia.txt)<br>
Hadoop: [Wikipedia.txt](./RQ2/Hadoop_Wikipedia.txt)<br>
Each line in the txt files means a record, each record represent a term labelled "correct" and whether it is included in Wikipedia. If the last word is "T", the term is in Wikipedia, if "F", not in Wikipedia.


### RQ3: Can the extracted domain glossary help developers to obtain the required knowledge?

We design an experiment to investigate whether the extracted domain glossary can help to answer real-world developer queries. We select 12 questions from the top 100 voted Stack Overflow questions with the tag "deep learning" or "Hadoop". These questions are related to domain concepts and can be answered by the documents.

The selected queries, search results before and after query expansion, annotation results are shown in following files:

Deep Learning: [usefulness.csv](./DeepLearning_usefulness.csv)<br>
Hadoop: [usefulness.csv](./Hadoop_usefulness.csv)<br>
There are four columns in the csv files. The field "query" means the select queries for this evaluatoin. The field "before or after expansion" means whether the corresponding queries are expanded for searching. The field  "sentence" means the sentences of the search result. The field "is related" are annotated by experts and mean whether the sentences are related to the corresponding queries.



