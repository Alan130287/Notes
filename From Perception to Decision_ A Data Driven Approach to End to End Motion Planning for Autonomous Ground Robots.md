# From Perception to Decision: A Data Driven Approach to End to End Motion Planning for Autonomous Ground Robots

标签（空格分隔）： PaperReview DRL Turtlebot

---

[TOC]

## First Pass
> 1. Carefully read the title, abstract, and introduction
2. Read the section and sub-section headings, but ignore everything else
3. Glance at the mathematical content to determine the underlying theoretical fundations
4. Read the conclusions
5. Glance over the references, mentally ticking off the ones you've already read.

`Five Cs`:
1. `Category`: raw 2-D-laser range findings and a target position -> steering commands for the robot 
2. `Context`: Which other papers is it related to? Which theoretical bases were used to analyze the problem?
3. `Correctness`: Do the assumption appear to be valid?
4. `Contribution`: 
 * A data driven end-to-end motion planner from laser range findings to motion commands
 * Development and test on a real robotic platform in unknown environment
 * Extensive evaluation and comparison of presented local approach with respect to a motion planner with global map information. 
5. `Clarity`: Is the paper well written?


## Second Pass
> Read the paper with greater care but ignore details such as proofs.

### Questions:
* a
* b
* c
* d


### Unread References
> W. Xu, et al., “A real-time motion planner with trajectory optimizationfor autonomous vehicles,” in Robotics and Automation (ICRA), 2012 IEEE International Conference on. IEEE, 2012, pp. 2061–2067.

### The Content of Paper(Roughly)
* the approach doesn't need a global map
* Based on the `hypothesis` that by learning a physical understanding of the environment and the navigation characteristics of an expert operator, the machine learning based approach is able to perform in a similar way, even in previously unseen scenarios.
* challenges
 * relevant information should be extracted from the sensor data
 * the training of end-to-end model
 * the model has to react immediately

* core function
$$\mu = \mathcal{F}_\theta(y,g)$$
where y is sensor data, g is goal information and $\mu$ is the desired steering commands. 
* loss function 
$$J_k(\Gamma_B)=\frac{1}{N_B}\sum^{i+N_B}_{j=i}|\mathcal{F}_{\theta_k}(y_j, g_j)-\mu_{exp,j}|$$
where mini-batch $\Gamma_B=[\gamma_i, \dots, \gamma_{i+N_B}]$

* Network Architecture
![image.png-101.8kB][1]

* to use a global motion planner as expert to solve the problem of numerous training data.

* increasing the size of the Fully connected layers of the network imporves the navigation performance in the real world while it was not benificial during the simulation test.


 

### The Main Trust of Paper with Supporting Evidence

by learning a physical understanding of the environment and the navigation characteristics of an expert operator, the machine learning based approach is able to perform in a similar way, even in previously unseen scenarios.

## Third Pass
> To attempt to virtually re-implement the paper: making the same assumption as the author and re-create the work.

### Innovations
* using the global map planner as expert driver which settles the problem of numerous training data(expert data)

### Hidden Failings and Assumptions
* Without the global map, the turtlebot may stuck in a local area. In other words, the model's generality to the complex envirnment is a challenge.
* It can not completely replace the global map based planner.

### Ideas for Future Work
* How training samples can be reduced
* How simulated and real-world training data can play together.
* When the robot enters a convex dead-end region, it is not capable of freeing itself. And the robot sometimes fluctuates before avoiding an obstable. **This issue might be solved by using recurrent neural networks(It may serve as a global map which can improve such problem and even perform far more better in complex environment)**


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
* RNN Application in navigation.


  [1]: http://static.zybuluo.com/Counting/5kwatm7ihn3fv8cblsrs65ho/image.png