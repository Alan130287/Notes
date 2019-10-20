# One-Shot Visual Imitation Learning via Meta-Learning
标签（空格分隔）： PaperReview

---
[TOC]
## First Pass
> 1. Carefully read the title, abstract, and introduction
2. Read the section and sub-section headings, but ignore everything else
3. Glance at the mathematical content to determine the underlying theoretical fundations
4. Read the conclusions
5. Glance over the references, mentally ticking off the ones you've already read.

`Five Cs`:
1. `Category`: The implementation of One-shot Imitation Meta-learning in reinforcement learning.
2. `Context`: Related paper *Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks*.Based on One-Shot Imitation Learning and Meta-Learning 
3. `Correctness`: Good.
4. `Contribution`: To demonstrate an aproach for one-shot imitation learning from raw pixels.
5. `Clarity`: Well Written.


## Second Pass
> Read the paper with greater care but ignore details such as proofs.

### Questions:
* -[x] what is meta learning?
* -[x] what is Two-Head Architecture(Meta Learning a Lost for Fast Adaptation) ?


### Unread References
* Computational approaches to motor learning by imitaion
* Learning to learn
* Discovering optimal imitaion strategies
* An autonomous land vehicle in a neural network
* so many

### The Content of Paper(Roughly)
* Introduce the visual meta-imitation learning problem(A vision based policy must addapt to a new task from a single demostration
* Summerize a prior meta-learning method and extend it into a meta-imitation learning algorithm
* Give the Model Architectures for Meta Imitation Learning.
* Experiment in both simulation and real world.


### The Main Trust of Paper with Supporting Evidence
The method of meta-imitation performs better than contextual policy, LSTM and LSTM+Attention

## Third Pass 
(`Unfinished)`
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations
* Create the two head architecture. One head for the action and one head for loss function, which enable the model to learn from raw pixels input.


### Hidden Failings and Assumptions
* Similar to Model-Free Imitation Learning, the tasks must be sampled from the same distribution, which means the tasks must be similar to each other.
* The meta-learnt loss function $\mathcal{L^*_{T_i}(f_{\theta'_i})} = \sum_{\mathcal{\tau^{(j)}\sim T_i}} \sum_t ||Wy^{(j)}_t+b||^2_2$ seems tricky.

### Identify and Challenge Every Assumption in Every Statement

### Ideas for Future Work
* We can test on more diverse tasks(demonstrations).
### Reconstruct the Entire Structure of Paper in Mermory
- [x] Reconstruct

### Strong and Weak Points
#### Strong Points
* a
* b
* c

#### Weak Points
* a
* b
* c

### Implicit Assumptions, Missing Citations to Relevant Work and Potential Issues


### Future Readings
* a
* b
* c

## Code Analysis
Questions:
* For the input state, why it cut the gif to half, one for the training and the other for validation?(In mian.py 255)
* 

### run_sim_push.sh
input:
* states: (m, 100, 20) where m is meta_mini_batch
* actions: (m, 100, 7) where m is meta_mini_batch
* `No pixels input`

output: 
*actions with dimentions of 7

Network Architecture:
* `two head architecture is used`

### run_sim_reach.sh
input:
* dimention of state: 10
* dimention of action: 2
* `No pixels input`

output:
* dimention of of action: 2

### test_sim_reach.sh 
input:
* dimention of state: 10
* dimention of action: 2
* `pixels input`

output:
* dimention of of action: 2



































