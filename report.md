### Technical Report On A Brief Performance Comparison Between A Metric Search Tree and Brute Force Verification 
### Abstract 

Graph Similarity Search (GSS) plays a pivotal role in domains such as molecular and protein similarity search where the inherent structure of the problem can be represented and processed as a graph. However, the common metric employed in GSS, the Graph Edit Distance (GED), can be computationally challenging to calculate as it requires an exponential amount of time. To overcome this, a common strategy is the utilization of upper and lower bounds of GED in a Binary Metric Tree search. Our experiments contrast this approach with a brute force verification method to evaluate efficiency and accuracy. Our results indicate that the Cascading Metric Tree (CMT) used for the search does not outperform brute force verification in most cases, suggesting that even the upper and lower bounds of GED are computationally intensive to compute compared to GED verification.

### Introduction

Graph Similarity Search (GSS) algorithm is widely used in quantifying similarity in proteomics and molecular analysis requiring a comparison of large graph-structured databases [1]. The most representative metric in similarity search is the Graph Edit Distance (GED), a measure signifying the minimum number of graph-editing steps to transform one graph into another. These steps include insertion, deletion, or substitution of nodes and edges. Despite its ability to provide an optimal measure of similarity, GED is computationally expensive, requiring the computation of all possible transformation sequences resulting in an NP-Hard problem [1]. 

A common approach to circumvent this issue involves the use of Metric Search Trees - data structures for efficiently querying distances in space. Among these trees, the Cascading Metric Tree (CMT) has shown to increase similarity searches’ effectiveness in other metrics, such as Euclidean distance and Kendall-Tau distances [2][3]. The CMT offers the advantage of using the upper and lower bounds of GED during a binary metric tree search. This study compares the CMT approach with a brute force (BF) method that verifies whether the GED is lower than a given threshold [1]. Our study aims to provide insights into which method yields improved performance in processing GED-based searches.

### Methods

Our study implements a binary tree based on exact distances. During a search, upper and lower bounds (UBLB) of Graph Edit Distance (GED) are used to determine whether an object is added to the 'confirmed' or 'suspected' set. If the upper bound is lower than the given threshold, it is confirmed and added to the 'confirmed' set. If the lower bound is lower than the threshold, it is flagged as 'suspected.' As the UBLB may lead to false positives, namely 'suspected' objects that do not meet the threshold, a brute force verification step is implemented. This step checks whether the actual calculated GED is indeed lower than the given threshold.

For the evaluation of algorithms, data on the graph were extracted from PubChem. A sequence of searches based on both the CMT structure and the brute force verification algorithm were executed on this extracted set of graph data [6]. The time taken and results yielded by both methods were collected and compared to investigate the efficiency and output accuracy of each.

# Graph Similarity Search: Performance Evaluation of the Cascading Metric Tree for Graph Edit Distance Verification

# Introduction
Graph Similarity Search (GSS) has made significant contributions to disciplines involving structural data representation, including molecular biology, social network analysis, and image processing. Graph Edit Distance (GED), a prevalent measure in GSS, quantifies the dissimilarity between two graphs based on the minimal cost of transforming one graph into another [1]. Despite its utility, the exponential time complexity of GED computation poses significant performance challenges. Several attempts have been made to speed up GED verification, using both brute force methodologies and tree structures.

This report assesses the performance of the Cascading Metric Tree (CMT), a metric search tree specifically designed to improve similarity search in various metrics [2], [3]. We investigate whether using CMT to perform GED searches is more efficient than a brute force (BF) verification process. We discuss the findings, present our conclusions, and identify future areas of inquiry.

# Methodology
In building our CMT, we began by constructing the tree based on exact distances to ensure the most accurate representation. We then used upper and lower bounds (UBLB) of GED during the binary search process in the metric tree. If the upper bounds were lower than the threshold distance, the corresponding graph was added to the confirmed set. If the lower bounds were lower than the threshold but the upper bounds were not, the graph was added to a suspected set. Finally, a BF verification process was applied to the suspected set to filter out false positives resulting from the UBLB search.

Our empirical evaluation was based on graph data derived from PubChem, a database of biological activities of small molecules. We then compared the performance of the CMT and BF methods. Our performance metrics include computation speed and accuracy in determining the set of graphs within the given threshold distance from the query graph.

# Results and Discussion
Our results indicate that the CMT method does not consistently outperform the BF verification. In fact, we observed that in many instances, CMT had a slower processing time compared to the brute force method. 

