# ESANS_results


### Training Cost for ESANS and baseline methods on #A2：
| Method   |      Time Costs      |
|----------|:-------------:|
| UNS |  xxx | 
| PNS |    xxx   |
| debiased MNS | xxx | 
| MixGCF | xxx | 
| FairNeg | xxx | 
| Ada - $\tau$ | xxx | 
| ESANS(ours) | xxx | 

Result Analysis:

Our method demonstrates a competitive advantage in terms of time efficiency compared to the latest approaches(FairNeg and Ada - $\tau$) since we didn't add specific auxiliary network to select negatives in training process. As a result, the theoretical computational complexity of ESANS is almost equivalent to the debiased MNS method.It should be noted that it costs a few computational resources during the offline negative sample stitching phase, but the storage resources remains unchanged. Besides, the EDIS module slightly improves the time cost of training process only on the back propagation since the interpolation is conducted within the low-dimensional embedding space after the forward pass MLPs. As for online deployment, ESANS will not incur additional computational overhead compared to classical EBR model.

### Training Cost for ESANS and baseline methods on #A2：
