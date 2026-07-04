**Student:** Vincent Sanchez  
**Mentor:** Dr. Samee Khan/Ramin Salehi

# Week 2

**Dates:** 06-22 to 06-28

## Goals

- Present the DQC1 clustering pipeline to my mentor and replicate the results from the paper. 
- Begin testing different components of the DQC1 clustering pipeline.
- Share findings and discuss potential improvements. 

## Approach and Implementation

I presented the DQC1 clustering pipeline to my mentor and was able to accurately explain the major components of the pipeline and understand where DQC1 is used. I also replicated the best clustering results reported in the paper. 

I began testing different elements of the pipeline. These included the number of initial clusters, the number of initial points in each cluster, the feature maps used in the paper, and the number of layers used in the feature maps.  

For each experiment, I kept the same base parameters whenever possible to ensure consitency across tests. This allowed me to compare how individual changes affected the DQC1-pre and DQC1-full pipelines.

## Results

- Feature map choice appeared to affect only the DQC1-full pipeline, where the entropy-based reduction step is introduced. 
- The optimal number of initial clusters seems to be around 8 to 10. 
- The number of initial points in each cluster seemed to have little impact on the final clustering results. 
- The number of feature map layers did not affect the final results in the test. 
- DQC1-pre ARI and NMI scores remained constant across different feature maps tested, which is unexpected. 

## Notes

The lack of change in DQC1-pre ARI and NMI scores across different feature maps was unexpected. This suggests that the DQC1-pre stage may not be very sensitive to feature map choice, or that another part of the implementation may be limiting the effect of the feature maps before the reduction step. 