Given the exponential time complexity of GED computation, our initial hypothesis was that using the more efficient CMT structure would lead to superior search performance. However, we found that even the computation of the upper and lower bounds of GED access times remained quite high. This limitation often led to the CMT process being slower than the simple brute force verification approach.

# Conclusion
Our findings suggest that while metric search trees, particularly the CMT, can improve similarity searches in several results such as the Euclidean distance and Kendall-Tau distances, this is not the case for GED. The exponential time complexity of determining GED poses significant performance challenges that applying the CMT does not sufficiently mitigate, compared to brute force verification approaches. 

# Limitations and Future Work
The presented study has several limitations which warrant consideration. These limitations could potentially affect the conclusions made and constitute areas requiring further research:

1. **Tuning Hyperparameters**: Different hyperparameters may yield different results, including the iteration values for the GED upper and lower bounds algorithm. Thus, optimizing these parameters could facilitate more accurate and efficient outcomes.
  
2. **Limited Search Space**: Our experiments used a particular search space bound by the parameters of the PubChem graphs. Testing the algorithms in various domains may yield different results, potentially highlighting circumstances where CMT outperforms BF.
   
3. **Graph Complexity**: We observed better relative performance in some cases (need more tests to confirm) for CMT when graph size decreased and dataset size increased. However, our dataset contains a limited number of small molecules, exposing a "blank space" in our experimentation. Further study should examine this space for potential conditions where CMT provides superior efficiency.
   
4. **Performance Optimization**: We did not iterate any performance optimization or tuning on our CMT implementation that could potentially improve the overall performance.

In summary, while our initial results are not promising for the use of CMT in speeding up GED verification, further studies in different scenarios and with optimized hyperparameters may still yield better performance outcomes. The high computational complexity of GED remains a significant challenge, and more research is required to devise efficient similarity search methodologies.

### ACKNOWLEDGEMENT 
Part of the computation for this work was performed on
the high-performance computing infrastructure provided
by Research Support Solutions and in part by the National
Science Foundation under grant number CNS-1429294 at
the University of Missouri, Columbia MO.
DOI: https://doi.org/10.32469/10355/69802
OpenAI ChatGPT is used as an aid in this project such as
brainstorming, language refining, etc. This tech report is 
produced by ChatGPT based on an author-written outline and proofread by 
the author. 


# References
[1] L. Chang, X. Feng, X. Lin, L. Qin, W. Zhang, and D. Ouyang, ‘Speeding up ged verification for graph similarity search’, in 2020 IEEE 36th International Conference on Data Engineering (ICDE), Apr. 2020, pp. 793–804. doi: 10.1109/ICDE48307.2020.00074.

[2] W. Guo and J. Uhlmann, ‘Metric search for rank list compatibility matching with applications’. arXiv, Aug. 10, 2023. doi: 10.48550/arXiv.2303.11174.

[3] J. Uhlmann and M. R. Zuniga, ‘The cascading metric tree’. arXiv, Dec. 20, 2021. doi: 10.48550/arXiv.2112.10900.

[4] D. B. Blumenthal, S. Bougleux, J. Gamper, and L. Brun, ‘Gedlib: a c++ library for graph edit distance computation’, in Graph-Based Representations in Pattern Recognition, D. Conte, J.-Y. Ramel, and P. Foggia, Eds., in Lecture Notes in Computer Science. Cham: Springer International Publishing, 2019, pp. 14–24. doi: 10.1007/978-3-030-20081-7_2.

[5] Z. Abu-Aisheh, R. Raveaux, and J.-Y. Ramel, ‘A graph database repository and performance evaluation metrics for graph edit distance’, in Graph-Based Representations in Pattern Recognition, C.-L. Liu, B. Luo, W. G. Kropatsch, and J. Cheng, Eds., in Lecture Notes in Computer Science. Cham: Springer International Publishing, 2015, pp. 138–147. doi: 10.1007/978-3-319-18224-7_14.

[6] K. Riesen, A. Fischer, and H. Bunke, ‘Computing upper and lower bounds of graph edit distance in cubic time’, in Artificial Neural Networks in Pattern Recognition, N. El Gayar, F. Schwenker, and C. Suen, Eds., Cham: Springer International Publishing, 2014, pp. 129–140. doi: 10.1007/978-3-319-11656-3_12.



