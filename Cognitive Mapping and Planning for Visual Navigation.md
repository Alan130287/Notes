# Cognitive Mapping and Planning for Visual Navigation

标签（空格分隔）： PaperReview Navigation DRL Robotics
---

[TOC]

## First Pass
> 1. Carefully read the title, abstract, and introduction
2. Read the section and sub-section headings, but ignore everything else
3. Glance at the mathematical content to determine the underlying theoretical fundations
4. Read the conclusions
5. Glance over the references, mentally ticking off the ones you've already read.

`Five Cs`:
1. `Category`: Visual navigation by Cogitive Mapping and Planning(CMP).
2. `Context`: 
3. `Correctness`: 
4. `Contribution`: 
 * The model can learn statistical regularities of indoor environments in a task-driven manner
 * Jointly training the mapper and the planner makes our planner more robust to errors of the mapper
 * the modle can be used in an online manner in novel environments without requiring a pre-constructed map.
5. `Clarity`: 


## Key Points of Paper
### Overall Architecture 
![image.png-232.6kB][1]
### Architecture of the Mapper
![image.png-522.1kB][2]

### Architecture of the Planner
![20180808104420.png-125kB][3]

### Pipeline 
CMP consists of a spatial memory(mapper) to capture the lay out of the world and a planner that can plan path given partial information. The mapper and the planner are put together into a unified architecture that can be trianed to leverage regularities of the world. The mapper fuses information from input views as observed by the agent over time to produce a metric egocentirc multi-scale belief about the world in a top-down view. The planner uses this multi-scale egocentric belief of the world to plan paths to the specified goal and outputs the optimal action to take. This process is repeated at each time step to convey the agent to the goal.

At each time step, the agent updates the belief of the world from the previous time step by using the egomotion to transform the belief from previous time step into the current coordinate frame and incorporating information from the current view of the world to update the belief. The planner uses the metric belief of the world to abtained through the mapping operation described above to plan paths to the goal.

## Second Pass
> Read the paper with greater care but ignore details such as proofs.
### Questions:
* belief network
* b
* c
* d


### Unread References
> 

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


  [1]: http://static.zybuluo.com/Counting/1vuszzz5vjn5y2zp1alvi0cu/image.png
  [2]: http://static.zybuluo.com/Counting/m7t11850pxzjhu627mkfau6r/image.png
  [3]: http://static.zybuluo.com/Counting/5urq94ng9qz2hdh9ybz4ppiy/QQ%E6%88%AA%E5%9B%BE20180808104420.png