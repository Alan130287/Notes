# Learning Modular Neural Network Policies for Multi-Task and Multi-Robot Transfer

标签（空格分隔）： PaperReview Task DRL ModularNetwork
---

[TOC]

## First Pass
> 1. Carefully read the title, abstract, and introduction
2. Read the section and sub-section headings, but ignore everything else
3. Glance at the mathematical content to determine the underlying theoretical fundations
4. Read the conclusions
5. Glance over the references, mentally ticking off the ones you've already read.

`Five Cs`:
1. `Category`: Modular DRL Model
2. `Context`: 
3. `Correctness`: 
4. `Contribution`: 
 * Address robotic multi-task and transfer learning by training policy modules that are decomposed over robots and tasks, so as to handle novel robot-task combinations with minimal additional training.
 * Analyze regularization techniques that force the modules to acquire a generalizable bottleneck interface.
 * Present a detailed evaluation of the method on a range of simulated tasks for both visual and non-visual policies.
5. `Clarity`: 


## Key Points of Paper
### The policy 
![image.png-12.2kB][1]

### Regularization Methods
* limit the numbers of hidden units in the modular interface
* apply drop out method

### Pipline
![20180807112612.png-67.9kB][2]

![image.png-33.7kB][3]

### Results
The task specified modules are robot-invariant and the robot specified modules are task-invariant. In some cases, previously untrained combinations might generalize immediately to the new task, while in other cases, the composition of previously trained modules for a new previously unseen task can serve as a very good initialization for speeding up learning.

## Second Pass
> Read the paper with greater care but ignore details such as proofs.
### Questions:
* a
* b
* c
* d


### Unread References
> Deep compositional question answering with neural module networks


## Third Pass
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations
Modular Network

### Ideas for Future Work
* To combine the approach with more traditional, sequential methods for transfer learning such that the same robot can learn multiple tasks in sequence, and still benefit from modular network.

### Reconstruct the Entire Structure of Paper in Mermory
- [x] Reconstruct

### Strong and Weak Points
#### Strong Points
* Modular models can be combined to generalize to new task-robot combination. 

#### Weak Points
* require different task-robot combinations to be trained simultaneously 


### Implicit Assumptions, Missing Citations to Relevant Work and Potential Issues


### Future Readings
> Deep compositional question answering with neural module networks


  [1]: http://static.zybuluo.com/Counting/pmrryd6f22hnxan9207mj8am/image.png
  [2]: http://static.zybuluo.com/Counting/1uszr0yci14n8wxtkeivezwr/QQ%E6%88%AA%E5%9B%BE20180807112612.png
  [3]: http://static.zybuluo.com/Counting/zqvc47rtblvaue4658wnxe5j/image.png