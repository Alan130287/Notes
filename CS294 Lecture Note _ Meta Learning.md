# CS294 Lecture Note ? Meta Learning

标签（空格分隔）： DRL LectureNote

---
## What is Meta Learning
* Very closely related to multi-task learning
* Formulations
 * Learning an optimizer
 * Learning an RNN that ingests experience
 * Learning a representation

<img src="http://static.zybuluo.com/Counting/m0s43eyb5kbriivhl1dokdmv/image.png" width="300" height="200" alt=""/>

 
## Why Meta Learning
* DRL, expecially model-free, requires a huge number of samples
* if we can meta-learn a faster reinforcement learner, we can learn new tasks efficiently

## Meta Learning in RL
Supervised Meta Learning: $f(D_{train}, x) \rightarrow y)$
Reinforcement Meta(for example): $f(D_{train},s)\rightarrow a$


## Preparing a Model for Faster Learning
> Model-Agnostic Meta-Learning

To train the ant to adapt new direction quickly.

<img src="http://static.zybuluo.com/Counting/t56csjvzyb4khmfwlwyfdwgh/image.png" width="500" height="200" alt=""/>

## Model-agnostic meta-learning(MAML)
Supervised learning: $f(x)\rightarrow y$
Supervised meta-learning: $f(D_{train},x) \rightarrow y$
MAML: $f_{MAML}(D_{train},x)\rightarrow y$

$f_{MAML}(D_{train},x) = f_{\theta'}(x)$
$\theta' = \theta- \alpha \sum_{(x,y)\in D_{train}}\nabla_\theta\mathcal{L}(f_\theta(x,y))$

It is just another computation graph, but has favorable inductive bias.

## Meta Learning Summary and Open Problems
* Meta-learning = learning to learn
* Supervised meta-learning = supervised learning with datapoints that are entire datasets
* RL meta-learning with RNN policies
* Ingest past experience with RNN
* Simply run forward pass at test time to 'learn'
* Just contextual policies(no actual learning)
* Model-agnostic meta-learning
* Use gradient descent learning rule
* Conceputally not that different`?`
* The promise of meta-learning: use past experience to simply acquire a much more efficient deep RL algorithm
* The reality of meta-learning: mostly works well on smaller problems 
* Main limitations
 * RNN policies are extremely hard to train, and likely not scalable
 * Model-agnostic meta-learning presents a tough optimization problem
 * Designing the right task distribution is hard 
 * Generally very sensitive to task distribution(meta-overfitting)
  

 



























































