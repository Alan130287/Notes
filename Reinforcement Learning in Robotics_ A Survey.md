# Reinforcement Learning in Robotics: A Survey

标签（空格分隔）： PaperReview

---

[TOC]

## First Pass

Mainly about the key challenges in robot reinforcement learning as well as notalbe successes.

## Second Pass
> Read the paper with greater care but ignore details such as proofs.
### Questions:
* In the part of value function approaches, how can we set the Lagrange Multipliers to be $V^\pi(s')$ and $\overline{R}$?
![image.png-53.5kB][1]
* What is the finite difference gradients P perturbed policy parameters?
![image.png-6.8kB][2]
* How to count 20 states and 7-d of actions
* The part **Meta-Actions**(4.1) is unprehensible. Maybe more references should be read. 
* As neural networks are globally affected from local errors, much work has focused on simply generalizing from neighboring cells`?`.


### Unread References
* a
* b
* c
* d

### The Content of Paper(Roughly)


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


## Content of Paper(Interested in)
### Introduction
Reinforcement Learning  enables a robot to autonomously discover an optimal behavior through trial-and-error interactions with its environment. 
#### Reinforcement Learning in the Context of Machine Learning
![image.png-21.8kB][3]
#### Reinforcement Learning in the Context of Robotics
* best represented with high-dimensional, continuous states and actions
* the state are often partially observed and noisy
* Experience on real physical system is tedious to obtain, expensive and often hard to reproduce.
* Algorithm need to be robust with respect to models that do not capture all the details of the real system(under modeling) and to model uncertainty.
* The generation of appropriate reward function is also difficult.
* Robot learning systems often employ policy search methods rather than value function-based approaches.
* If a task can be phrased as an optimization problem and exhibits temporal structure, reinforcement learning can often be profitably applied to both phrase and solve that problem.

### A Concise Introduction to Reinforcement Learning
In reinforcement learning, an agent tries to maximize the accumulated reward over its life-time.
#### Reinforcement Learning in the Average Reward Setting 
##### Value Function Approaches
* Dynamic Programming-Based Methods
 * Require: transition probabilities $T(s', a, s)$ and the reward function $R(s,a)$
 * model-based, update after an episode
 * Policy improvement greedily selects the best action in every state accoring to the value function updated.
* Monte Carlo Methods
 * Require: no transition probabilities $T(s', a, s)$ and reward function $R(s,a)$
 * model-free, on policy, update after an episode
 * Use sampling in order to estimate the value function when executing the current policy.
* Temporal Difference Methods
 * Require: reward function
 * model-free, on policy(off policy with important sampling)
 * use temporal error to update the value function every time step

##### Policy Search 
Often appears more natural to robotics
##### Value Function Approaches versus Policy Search
##### Function Approximation

#### Challenges in Robot Reinforcement Learning
##### Curse of Dimensionality
Robotics systems have to deal with these high dimensional states and actions due to the many degrees of freedom of modern anthropomorphic robots.
We can use hierarchical task decomposition which shifts some complexity to a lower layer of functionality.
##### Curse of Real-World Samples
* Hardware is expensive and requires careful mainten so safe exploration is a key issue of learning process.
* Dynamics of robot can change due to many external factors(temperature, wear ...)
* Environment setting can't be always reproduced.
* External factors are not always clear(how light condition affects the computor vision)
* Uncertainty due to inherent measurement noise and the inability to observe all stetes directly with sensors.
* Most robots need human supervision.
* Learning speed is slow compared to simulation environment
* Strict constraints on the interaction between the learning algorithm and robot setup(no time for robot to pause to think, learn or plan).
* Time discretization of robot versus continuous system of real physical world
* Delay in sensing and actuatio
##### Curse of Under-Modeling and Model Uncertainty
* Create sufficiently accurate model of the robot and its environment is challenging and often require many data samples
* Small simulation error can cause huge diverge in real world model.
* tasks are always learned better in real world due to complex mechanical interactions that have proven difficult to model accurately.
##### Curse of Goal Specification
* It is difficult to define a good reward function in robot reinforcement learning
* Binary rewards performs poorly and it is neccessary to introduce intermediate rewards.
* Trade-off between the complexity of the reward function and complexity of the learning problem.

#### Tractability Through Representation
a few key priciple for success in RL

* effective representations
* approximate models 
* prior knowledge or information

##### Smart State-Action Discretization
* hand crafted discretization
* Learned from data
* Meta-Actions
The idea is to have more intelligent actions that are composed of a sequence of movements and that in themselves achieve a simple task.
* Relational Representation
Used in highly geometic tasks.

##### Value Function Approximation
###### Physics-inspired Features
If good hand-crafted features are known, value function approximation can be accomplished using a linear combination of features. It is likely to yield good result in an on-policy setting while is unstable in off-policy case.
###### Neural Network
Clamping technique is key to achieve good performance with value function approximation in practice.
###### Generalize to Neighboring Cells
As neural networks are globally affected from local errors, much work has focused on simply generalizing from neighboring cells`?`.
But the method is lack of scalability to high-dimensional state and action spaces.
###### Local Models`?`
An extension of generalization among neighboring cells to generalizing among neighboring data points.
The parameters need to pre-specify, which requires a trade-off between representational accuracy and the number of parameters.
###### Gaussian Process Regression 
Gaussian Process Regression(GPR) is a non-parametric function with high computational complexity.
##### Prestructed Policies
There is a trade-off between the representational power(number of parameters) and learning speed(number of samples).
Function approximation can take the domain knowledge(task relevant parameters or generalization properties) into account. 

* Via Points & Splines
* Linear Models
* Motor Primitives
* Gaussian Mixture Models and Radial Basis Function Models
* Neural Network
* Locally Linear Controllers
* Non-parametric Policies

#### Tractability Through Prior Knowledge
* initial policy
allow model to focus on promising region in the value function or in policy space
* demonstrations
using the combination of imitation and trial and error. Often called Apprenticeship Learning(Inverse reinforcement learning).
Remove the need for global exploration
* initial models
* a predefined task structure 
reduce the complexity of learning task 
#### Tractability Through Model
##### Dealing with Simulation Biases
* To learn a model in simulated environment and transfer it to real-world robot system without error is impossible.
* Artificiallly adding a little noise will smooth model errors and avoid policy over-fitting.
##### Distributions over Models for Simulation`?`
##### Sampling by Re-Using Random Numbers`?`
#### Successful Learning Approaches with Forward Models
Methods that directly obtain a new policy candidate from a forward model.

##### Iterative learning control
Using a crude model to approximate gradient and inmprove the robot in real world iteratively.

##### Locally Linear Quadratic Regulators`?`

##### Value Function Methods with Learned Models
##### Policy Search with Learned Models

### A Case Study: Ball-in-a-Cup
It is a simple task and used as an example to highligh the methods and challenges disscussed above.
#### Experimental Setting: Task and Reward
![image.png-598.4kB][4]
States(20): 
1. joint angles of the robot 
2. joint velocities of the robot
3. cartesian coordinates of the ball
4. velocities of the ball

Actions(7):
1. joint space accelerations(translated into torques by a fixed inverse dynamics controller)

Reward Function: $r(t_c) = \exp(-\alpha(x_c-x_b)^2-\alpha(y_c-y_b)^2)$

#### Appropriate Policy Representation
So many physics stuff
#### Generating a Teacher Demonstration
A demonstration for imitation was obtained by recording the motions of a human player performing kinesthetic teach in  as show in (b). It requires a back-derivable robot system that is similar enough to a human arm to not cause embodiment issues.
#### Reinforcement Learning by Policy Search
Policy search methods are better suited for a scenario like this, where the task is episodic, local optimization is sufficient(thanks to the initial demonstration), and high dimentional, continuous states and actions need to be taken into account. 

* A single update step in a gradient based method usually requires as many episodes as parameters to be optimized.
* Step-size parameter for gradient based methods often is a crucial parameter that need times and efforts to be fine-tuned. 
An expectation-maximization inspired algorithm was employed that requires significanly `less samples` and has `no learning rate`.

**Policy learning by Weighting Exploration with the Returns(PoWER)**`?`
![image.png-23.4kB][5]
![image.png-8kB][6]


#### Use of Simulations in Robot Reinforcement Learning`?`
![image.png-19.1kB][7]
Most important parameters to tune
1. greediness of the important sampling 
2. the initial magnitude of the exploration
3. the number of parameters for policy

#### Results on the Real Robot
Running the real robot experiment was tedious as the ball was tracked by a stereo vision system.

#### Alternative Approach with Value Function Methods
> It need many prior knowledge which means it is not an end-to-end model. We can skip it because of the lack of generalization ability. 

### Discussion 
#### Open Questions in Robotic Reinforcement Learning 
Reinforcement learning can be employed for a wide variety of physical systems and control tasks in robotics. It is unlikely that single answers do exist for such a heterogeneous field, but even for very closely related tasks, appropriate methods currently need to be carefully selected.

* How to choose representations automatically? 
* How to generate reward funciton from data? 
* How much can prior knowledge help? How much is needed?
* How to integrate more tightly with perception?
* How to reduce parameter sensitivity? 
* How to deal with model errors and under-modeling?
#### Practical Challenges for Robotic Reinforcement Learning
* How to Exploit Data Sets Better?
* Comparable Experiments and Consistent Evaluation.
#### Robotics Lessons for Reinforcement Learning
* Focus on High-Dimensional Continuous Actions and Constant Adaptation
* Exploit Domain Structure for Scalability
* Local Optimality and Controlled State Distributions
* Reward Design






  [1]: http://static.zybuluo.com/Counting/mar8mt3phcbew1vfb4tutpur/image.png
  [2]: http://static.zybuluo.com/Counting/ntbovsqoogu16nv54fol7zmm/image.png
  [3]: http://static.zybuluo.com/Counting/6d01l8h6efc0rdx6yn72fcmn/image.png
  [4]: http://static.zybuluo.com/Counting/5zv33qvpy2dx0pfghg7idpmz/image.png
  [5]: http://static.zybuluo.com/Counting/m9zegf0irpa6wlkq84bwpvuq/image.png
  [6]: http://static.zybuluo.com/Counting/fc25cvqyuh1n0kqup9lg08us/image.png
  [7]: http://static.zybuluo.com/Counting/dxzgl8jmv1ek7es5lsxi5q1x/image.png