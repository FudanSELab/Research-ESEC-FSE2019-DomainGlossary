## Domain-specific Glossary Construction

We post our data of empirical study in this page.

The two subject domains that we choose for the study represent two kinds of technical domains. Deep learning domain includes software libraries that are written in different languages and provide similar functionalities for the development of deep learning applications. Hadoop domain is a software ecosystem that consists of interdependent software systems. 

The subject projects we choose for the deep learning domain are three popular deep learning libraries: Deeplearning4j 1.0.0-
beta3, Tensorflow 1.12, PyTorch 1.0.0. Among them, Deeplearning4j is written in Java, Tensorflow and PyTorch are written in Python. The subject projects we choose for the Hadoop domain are Hadoop 2.9.2, HBase 2.1.0, Hive 2.3.4. Hadoop is a distributed data storage and processing framework based on the MapReduce model. HBase is a distributed database that runs on top of HDFS (Hadoop Distributed File System) and provides Bigtable-like capabilities for Hadoop. Hive provides a SQL-like interface to query data stored in various databases and file systems that integrate with Hadoop. All these three projects are written in Java.

### RQ1: How accurate are the extracted domain concepts, relations, and explanations? Can the approach outperform existing approaches for domain glossary extraction?

There are two part of this RQ:

#### 1. Accuracy of key steps of our approach.

We evaluate the accuracy of term extraction, alias merging, relation identification, explanation extraction, for each step we select 384 samples. We invite three master students who are experts in the domain to examine the accuracy. For each examination two experts independently make the decision based on the related contexts and their agreement on the decision is checked. When there is disagreement on a decision, the third expert gives an additional judgement.

The annotation results are shown in following files:

[deep learning term extraction annotation](./deeplearning_term_annotation.json)<br>
[deep learning term extraction arbitration](./deeplearning_term_arbitration.json)<br>
[deep learning alias merging annotation](./deeplearning_fusion_annotation.json)<br>
[deep learning alias merging arbitration](./deeplearning_fusion_arbitration.json)<br>
[deep learning relation identifiction annotation](./deeplearning_relation_annotation.json)<br>
[deep learning relation identifiction arbitration](./deeplearning_relation_arbitration.json)<br>
[deep learning explanation extraction annotation](./deeplearning_explanation_annotation.json)<br>
[deep learning explanation extraction arbitration](./deeplearning_explanation_arbitration.json)<br>
[hadoop term extraction annotation](./hadoop_term_annotation.json)<br>
[hadoop term extraction arbitration](./hadoop_term_arbitration.json)<br>
[hadoop alias merging annotation](./hadoop_fusion_annotation.json)<br>
[hadoop alias merging arbitration](./hadoop_fusion_arbitration.json)<br>
[hadoop relation identifiction annotation](./hadoop_relation_annotation.json)<br>
[hadoop relation identifiction arbitration](./hadoop_relation_arbitration.json)<br>
[hadoop explanation extraction annotation](./hadoop_explanation_annotation.json)<br>
[hadoop explanation extraction arbitration](./hadoop_explanation_arbitration.json)<br>

#### 2. Comparison with Arora et al.’s Approach.

Arora et al.’s approach extracts glossary terms and their related terms (i.e., the terms that belong to the same categories), but does not identify concept aliases or relations. Therefore, we can only compare the accuracy of the extraction of glossary terms with the approach. For each target domain we use the same sampling method to randomly select 384 sentences from the corpus of technical documents and ask the experts to annotate the glossary terms that are included in these sentences. For each sentence two experts independently identify the glossary terms in it and their agreement on each identified term is checked. When there is disagreement on an identified term, the third expert gives an additional judgement. These identified terms are used as the golden set. We implement Arora et al.’s approach and use the implementation to extract glossary terms from the corpus of each domain. We then identify the extracted terms that are included in the sampled sentences and treat these terms as the result set of the approach. The result set of our approach is produced in a similar way. Based on the result sets of the two approaches and the golden set, we calculate the precision, recall, and F1-measure (the harmonic mean of precision and recall) of glossary term extraction for the two approaches.

The annotation and arbitration results are shown in following files:

[deep learning](./DL_comparison.csv)<br>
[hadoop](./hadoop_comparison.csv)

### RQ2: How does the extracted domain glossary fuse the knowledge from different projects and documents? How does the extracted concepts complement general knowledge base such as WikiPedia?

We further analyze the complementarity with Wikipedia based on the 384 terms sampled in each domain for the evaluation of term extraction (see Section 4.3). For each term confirmed in RQ1, we manually examine Wikipedia to check whether it is included with the same meaning.

The checking result are shown in following files:

[deep learning](./DL_wikipedia.txt)<br>
[hadoop](./hadoop_wikipedia.txt)

### RQ3: Can the extracted domain glossary help developers to obtain the required knowledge?

We design an experiment to investigate whether the extracted domain glossary can help to answer real-world developer queries. We select 12 questions from the top 100 voted Stack Overflow questions with the tag “deep learning” or “Hadoop”. These questions are related to domain concepts and can be answered by the documents.

The selected queries, search results before and after query expansion, annotation results are shown in following files:

[deep learning](./DL_usefulness.csv)<br>
[hadoop](./hadoop_usefulness.csv)



