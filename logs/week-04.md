# Week 4

**Dates:** 07-06 to 07-12

## Goals

- Apply a more statistical approach to the DQC1 clustering analysis. 
- Apply the DQC1 clustering to more complex datasets. 
- Review papers on automated feature map and kernel selection. 
- Implement potential methods for automated feature map and kernel selection. 

## Approach and Implementation

I performed a broader sweep of gamma values for the commutator kernel and analyzed their effect on clustering performance for the moons dataset. The goal was to identify an optimal parameter range and determine whether the sweep could provide a more meaningful basis for future kernel parameter selection.

I also searched for more complex datasets on which to evaluate the DQC1 clustering pipeline. I selected one synthetic dataset, 3D anisotropic blobs, and four real-world datasets: iris, lenses, seeds, and wine. I applied only the preprocessing required by the pipeline, including numerical encoding for the categorical values in the lenses dataset. I then tested the DQC1 clustering pipeline using the five feature maps presented in Ramin’s paper.

I found two papers that propose methods relevant to automated feature map and kernel selection. The first uses unsupervised multiple kernel learning, or UMKL, as described by Zhuang et al. (2011). The second uses the Nyström approximation proposed by Williams and Seeger (2000). I implemented both approaches using multiple candidate kernels and feature maps to investigate whether they could identify a strong combination without exhaustively evaluating every candidate using the true labels. 

## Results

- With the commutator kernel, ARI began to decline steadily once gamma exceeded approximately 0.8 and started to level off near a gamma value of 1.0. This suggests that an intermediate gamma range may provide better clustering performance than larger values. 
- The DQC1 clustering pipeline performed best on the 3D anisotropic blobs dataset. This was consistent with its relatively strong performance on the simpler 2D synthetic datasets. 
- The iris dataset produced relatively strong results across all five feature maps.  
- The seeds dataset performed slightly worse than iris but still produced reasonable results across most feature maps. 
- The wine dataset was substantially more computationally expensive than the other datasets. One feature map experiment ran for approximately five hours before I terminated it. 
- The lenses dataset produced the weakest overall results, with most ARI scores near or below zero. 
- Both automation approaches suggested using the DQC1 based kernel. 

## Notes

- Ramin suggested that the most important next step is to implement PCA to reduce the number of features and enable faster, more extensive testing. 
- The lenses dataset contained significantly fewer samples than the other datasets, which may explain its results being worse. 
- The RXRYRZ feature map outperformed the others on the lenses dataset, but the performance was still suboptimal. This may suggest that datasets with fewer samples may benefit from a feature map with multiple rotation gates for more expressive representations. 
- The Nyström approximation approach used K-means during the selection process. Replacing K-means with DQC1 clustering may be worth testing to see whether it produces better selections for the DQC1 pipeline. 