# Deep Learning for detecting robotics grasps

标签（空格分隔）： PaperReview Grasping
---

[TOC]

## First Pass
> 1. Carefully read the title, abstract, and introduction
2. Read the section and sub-section headings, but ignore everything else
3. Glance at the mathematical content to determine the underlying theoretical fundations
4. Read the conclusions
5. Glance over the references, mentally ticking off the ones you've already read.

`Five Cs`:
1. `Category`: A new method to determine where to grasp.
2. `Context`: Grasps and Deep Learning 
3. `Correctness`: 
4. `Contribution`:
 * first deep learning algorithm for detecting robotic grasps
 * handle multimodal inpurts based on multimodal group regularization
 * present a multi-step cascaded system for detection, significantly reducing its computational cost.
5. `Clarity`: 


## Second Pass
> Read the paper with greater care but ignore details such as proofs.

### Questions:
* multimodal data
  data composed of with the different different distribution
* The network structure
* structured regularization
* Multimodal group regularization
* Multimodal feature learning algorithm
* 


### Unread References
* M. Dogar, K. Hsiao, M. Ciocarlie, and S. Srinivasa. Physics-based grasp planning through clutter. In RSS, 2012.
* Goodfellow I, Le Q, Saxe A, Lee H and Ng AY (2009) Measuring invariances in deep networks. In: NIPS.
* a dirty model for multi-task learning

### The Content of Paper(Roughly)

![image.png-631.8kB][1]
A small deep network is used to score potential grasps in this image, and a small candidate set of the top-ranked grasps is provided to a larger deep network, which yields a single best-ranked grasp.

The rectangle is defined by tuple of 5 elements (x, y, width, height, orientation).

![image.png-274.4kB][2]


![image.png-225.4kB][3]

Use variation of SAE(sparse auto-encoder)
![image.png-50.2kB][4]
to pre-training weights to avoid overfitting.

The parameter are defined bellow. It maximize the log-likelihood of the data along with regularization penalties on hidden layer weights.
![image.png-27.2kB][5]

Possible models for multimodal deep learning.

![image.png-151.4kB][6]


In structured multimodal regularization algorithm, each modality will be used as a regularization group separately for each hidden unit.
A group-wise p-norm `?????`
![image.png-15.4kB][7]

It shows the network can learn where to grasp.
![image.png-752.6kB][8]


### The Main Trust of Paper with Supporting Evidence

## Third Pass
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations
 * first deep learning algorithm for detecting robotic grasps
 * handle multimodal inpurts based on multimodal group regularization`?`
 * present a multi-step cascaded system for detection, significantly reducing its computational cost.


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


  [1]: http://static.zybuluo.com/Counting/i93odlodhv04cv1gi3blq6a9/image.png
  [2]: http://static.zybuluo.com/Counting/zba2hg5xpfzcpqngg3tu2on1/image.png
  [3]: http://static.zybuluo.com/Counting/peozwh6x9rialpjqdcdsw86q/image.png
  [4]: http://static.zybuluo.com/Counting/aui7p0g4t49mwzf9i3zhioxp/image.png
  [5]: http://static.zybuluo.com/Counting/54zlyeazzxyze3k9ai0s1h06/image.png
  [6]: http://static.zybuluo.com/Counting/alu9ucssa2l8u9wp8vrw30ht/image.png
  [7]: http://static.zybuluo.com/Counting/lrcal77ccohcekjaukh2ywn4/image.png
  [8]: http://static.zybuluo.com/Counting/pccf2aqsqnybt1tynsule9cv/image.png