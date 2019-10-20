# Third Person Imitation Learning

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
1. `Category`: A new architecture introduced for the third-person imitation learning. 
2. `Context`: Based on Markov Decision Process(MDP) and Generative adversarial networks(GAN).
3. `Correctness`: 
4. `Contribution`: Presents a method for unsupervised third-person imitation learning. Here the third person refers to training an agent to correctly achieve a simple goal in a simple environment when it is provided a demonstration of a teacher achieving the same goal but from a different view point.The unsupervised refers to the fact that the agent receive only third-person demonstrations and is not provided a correspondence between teacher states and student states
5. `Clarity`:


## Second Pass
> Read the paper with greater care but ignore details such as proofs.
### Questions:
* GAN?
* What does function $\mathcal{G}$ do? 


### Unread References
* So many

### The Content of Paper(Roughly)
* Previous study:find a policy $\pi_{\theta}$ that makes it impossible for a discriminator to dinstinguish states visited by the experts from states visited by the imitator agent.
![image.png-11.1kB][1]
which can be realized as fellow:
![image.png-10.8kB][2]
if $\mathcal{D}_R$ works well, if $s \sim \pi_{\theta}$, $\mathcal{D}_R(s) \rightarrow 1$, if $s \sim \pi_E$, $\mathcal{D}_R(s) \rightarrow 0$
* But the above Eq will fail in cases when the expert and non-expert act in different environments, since $\mathcal{D}_R$ will quickly learn these differents and use them as a strong classification signal. To solve such problem, we can let $\mathcal{D}_R$ works by first extracting features from $o_t$, and then using these features to make a classification. Partition the $\mathcal{D}_R$ into two part.
![image.png-17.1kB][3]
* The mutual information term can be instantiated by introducing another classifier $\mathcal{D}_D$
![image.png-13.9kB][4]
* Consider the change
![image.png-14.9kB][5]
* To deal with the competition over $\mathcal{D}_F$ , we introduce a function $\mathcal{G}$ that acts as the identity when moving forward through a directed acyclic graph and flips the sign when backpropagating through the graph.
![image.png-17.1kB][6]
* The architecture:
![image.png-142.5kB][7]

## Third Pass
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations
The separation of $\mathcal{D}_R$ and the domain loss.

### Hidden Failings and Assumptions
Sorry, I couldn't find.
### Identify and Challenge Every Assumption in Every Statement
...
### Ideas for Future Work
The experience is based on simple immitation learning task. What would happen if we extend it to more complex environment?
### Reconstruct the Entire Structure of Paper in Mermory
- [x] Reconstruct

### Strong and Weak Points
#### Strong Points
* Simple algorithm
* Simple policy architecture

#### Weak Points
* The extention to complex imitation tasks is challenging. 

### Implicit Assumptions, Missing Citations to Relevant Work and Potential Issues


### Future Readings
* ao many
* 


  [1]: http://static.zybuluo.com/Counting/a5enakkjow0nwz5o3m3od580/image.png
  [2]: http://static.zybuluo.com/Counting/y4ypd31hh0s0vffbhc2lt3dh/image.png
  [3]: http://static.zybuluo.com/Counting/3z7t8itfwgiz9eaksz94wz1b/image.png
  [4]: http://static.zybuluo.com/Counting/xjeblp5f8i41zcbipgewsr2h/image.png
  [5]: http://static.zybuluo.com/Counting/hubrpb56mf8hzkp9yiuaolm7/image.png
  [6]: http://static.zybuluo.com/Counting/8fare88jhk1uqld0la4lr4fy/image.png
  [7]: http://static.zybuluo.com/Counting/y6zrtyve3vyhzjib609kgbcg/image.png