# Imitation from Observation Learning to Imitate Behaviour from Raw Video via Context Translation

标签（空格分隔）： PaperReview DRL
---

[TOC]

## First Pass
> 1. Carefully read the title, abstract, and introduction
2. Read the section and sub-section headings, but ignore everything else
3. Glance at the mathematical content to determine the underlying theoretical fundations
4. Read the conclusions
5. Glance over the references, mentally ticking off the ones you've already read.

`Five Cs`:
1. `Category`: Imitation Learning
2. `Context`: 
 * Third Person Imitation Learning
 * Generative Adversarial Imitation Learning
 * Unsupervised Perceptual Rewards for Imitation Learning
3. `Correctness`: 
4. `Contribution`: The imitation-from-observation algorithm is based on learning a context translation model that can convert a demonstration from one context to another context, which can acqurie a feature representation that is suitable for tracking demonstrated behavior. Then use DRL to optimize for the actions that optimally track the translated demonstration in the target context.
5. `Clarity`: 

## The Content of Paper(Roughly)

### Pipeline
The imitation-from-observation algorithm is based on learning a context translation model that can convert a demonstration from one context to another context, which can acqurie a feature representation that is suitable for tracking demonstrated behavior. Then use DRL to optimize for the actions that optimally track the translated demonstration in the target context.

The network used to translate between context(e.g. the angle of view)
![image.png-116.3kB][1]

### 3 Loss functions and 2 Rewards
To deal with pixel level reconstruction
![image.png-5.9kB][2]

It needs $z_3$ to carry useful information, which means $Enc_1$ and $Dec$ should do well in reconstruciton.
![image.png-7.8kB][3]

This forces the encoder $Enc_1$ and decoder $Dec$ to adopt a consistent feature representation
![image.png-6.5kB][4]

A conbined loss function is given:
![image.png-9.1kB][5]
where $\lambda_1$ and $\lambda_2$ are hyperparameters

A penalty for deviation from the translated features. Note that, there are n demonstration contexts(n angles of observations $o_t^i, \dots, o_t^n$)`?`
![image.png-13.2kB][6]

This reward directly penalizes the policy for experiencing observations that differ from the translated observations.
![image.png-11.8kB][7]

Final reward
![image.png-2.9kB][8]![image.png-7.3kB][9]
where $\omega_{rec}$ is hyperparameter

### Network Structure
![image.png-328.1kB][10]

### Results
![image.png-35.9kB][11]

### Ablations on Model Losses and Reword Functions
![image.png-31.9kB][12]


## Second Pass
> Read the paper with greater care but ignore details such as proofs.
### Questions:
* a
* b
* c
* d


### Unread References
> Generative Adversarial Imitation Learning 
Unsupervised Perceptural Rewards for Imitation Learning
Trust region policy optimiztion
End-to-end training of deep visuomotor policies




### The Main Trust of Paper with Supporting Evidence

## Third Pass
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations

### Hidden Failings and Assumptions
So many loss functions and Reword Functions. How to find the suitable hyperparameter values remains a problem.

### Ideas for Future Work



### Reconstruct the Entire Structure of Paper in Mermory
- [ ] Reconstruct


  [1]: http://static.zybuluo.com/Counting/33nn8pbqhp7z8dwy494hfmwh/image.png
  [2]: http://static.zybuluo.com/Counting/l0zwpqhv85knls6h3i5vlymg/image.png
  [3]: http://static.zybuluo.com/Counting/iynmhmjevek666a0fcx2jfw4/image.png
  [4]: http://static.zybuluo.com/Counting/mivw8q0kjz4u9pz9plzcan70/image.png
  [5]: http://static.zybuluo.com/Counting/ai06bj9kcn9zenbcr4qva3o8/image.png
  [6]: http://static.zybuluo.com/Counting/k5rgmddyle8kk9m8luk97p78/image.png
  [7]: http://static.zybuluo.com/Counting/6xp0lr5ggdpuigbyvla02k3t/image.png
  [8]: http://static.zybuluo.com/Counting/ker6rhe9yif1j28744elojv1/image.png
  [9]: http://static.zybuluo.com/Counting/fntzamg5ceuxfp29t215p9j7/image.png
  [10]: http://static.zybuluo.com/Counting/fhx9j1qcoimvwicuczyhanwf/image.png
  [11]: http://static.zybuluo.com/Counting/0wr0ie0lp78vlgrhbu0fi8vt/image.png
  [12]: http://static.zybuluo.com/Counting/k4x0h0o7l6do015gnrqkhlnc/image.png