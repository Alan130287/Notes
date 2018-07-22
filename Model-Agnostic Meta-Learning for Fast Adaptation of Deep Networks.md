# Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks

标签（空格分隔）： PaperReview

---
## First Pass
> 1. Carefully read the title, abstract, and introduction
2. Read the section and sub-section headings, but ignore everything else
3. Glance at the mathematical content to determine the underlying theoretical fundations
4. Read the conclusions
5. Glance over the references, mentally ticking off the ones you've already read.

`Five Cs`:
1. `Category`: A new method called Model-Agnostic Meta-Learning
2. `Context`: Related to deep neural network and DRL. Based on Meta Learning.
3. `Correctness(Assumptions)`: Based on the Assumption that all the tasks are sampled from the same distribution.
4. `Contribution`: Create a simple model and task-agnostic algorithm for meta-learning that trains a model's parameters such that a small number of gradient updates will lead to fast learning on a new task.
5. `Clarity`: Well Written


## Second Pass
> Read the paper with greater care but ignore details such as proofs.

### Questions:
* $\min_{\theta} \sum_{\mathcal{T}_i\sim p(\mathcal{T})}\mathcal{L}_{\mathcal{T}_i}(f_{\theta'_i})= 
\sum_{\mathcal{T}_i\sim p(\mathcal{T})}\mathcal{L}_{\mathcal{T}_i}(f_{\theta-\alpha\nabla_\theta\mathcal{L}_{\mathcal{T}_i}(f_\theta)})$
how does it reach minimum?


### Unread References
* All of them

### The Content of Paper(Roughly)


### The Main Trust of Paper with Supporting Evidence
1. MAML learn and adapt quickly from only a few examples and continue to adapt as more data becomes available.
2. The ingnoring of second or third derivatives of loss function is not a big deal.

## Third Pass
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations
The method does not introduce additional parameters for meta-learning nor require a particular learner architecture.
### Hidden Failings and Assumptions
1. The tasks may not be sampled from the same distribution
2. When second or third derivatives are not ignorable, we can't just calculate the first order.

### Identify and Challenge Every Assumption in Every Statement

### Ideas for Future Work

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

Not found.

### Future Readings
* a
* b
* c


































