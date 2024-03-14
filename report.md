# Efficient Search in Graph Edit Distance: Metric Search Trees vs. Brute Force Verification

## Introduction
Graph similarity search (GSS) plays a key role in domains such as molecular and protein similarity search[1]. Specifically, Graph Edit Distance (GED)--the measure of similarity based on the steps required to edit one graph into another--is one of the most commonly used metrics in GSS. However, the computation of exact GED traditionally requires exponential time, which can slow down the search process considerably[1]. 

Researchers have proposed various methodologies to speed up the GED computation process. One promising approach involves augmenting similarity searches with metric search trees, such as the Cascading Metric Tree (CMT)[3]. CMT has been shown to enhance similarity searches using different metrics, like Euclidean distance and Kendall-Tau distances[2][3]. The other popular approach is to use Brute Force (BF) search in which the computation of exact GED is replaced by a Verification process: a procedure to verify if the GED of two graphs is lower than a given threshold[1]. 

In this study, we aim to investigate whether adapting the CMT for use with GED (using Upper and Lower Bounds of GED in place of exact GED) can outperform the simple brute force verification relayed in [1]. Our results suggest that, contrary to our initial hypothesis, CMT does not routinely outperform brute force verification strategy in most contexts.

## Methodology

Our experimentation involved building trees based on exact distances and using the Upper and Lower Bounds (UBLB) during the binary metric tree searches. In our approach:

- If the upper bounds are lower than the threshold, the corresponding graph is added to a 'confirmed set'.
- If the lower bounds are lower than the threshold, the graph is added to a second 'suspected set'.
- A brute force verification step then examines each member of the suspected set to filter out any false positives from the UBLB search.

The algorithm was tested on graph data derived from PubChem and the performance of CMT was compared to that of brute force verification.

## Results and Discussion
![Figure 1]
Results indicate that CMT does not routinely outperform brute force verification. In fact, in many cases, CMT significantly lags behind brute force in terms of speed. One possible explanation for this could be the complexity of computing not just the GED, but its Upper and Lower Bounds. Since both benchmarks pose their unique computational challenges, this surprising finding underlines the need for continuous innovation in methodologies to speed up GED computation. 

## Future Work and Limitations

Our study has several limitations which indicate possible directions for future work. These include:

1. **Hyper-parameters**: Various hyper-parameters, like the iterations of the UBLB algorithm, have a bearing on the results. Future research could fine-tune these to yield more optimized results.
2. **Search Space**: Our research was conducted in a limited search space. Investigations in other search scenarios might yield different findings.
3. **Data Sampling**: The graph data used was only sourced from PubChem, which could introduce sample bias. Future studies using data from varying sources might enhance the generalizability. 
4. **Small Molecules**: Our dataset lacked a significant number of small molecules. Given the positive correlation between CMT performance and smaller graph size, this represents a potential direction for future work.
5. **Optimization**: Our implementation of CMT was not fully optimized. Enhancing the implementation might improve its performance.

## Conclusion

This study investigated the performance of Cascading Metric Trees in GED computation for graph similarity search in comparison to brute force verification. Surprisingly, our results showed that despite its proven efficacy in other metrics, CMT did not routinely outperform brute force verification in computing GED. These findings highlight the need for continued exploration of methods for speeding up GED computation and verification, with a particular focus on optimizing the computation of GED upper and lower bounds and investigating the performance of these methods on a wider range of datasets and search spaces.


## ACKNOWLEDGEMENT 
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


## References
[1] L. Chang, X. Feng, X. Lin, L. Qin, W. Zhang, and D. Ouyang, ‘Speeding up ged verification for graph similarity search’, in 2020 IEEE 36th International Conference on Data Engineering (ICDE), Apr. 2020, pp. 793–804. doi: 10.1109/ICDE48307.2020.00074.

[2] W. Guo and J. Uhlmann, ‘Metric search for rank list compatibility matching with applications’. arXiv, Aug. 10, 2023. doi: 10.48550/arXiv.2303.11174.

[3] J. Uhlmann and M. R. Zuniga, ‘The cascading metric tree’. arXiv, Dec. 20, 2021. doi: 10.48550/arXiv.2112.10900.

[4] D. B. Blumenthal, S. Bougleux, J. Gamper, and L. Brun, ‘Gedlib: a c++ library for graph edit distance computation’, in Graph-Based Representations in Pattern Recognition, D. Conte, J.-Y. Ramel, and P. Foggia, Eds., in Lecture Notes in Computer Science. Cham: Springer International Publishing, 2019, pp. 14–24. doi: 10.1007/978-3-030-20081-7_2.

[5] Z. Abu-Aisheh, R. Raveaux, and J.-Y. Ramel, ‘A graph database repository and performance evaluation metrics for graph edit distance’, in Graph-Based Representations in Pattern Recognition, C.-L. Liu, B. Luo, W. G. Kropatsch, and J. Cheng, Eds., in Lecture Notes in Computer Science. Cham: Springer International Publishing, 2015, pp. 138–147. doi: 10.1007/978-3-319-18224-7_14.

[6] K. Riesen, A. Fischer, and H. Bunke, ‘Computing upper and lower bounds of graph edit distance in cubic time’, in Artificial Neural Networks in Pattern Recognition, N. El Gayar, F. Schwenker, and C. Suen, Eds., Cham: Springer International Publishing, 2014, pp. 129–140. doi: 10.1007/978-3-319-11656-3_12.



