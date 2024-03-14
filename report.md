## Abstract
This report explores the effectiveness of two graph similarity search (GSS) methods: the cascading metric tree (CMT) and brute force verification in improving graph edit distance search, a popular algorithm used in applications such as protein and molecular similarity search. Our preliminary results indicate that the CMT often underperforms when compared to brute force, being particularly slower in many tested scenarios. The paper discusses these findings, lays down potential limitations and areas of exploration for future work and presents an algorithm overview. The findings of this study can contribute to the body of knowledge on GSS and lend insight into the optimization of graph similarity search processes in real-world applications.

## Introduction
Graph similarity search (GSS) is a tool widely used in several fields, most notably molecular and protein similarity search where the similarity between graphs is computed—a process that aids in identifying remarkable patterns among graphs and detecting graph motifs.. One of the common metrics used in GSS is the Graph Edit Distance (GED), which measures the steps required to edit one graph into another. However, its computational intensity makes it a slow process as it requires exponential time for computation.

To address this concern, various approaches have been proposed to expedite the GED computation process. One of these is the adoption of metric search trees such as Cascading Metric Tree (CMT). CMT has been successful in speeding up similarity searches in other metrics, such as Euclidean distance and Kendall Tau distances. Another approach, Brute Force (BF) search, checks solely for GED verification, that is, it confirms if the GED is below the designated threshold. 

Despite these advancements, more comprehensive comparisons and assessments of these search methods are needed so as to devise the most efficient approach. In light of this, this report investigates the efficiency between CMT and BF in the context of GED computation, exploring whether metric search is more efficient than the brute force verification algorithm for GED search.

## Methodology
The methodology implemented for this study includes: (i) adaptation of the cascading metric tree (CMT) so as to be used with the upper and lower bounds of the Graph Edit Distance (GED); (ii) testing on the Euclidean distance for ease of debug, followed by (iii) incorporation of the GED; (iv) collection of graph data from PubChem; (v) comparison of the performance of CMT and brute-force verification.

In the conducted test, trees were built using exact distances for accuracy. A binary metric search, requiring upper and lower bounds (UBLB), then confirmed or suspected entries depending on the UBLB relationship with the threshold. For any entry where the upper bound was lower than the threshold, it was added to a confirmed set; if the lower bound was less than the threshold but the upper bound wasn't, the entry was added to a 'suspected' set. A brute-force verification, was the final step in the process and cleansed the suspected set for any false positives from the UBLB search. 

This facilitated a direct evaluation of the performance efficiencies of the two methods, with our results suggesting that the CMT, contrary to expectations, is not as efficient as brute force verification in GED similarity search in most cases.

## Efficient Search VS Brute Force Verification Algorithm for Graph-Edit Distance Search: Results and Discussion

The emphasis of our research centered on the comparison between the efficiency of Cascading Metric Tree (CMT) [3] and Brute Force (BF) verification in Graph-Edit Distance (GED) search.

The initial phase of our work entailed building the tree using exact distances. During the binary metric tree searches, the Upper and Lower Bounds (UBLB) of GED [4] [5] [6] were employed. If the upper bounds were detected to be lesser than the threshold, they were incorporated into the confirmed set. Conversely, if the lower bounds fell below the threshold, they were included into the suspected set. In the final stages, a brute force verification was applied to the suspected set to weed out false positives spotted during the UBLB search.

Unlike the exact distance method that computation of the Graph Edit Distance (GED) for every pair and comparison to the threshold, the brute-force verification algorithm applied a two-step process, comprising filtering and verification. During the filtering process, if the lower bound fell below the threshold, the computation proceeded; otherwise, the input was terminated. If the process moved forward, the verification involved calculating if the GED was less than the threshold, focusing solely on the exact GED.

In the CMT method, we didn’t calculate the exact distance due to the complexity involved in its computation. Instead, we used the upper and lower bounds (UBLB) of GED to analyze whether the graphs should be included in the query.

### Results

The results derived from our experiments, however, suggested that CMT underperformed in comparison to brute force verification in most instances. In fact, CMT was notably slower than brute force verification in numerous tested situations. We hypothesize that this discrepancy might be because even the computation of the UBLB of GED seems to be more complex compared to GED verification.

### Discussion and Conclusion

Our experimental results and findings suggest that the CMT does not have a performance advantage over Brute Force verification for Graph Edit Distance search tasks. Surprisingly, in many scenarios we evaluated, the CMT was significantly slower than the brute-force method. This appears to contradict the common perception that optimizing the efficient search mechanism should theoretically improve performance. We believe these results are likely due to the inherent difficulty in computing even the UBLB bounds of the GED, which is itself a complex task. 

The implication of these findings is that when considering and implementing a Graph Similarity Search (GSS) aid such as the GED, algorithmic efficiency and computational resource trade-offs need to be carefully evaluated to avoid suboptimal results.

### Limitations and Future Work

Certain limitations were prevalent in our research. Firstly, the influence of different hyper-parameters on the outcome was not factored in, such as the iterations of the upper and lower bounds algorithm. Embarking upon different hyper-parameters could provide different results. 

Secondly, our algorithm was only tested in a limited search space. We acknowledge that outcomes may differ in different scenarios. Additionally, our graph data was solely sourced from PubChem; as a result, the possibility of dataset bias, which means our results might not reproduce on other datasets, was not ruled out. 

We also observed that with the decrease in size of the graph and the increase in the dataset size, CMT’s performance appeared to be improving. However, our dataset hardly contained small molecules, indicating a “blank space” in our test conditions. 

Furthermore, potential improvements could be made by optimizing our implementation of the CMT, which was not optimized in our experiments. 

In future work, given more computational resources, it would certainly be warranted to run experiments on larger datasets to obtain a more comprehensive view of the performance characteristics of these methods. The exploration of these areas could potentially uncover more advantageous situations where CMT outperforms brute force verification. The further investigation of these directions would be a valuable extension of this work. 

In conclusion, our findings spur a critical reevaluation of the use of optimized search trees for GED-based GSS tasks, opening new avenues for future research to optimize and leverage brute force methods effectively as the computational bounds allow.
