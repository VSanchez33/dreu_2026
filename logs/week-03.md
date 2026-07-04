**Student:** Vincent Sanchez  
**Mentor:** Dr. Samee Khan/Ramin Salehi

# Week 3

**Dates:** 06-29 to 07-05

## Goals

- Layer multiple feature maps and study their combined effect on DQC1 clustering. 
- Research and analyze the impact of new feature maps on the DQC1 clustering. 
- Research and analyze the impact of new kernels on the DQC1 clustering. 

## Approach and Implementation

I tested combinations of feature maps by using each of the five original feature maps as a base and layering it with each of the other feature maps. All tests were performed using the same base parameters to ensure consistency, and the moons dataset was used for these experiments. 

I also implemented and tested several new feature maps. This included modifying one of the paper’s Pauli-Z feature maps into a Pauli-XZ feature map, as well as implementing an IQP-style feature map, a Hamiltonian feature map, and a random kitchen sink feature map. These feature maps were tested across all datasets. 

In addition to feature map testing, I implemented several new kernels for the DQC1 clustering pipeline, including two kernels that were previously tested by Ramin. I also tested an eigenvalue-based kernel, a commutator kernel, and a subsystem density kernel. For the new kernels, I tested two different gamma values to observe how the scaling parameter affected clustering performance. 

## Results

- Layering feature maps produced varying effects on DQC1 clustering performance, with some combinations improving results. 
- The combination of the Pauli and RXRYRZ feature maps showed a significant improvement in DQC1-full performance compared to the Z-diagonal baseline. 
- Feature maps with similar initial gate structures produced very similar scores, while the entangling portions of the circuits appeared to have less impact. 
- The random kitchen sink feature map had the best overall average performance across all datasets compared to the other new feature maps tested. 
- The new kernels appeared to have less impact on DQC1 clustering performance overall, but some produced promising results. 
- The commutator kernel with a gamma value of 0.5 significantly improved clustering performance on the moons dataset compared to the paper’s reported results. 

## Notes

- The DQC1-pre results remained the same across the new feature map and new kernel tests. This behavior is unexpected and suggests that the preclustering step may be dominating the DQC1-pre scores more strongly than the feature map or kernel choice. This is further supported by the fact that DQC1-pre scores changed when testing different numbers of initial clusters and initial points, but not when changing feature maps or kernels. 
- I also verified that the kernels used in the DQC1-pre step were actually different. This suggests that the identical DQC1-pre scores were not simply caused by the kernels failing to change, but may instead be due to the structure or sensitivity of the preclustering step itself. 
- Next steps include trying the DQC1 clustering on more complex datasets and exploring the impact of different distances(not Euclidean).