<font size=4>Pitfalls in Machine Learning<font>
ML is often non trivial and prone to several pitfalls, ranging from obvious flaws to minor blemishes.

Ten pitfalls will be described with respect to the stages of a typical machine learning workflow
![[Pasted image 20240426112557.png]]


<font size = 3>Data collection and Labelling<font>
Its clear that conducing experiments using unrealistic data leads to the misestimation of an approach's capabilities. 
- The following two pitfalls induce this problem and require special attention when developing learning based systems in computer security

>P1 - Sampling Bias. The collected data does not sufficiently represent the true data distribution of the underlying security problem
> - Sampling bias refers to a situation where the collected data does not adequately reflect the true distribution of the underlying problem or phenomenon.
> - With a few rare exceptions, researchers develop learning-based approaches without exact knowledge of the true underlying distribution of the input space.  Instead they rely on a dataset with a fixed number of samples that aim to resemble the actual distribution, but may not perfectly represent it
> **Security implications** : this problem is relevant to security, becuase its particularly challenging to obtain security data, and often requires multiple sources of varying quality, which can inroduce bias,
> 	- The mixing of data from incompatible sources should be avoided, as it is a common cause of additional bias. A strategy around this is to include the extention of the dataset with synthetic data

>P2 - Label Inaccuracy. The ground truth labels required for classification tasks are inaccurate, unstable or erroneous, affecting overall performance of a learning based system

