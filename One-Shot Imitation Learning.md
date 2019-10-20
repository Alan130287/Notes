# One-Shot Imitation Learning

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
1. `Category`: It is imitation learning with only one demonstration as input. 
2. `Context`: Countless related papers.
3. `Correctness`: 
4. `Contribution`: Propose a meta-learning framework that enabe robot to learn very few demonstrations of any given tasks and instantly generalize to new situations of the same task, without requiring task-specific engineering. 
5. `Clarity`: No.


## Second Pass
> Read the paper with greater care but ignore details such as proofs.
### Questions:
* The network architecture is incomprehensible.
* What is dilated temporal convolution?
* what is neigborhood attention(soft attention)?
* What is context network?


### Unread References
> * Neural machine translation by jointly learning to align and translate
* Multi-scale context aggregation by dilated convolutions

### The Content of Paper(Roughly)
* Two broad problems:
 * dexterity: robots should learn how to approach, grasp and pick up complex objects and how to place or arrange them into a desired configuration?
 * communication: how to communicate the intent of the task at hand, so that the robot can replicate it in a broader set of initial condition?

* The network architecture
 * Demonstration network 
 *Temporal Dropout
 *Neighborhood Attention
 * Context network
 *Attention over demonstration
 *Attention over current state
 * Manipulation network
![image.png-226.2kB][1]
 

### The Main Trust of Paper with Supporting Evidence
![image.png-65.9kB][2]

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


  [1]: http://static.zybuluo.com/Counting/56jfajzrc3qtzh3rkq4nqfjw/image.png
  [2]: http://static.zybuluo.com/Counting/gx1ezh4fp3pslagrl86iov5a/image.png