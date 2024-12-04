# ESANS_results

### Training Cost for ESANS and baseline methods on #A2：
| Method   |      Time Costs      |
|----------|:-------------:|
| UNS |  xxx | 
| PNS |    xxx   |
| debiased MNS | xxx | 
| MixGCF | xxx | 
| FairNeg | xxx | 
| Ada-$\tau$ | xxx | 
| ESANS(ours) | xxx | 

Time Costs Analysis:

Our method demonstrates a competitive advantage in terms of time efficiency compared to the latest approaches since we didn't add specific auxiliary network to select negatives in training process and the theoretical computational complexity is almost equivalent to debiased MNS. The EDIS module slightly improve the time cost only on the back propagation since the interpolation is conducted within the low-dimensional embedding space after the forward pass MLPs.
