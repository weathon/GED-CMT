Abstract:
This work presents a comprehensive evaluation of the Cascading Metric Tree (CMT) search process for algorithmic efficiency in graph similarity searches compared with the brute force verification method. Despite CMT's demonstrated utility in increasing the speed of similarity searches in other metrics, its utility in graph edit distance (GED) searches remains unclear. Herein, we implement the CMT in the GED search process, adapt it to use upper and lower bounds, and compare its performance with a brute force verification process. Our empirical studies suggest that in most of the tested cases, CMT does not outperform the brute force method, with the latter being faster in many situations.

Introduction:
Graph Similarity Search (GSS) is a vital process used in many fields such as molecular and protein similarity search [1]. Traditionally, GED has been the common metric used in GSS. However, its computation-process involves an exponential time, limiting its efficiency in terms of speed [1]. Notably, other metrics such as Euclidean distance and Kendall-Tau distances have been improved with the use of metric search trees, notably the Cascading Metric Tree (CMT) [3]. We hypothesized that the implementation of a metric search tree based on upper and lower bounds of GED's (referred to as UBLB) during a binary metric tree search would enhance the efficiency of graph similarity searches.

Methods:
Our study involved a procedural implementation involving the construction of a CMT based on exact distances, using UBLB during a binary metric tree search process. During the search, if the upper or lower bounds were lower than the determined threshold, the respective metrics were added to the confirmed or suspected set. Finally, the suspected set was processed using a brute force verification to eliminate any false positives from the UBLB search. 

To ascertain CMT’s efficiency, we carried out performance tests on the algorithm using graph data obtained from PubChem. Furthermore, we compared its performance against a brute force verification method. The performance measures adopted involved comparing computational speed, graph size, threshold determination, and dataset sizes [1, 3]. 

Results and Discussion:
Remarkably, our results reveal that in many instances, CMT was much slower than the brute force verification method, countering our initial hypothesis. Our interpretation is that the computational complexity of even the UBLB of GED may be contributing to these observed outcomes. 

Limitation and Future Works:
Our study had some limitations that need to be addressed in future research. These included the limited scope of hyper-parameter choices that can influence results, restricted to a small search space, and potential dataset biases by using only data from PubChem [1, 3]. Moreover, we noted a blank space in our dataset as it contained very few small molecules, an area that should be included in future studies. Notably, optimization of the CMT implementation could also present interesting implications on metric search tree efficiency in the future [3]. 

Conclusion:
Our study lends weight to the application of brute force verification in GED similarity search processes, noting its higher efficiency than the CMT iteration under most circumstances. Future studies need to consider the potential effect of sourcing a more diverse dataset, including various graph sizes and supplementing their analytical processes with a range of hyperparameters. The process also offers the opportunity to explore areas where CMT implementation is more efficient. 

References:
1. L. Chang, X. Feng, X. Lin, L. Qin, W. Zhang, and D. Ouyang, ‘Speeding up ged verification for graph similarity search’, in 2020 IEEE 36th International Conference on Data Engineering (ICDE), Apr. 2020, pp. 793–804. doi: 10.1109/ICDE48307.2020.00074.
2. W. Guo and J. Uhlmann, ‘Metric search for rank list compatibility matching with applications’. arXiv, Aug. 10, 2023. doi: 10.48550/arXiv.2303.11174.
3. J. Uhlmann and M. R. Zuniga, ‘The cascading metric tree’. arXiv, Dec. 20, 2021. doi: 10.48550/arXiv.2112.10900.
