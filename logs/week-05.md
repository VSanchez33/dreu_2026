# Week 5

**Dates:** 07-13 to 07-19

## Goals

- Determine why previous DQC1-pre clustering results had the same score in testing. 
- Implement PCA to enable faster and more extensive testing on more complex datasets.
- Test different rotation values using RXRYRZ feature map and evaluate their effect on clustering performance.
- Test different distance metrics for the DQC1 clustering pipeline and evaluate their effect on clustering performance.

## Approach and Implementation

I used knowledge from my previous initial-point experiments to investigate why DQC1-pre produced identical clustering scores across different feature maps. I hypothesized that DQC1-pre clustering depends heavily on the number and selection of the initial points. To investigate this, I performed a small parameter sweep on the Moons dataset by varying the number of initial points. I also tested different dataset sizes to analyze how dataset size affects the DQC1-pre clustering scores. 

Ramin suggested implementing PCA to make testing on more complex and higher-dimensional datasets faster. He provided code from his previous work that used PCA for dimensionality reduction. I adapted this code and implemented the same PCA approach in the current DQC1 pipeline.

I tested different rotation scaling values in the RXRYRZ feature map to evaluate their effect on clustering performance. I performed a limited sweep as an initial comparison to determine whether rotation values meaningfully affected performance and whether this direction was worth investigating further. 

I chose different distance metrics for the DQC1 clustering pipeline that Ramin had suggested to evaluate a classical part of the DQC1 clustering pipeline. These distance metrics were squared Euclidean (what was used previously), Wasserstein, Manhattan, and Cosine. This is to be run on the Moons dataset. 

## Results

- DQC1-pre produced the same scores across feature-map choices once the number of initial points reached three.
- The DQC1-pre scores obtained with three initial points were also higher than those obtained with two initial points. Based on these preliminary results, using three initial points appears to be a reasonable choice for future testing.
- N_INIT values of three and four produced very similar results across the dataset-size sweep. Small differences appeared at dataset sizes of 150 and 500.
- The tested RXRYRZ rotation values had a substantial effect on clustering performance.
- Even the limited rotation sweep suggested that the best rotation values may depend on the dataset.
- On the Moons dataset, the combination X=1.0, Y=1.0, and Z=1.0 produced a large increase in ARI compared with the reported paper result from Ramin. 

## Notes

- I implemented PCA but did not have enough time to test it on the more complex datasets. I will need to check the PCA implementation before using it in additional complex-dataset experiments.
- Based on the strong effect of the rotation values, I plan to shift the focus of the research from automating every component of the DQC1 clustering pipeline to learning adaptive rotation values for the RXRYRZ feature map. 
- A robust representation of each input dataset will be needed before training a model to recommend rotation values. 
- When testing n possible values independently for each of the X, Y, and Z rotations, a complete search requires n^3 DQC1 clustering runs. This quickly becomes computationally expensive as the number of candidate rotation values increases.
- I found a paper by Tung et al. (2026) that uses a dataset-representation method that may be useful for this project. However, the method appears to rely on labeled datasets, so it may need to be adapted for unlabeled, unsupervised datasets.
- After selecting a robust dataset-representation method, I will investigate how to train a machine-learning model to recommend RXRYRZ rotation values for an unseen dataset and how it fits into the DQC1 clustering pipeline. 
- I created most of the code needed for the distance-metric experiments but did not finish running the tests. I plan to complete these experiments before the beginning of next week. 