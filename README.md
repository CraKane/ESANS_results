# ESANS_results

### 0. separate impacts of interpolation on simple negatives and interpolation on hard negatives(Reviewer1 A6)
| Method   |      Time Costs      |
|----------|:-------------:|
| UNS |  xxx | 
| PNS |    xxx   |
| debiased MNS | xxx | 
| MixGCF | xxx | 
| FairNeg | xxx | 
| Ada - $\tau$ | xxx | 
| ESANS(ours) | xxx | 



### 1. Training Cost for ESANS and baseline methods on #A2 dataset(Reviewer1 A1, Reviewer5 A2)
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

### 2. Modality ablation study on #A2 dataset(Reviewer5 A4)

| Methods   |      Recall@50      | Recall@200      |
|----------|:-------------:|:-------------:|
| Tree modals |  xxx |  xxx | 
| w/o visual modal |    xxx   | xxx | 
| w/o textual modal | xxx |  xxx | 
| w/o behavior-based modal | xxx |  xxx |

### 3. Hyperparameter experiments for $\lambda$(Reviewer3 A1, Reviewer4 A2, Reviewer5 A8)

| hyperparameter setting   | #A1   |      #A2      | #A3      | #A4      |
|----------|:-------------:|:-------------:|:-------------:|:-------------:|
| $\lambda$=0.5 |  xxx |  xxx |   xxx |   xxx | 
| $\lambda$=0.3 |    xxx   | xxx |   xxx |   xxx | 
| $\lambda$=0.1 | xxx |  xxx |   xxx |   xxx | 
| $\lambda$=-0.1 | xxx |  xxx |  xxx |   xxx | 
| $\lambda$=-0.3 | xxx |  xxx |  xxx |   xxx | 

Most of the hyperparameter experiments have been conducted in our pape, but we feal sorry for omiting the hyperparameter experiment for $\lambda$ . According to our experiments, 


### 4. Online environment description(Reviewer5 A9)
Since ESANS is a EBR-based model, the deploy of this model is similar to classical two-tower model. We select the country of #A2 to validate our model and conduct our online experiment from September 13 to 19, 2024. Based on our experience, the increase in traffic during the experiment is highly reliable.


### 5. How to avoid the size of each primary cluster not less than $m_o$(Reviewer5 A16)
The classical method to avoid codebook collapse is to use k-means method to set proper initialization parameters. We use this method in our model and it really works. You can refer to [1] for more details.

### 6. Discussions for Equation 12(Reviewer5 A17)
Suppose we have $m_c^v$ negatives, each time we randomly select k negatives and generate a virtual negative sample with Equation 11. k range from 2 to $m_o$. In this way, we can get

$m_c^v$ = 2+3+...+ $m_o$-1 + $m_o$ =($m_o$+2)($m_o$-1)/2

We have re-read the description of our paper and realize that the writing was not as clear as it should be. We sincerely apologize for this and hope our additional description can clarify our idea for you.


### 7. Supplementary experiments for different numbers of negative samples on #A2 dataset(Reviewer5 A20)

| Negative scales   |      Recall@50      | Recall@200      |
|----------|:-------------:|:-------------:|
| $m_c$=2, $m_o$=5 |  xxx |  xxx | 
| $m_c$=1, $m_o$=5 |    xxx   | xxx | 
| $m_c$=2, $m_o$=4 | xxx |  xxx | 
| $m_c$=3, $m_o$=5 | xxx |  xxx |
| $m_c$=2, $m_o$=6 | xxx |  xxx |



[1].Adrian Łańcucki, Jan Chorowski, Guillaume Sanchez, Ricard Marxer, Nanxin Chen, Hans JGA Dolfing, Sameer Khurana, Tanel Alumäe, and Antoine Laurent.Robust training of vector quantized bottleneck models.In IJCNN, pages 1–7. IEEE, 2020.
