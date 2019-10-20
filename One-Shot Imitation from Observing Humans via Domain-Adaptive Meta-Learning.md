# One-Shot Imitation from Observing Humans via Domain-Adaptive Meta-Learning

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
1. `Category`: A descrption of the prototye of Domian-Adaptive Meta-Learning and its application in one-shot imitation learning. 
2. `Context`: 
* One-Shot Imitation Learning
* Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks
* One-Shot Visual Imitation Learning via Meta-Learning
3. `Correctness`: Assumption valid.
4. `Contribution`: Attribute a system for learning robotic manipulation skills from a single video of a human by leveraging large amounts of prior meta-training data, collected for different tasks.
5. `Clarity`: Well written.


## Second Pass
> Read the paper with greater care but ignore details such as proofs.
### Questions:
* How does the complex architecture work?
* $\mathcal{L}_{BC}(\phi,d^r)=\sum_t\log\pi_{\phi}(a_t|o_t,s_t)$ ?
* Probabilistic graphical model?
* Temporal Convolution? 


### Unread References
So many.
### The Content of Paper(Roughly)
* Previous study: 
 * Model Agnostic Meta Learning
 * Two head architecture
* Domain-Adaptive Meta Learning:
 * The Algorithm
![image.png-77.5kB][1]
![image.png-41.5kB][2]
 * Learned Temporal Adaptation Objectives(The loss function $\mathcal{L}{\psi}$)
![image.png-91.3kB][3]
 * Probabilistic Interpretation`?`
![image.png-80kB][4]
* Network Architecture
 * Policy Architecture 
![image.png-171.3kB][5]
 * learned Adaptation Objective Architecture
$\mathcal{L}_{\psi}= \mathcal{L}_{\psi_1}(f_{1:T})+\mathcal{L}_{\psi_2}(h_{1:T})$ 
![image.png-78.3kB][6]

   
### The Main Trust of Paper with Supporting Evidence

## Third Pass
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations

### Hidden Failings and Assumptions

### Identify and Challenge Every Assumption in Every Statement

### Ideas for Future Work

### Reconstruct the Entire Structure of Paper in Mermory
- [ ] Reconstruct

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


  [1]: http://static.zybuluo.com/Counting/xbo7ddosfvju93t56q69xzfe/image.png
  [2]: http://static.zybuluo.com/Counting/kf0v2q6la80qamwz0mm3bvuu/image.png
  [3]: http://static.zybuluo.com/Counting/8k90otg8fkcnnjv4mck32rbf/image.png
  [4]: http://static.zybuluo.com/Counting/qi5c2i4bf9oq2xfqa2b91fia/image.png
  [5]: http://static.zybuluo.com/Counting/lixbk5xoug5o65h8h8a7od1i/image.png
  [6]: http://static.zybuluo.com/Counting/tnf2c12rmbwveyqqnz4bl03k/image.png