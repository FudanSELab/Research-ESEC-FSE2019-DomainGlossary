## Domain-specific Glossary Construction

  We post our data of empirical study in this page.

  The two subject domains that we choose for the study represent two kinds of technical domains. Deep learning domain includes software libraries that are written in different languages and provide similar functionalities for the development of deep learning applications. Hadoop domain is a software ecosystem that consists of interdependent software systems. 

  The subject projects we choose for the deep learning domain are three popular deep learning libraries: Deeplearning4j 1.0.0-
beta3, Tensorflow 1.12, PyTorch 1.0.0. Among them, Deeplearning4j is written in Java, Tensorflow and PyTorch are written in Python. The subject projects we choose for the Hadoop domain are Hadoop 2.9.2, HBase 2.1.0, Hive 2.3.4. Hadoop is a distributed data storage and processing framework based on the MapReduce model. HBase is a distributed database that runs on top of HDFS (Hadoop Distributed File System) and provides Bigtable-like capabilities for Hadoop. Hive provides a SQL-like interface to query data stored in various databases and file systems that integrate with Hadoop. All these three projects are written in Java.

### RQ1  How accurate are the extracted domain concepts, relations, and explanations? Can the approach outperform existing approaches for domain glossary extraction?

There are two part of this RQ:

1) Accuracy of key steps of our approach.

We evaluate the accuracy of term extraction, alias merging, relation identification, explanation extraction, for each step we select 384 samples. We invite three master students who are experts in the domain to examine the accuracy. For each examination two experts independently make the decision based on the related contexts and their agreement on the decision is checked. When there is disagreement on a decision, the third expert gives an additional judgement.

The annotation results are shown in following files:

[deep learning term extraction annotation](https://help.github.com/categories/github-pages-basics/)
[deep learning term extraction arbitration]
[deep learning alias merging annotation](https://help.github.com/categories/github-pages-basics/)
[deep learning alias merging arbitration]
[deep learning relation identifiction annotation](https://help.github.com/categories/github-pages-basics/)
[deep learning relation identifiction arbitration]
[deep learning explanation extraction annotation](https://help.github.com/categories/github-pages-basics/)
[deep learning explanation extraction arbitration]
[hadoop term extraction annotation](https://help.github.com/categories/github-pages-basics/)
[hadoop term extraction arbitration]
[hadoop alias merging annotation](https://help.github.com/categories/github-pages-basics/)
[hadoop alias merging arbitration]
[hadoop relation identifiction annotation](https://help.github.com/categories/github-pages-basics/)
[hadoop relation identifiction arbitration]
[hadoop explanation extraction annotation](https://help.github.com/categories/github-pages-basics/)
[hadoop explanation extraction arbitration]

2) Comparison with Arora et al.’s Approach.

### RQ2 How does the extracted domain glossary fuse the knowledge from different projects and documents? How does the extracted concepts complement general knowledge base such as WikiPedia?

### RQ3 Can the extracted domain glossary help developers to obtain the required knowledge?



