![image](https://github.com/user-attachments/assets/d09ea86c-8cf2-475d-8866-8608514e2a62)# ESANS_results

### 1. separate impacts of interpolation on simple negatives and interpolation on hard negatives(Reviewer1 A6)
| Methods   |      Recall@50      | Recall@200      |
|----------|:-------------:|:-------------:|
|  ESANS |  xxx |  xxx | 
| w/o simple interpolation |    xxx   | xxx | 
| w/o hard interpolation | xxx |  xxx | 


### 2. Training Cost for ESANS and baseline methods on #A2 dataset(Reviewer1 A1, Reviewer5 A2)
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

### 3. Modality ablation study on #A2 dataset(Reviewer5 A4)

| Methods   |      Recall@50      | Recall@200      |
|----------|:-------------:|:-------------:|
|  ESANS |  xxx |  xxx | 
| w/o visual modal |    xxx   | xxx | 
| w/o textual modal | xxx |  xxx | 
| w/o behavior-based modal | xxx |  xxx |

### 4. Hyperparameter experiments for $\lambda$(Reviewer3 A1, Reviewer4 A2, Reviewer5 A8)

| hyperparameter setting   | #A1   |      #A2      | #A3      | #A4      |
|----------|:-------------:|:-------------:|:-------------:|:-------------:|
| $\lambda$=0.5 |  xxx |  xxx |   xxx |   xxx | 
| $\lambda$=0.3 |    xxx   | xxx |   xxx |   xxx | 
| $\lambda$=0.1 | xxx |  xxx |   xxx |   xxx | 
| $\lambda$=-0.1 | xxx |  xxx |  xxx |   xxx | 
| $\lambda$=-0.3 | xxx |  xxx |  xxx |   xxx | 

Most of the hyperparameter experiments have been conducted in our pape, but we feal sorry for omiting the hyperparameter experiment for $\lambda$ . According to our experiments, 


### 5. Online environment description(Reviewer5 A9)
Since ESANS is a EBR-based model, the deploy of this model is similar to classical two-tower model. We select the country of #A2 to validate our model and conduct our online experiment from September 13 to 19, 2024. Based on our experience, the increase in traffic during the experiment is highly reliable.


### 6. How to avoid the size of each primary cluster not less than $m_o$(Reviewer5 A16)
The classical method to avoid codebook collapse is to use k-means method to set proper initialization parameters. We use this method in our model and it really works. You can refer to [1] for more details.

### 7. Discussions for Equation 12(Reviewer5 A17)
We have re-read the description of our paper and realize that the writing was not as clear as it should be. We sincerely apologize for this and hope our additional description can clarify our idea for you.

Suppose we have $m_c^v$ negatives, each time we randomly select k negatives and generate a virtual negative sample with Equation 11. k range from 2 to $m_o$. In this way, we can get

$m_c^v$ = 2+3+...+ $m_o$-1 + $m_o$ =($m_o$+2)($m_o$-1)/2


### 8. Supplementary experiments for different numbers of negative samples on #A2 dataset(Reviewer5 A20)

|Negative scales|Recall@50|Recall@200|
|-|:-:|:-:|
|$m_c$=2, $m_o$=5|0.3887|0|
|$m_c$=2, $m_o$=4|0.3875|0.6197|
|$m_c$=2, $m_o$=6|0.3899|0.6232|
|$m_c$=1, $m_o$=5|0.3793|0.6164|
|$m_c$=3, $m_o$=5|0.3930|0.6241|


Recall@50
|Method|Amazon R@50|Amazon R@200|Pixel R@50|Pixel R@100|#A1 R@50|#A1 R@200|#A2 R@50|#A2 R@100|#A3 R@50|#A3 R@100|#A4 R@50|#A4 R@100|
|-|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|FairNeg|0.1798 $\pm$ 0.0034|0.4705|0.0836|0.1782|0.4790|0.6688|0.3669|0.6052|0.4043|0.6687|0.3983|0.6501|
|Ada - $\tau$|0.2018|0.4873|0.0763|0.1684|0.4694|0.6757|0.3538|0.5883|0.4097|0.6625|0.4046|0.6437|
|ESANS|0.2135|0.4948|0.0908|0.1828|0.4862|0.6918|0.3887|0.6216|0.4176|0.6732|0.4182|0.6609|



Recall@50
|Dataset|FairNeg_avg|FairNeg_std|Ada - $\tau$ _avg|Ada - $\tau$ _std|ESANS_avg|ESANS_std|
|-|:-:|:-:|:-:|:-:|:-:|:-:|
|Amazon R@50|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|Amazon R@200|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|Pixel R@50|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|Pixel R@200|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A1 R@50|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A1 R@200|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A2 R@50|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A2 R@200|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A3 R@50|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A3 R@200|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A4 R@50|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|
|#A4 R@200|0.1798 $\pm$ 0.0034|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|0 $\pm$ 0|


Recall@50
|Method|Amazon R@50|Amazon R@200|Pixel R@50|Pixel R@100|#A1 R@50|#A1 R@200|#A2 R@50|#A2 R@100|#A3 R@50|#A3 R@100|#A4 R@50|#A4 R@100|
|-|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|ESANS vs FairNeg|0.1798 $\pm$ 0.0034|0.4705|0.0836|0.1782|0.4790|0.6688|0.3669|0.6052|0.4043|0.6687|0.3983|0.6501|
|ESANS vs Ada - $\tau$|0.2018|0.4873|0.0763|0.1684|0.4694|0.6757|0.3538|0.5883|0.4097|0.6625|0.4046|0.6437|


We run our ESANS as well as the best baselines(Ada - $\tau$ and FairNeg) for a total of 5 times on public and industrial datasets. We present the mean, variance, and significance test p-values in the table. The experimental results strongly indicate that our ESANS is significantly superior to the two strong baselines. 有语法问题吗？



0.1798 $\pm$ 0.0034
0.4716 $\pm$ 0.0013
0.0829 $\pm$ 0.0019
0.1781 $\pm$ 0.0012
0.4801 $\pm$ 0.0010
0.6691 $\pm$ 0.0032
0.3674 $\pm$ 0.0018
0.6041 $\pm$ 0.0019
0.4030 $\pm$ 0.0012
0.6684 $\pm$ 0.0005
0.3969 $\pm$ 0.0025
0.6450 $\pm$ 0.0040

0.2045 $\pm$ 0.0020
0.4868 $\pm$ 0.0045
0.0757 $\pm$ 0.0005
0.1682 $\pm$ 0.0016
0.4685 $\pm$ 0.0009
0.6768 $\pm$ 0.0018
0.3544 $\pm$ 0.0010
0.5885 $\pm$ 0.0027
0.4089 $\pm$ 0.0017
0.6617 $\pm$ 0.0037
0.4060 $\pm$ 0.0017
0.6435 $\pm$ 0.0024

0.2121 $\pm$ 0.0015
0.4945 $\pm$ 0.0017
0.0906 $\pm$ 0.0013
0.1824 $\pm$ 0.0023
0.4862 $\pm$ 0.0008
0.6922 $\pm$ 0.0014
0.3883 $\pm$ 0.0006
0.6229 $\pm$ 0.0030
0.4180 $\pm$ 0.0008
0.6735 $\pm$ 0.0015
0.4176 $\pm$ 0.0012
0.6599 $\pm$ 0.0026


[1].Adrian Łańcucki, Jan Chorowski, Guillaume Sanchez, Ricard Marxer, Nanxin Chen, Hans JGA Dolfing, Sameer Khurana, Tanel Alumäe, and Antoine Laurent.Robust training of vector quantized bottleneck models.In IJCNN, pages 1–7. IEEE, 2020.
