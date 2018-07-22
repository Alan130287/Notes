# CS294 Lecture Note 4 Policy Gradient

---

[TOC]

## Outline
1. The policy gradient algorithm
2. What does the policy gradient do?
3. Basic Variance reduction: causality
4. Basic variance reduction: baselines
5. Policy gradient examples

Goals:
* Understand policy gradient reinforcement learning
* Understand practical considerations for policy gradients


## Content
* Evaluating the RL objective
 * Monte Carlo Methods: $\theta^*=\arg \max_{\theta}E_{\tau\sim p_{\theta}(\tau)}[\sum_t r(s_t, a_t)]$
$J(\theta)=E_{\tau\sim p_{\theta}(\tau)}[\sum_t r(s_t, a_t)]\approx \frac{1}{N}\sum_i\sum_tr(s_{i,t},a_{i,t})$
* Evaluating the policy gradient
 * Log-gradient trick(a convenient identity)
$\pi_{\theta}(\tau)\nabla_{\theta}\log\pi_{\theta}(\tau)=\pi_{\theta}(\tau)\frac{\nabla_{\theta}\pi_{\theta}(\tau)}{\pi_{\theta}(\tau)}=\nabla_{\theta}\pi_{\theta}(\tau)$
  * Direct policy gradient
$\nabla_{\theta}(J)=E_{\tau\sim\pi_{\theta}(\tau)}[\nabla_{\theta}\log\pi_{\theta}(\tau)r(\tau)]=E_{\tau\sim\pi_{\theta}(\tau)}[(\sum_{t=1}^T\nabla_{\theta}\log\pi_{\theta}(a_t|s_t)(\sum_{t=1}^Tr(s_t, a_t))]$
$\approx \frac{1}{N} \sum_{i=1}^N((\sum_{t=1}^T\nabla_{\theta}\log\pi_{\theta}(a_{i,t}|s_{i,t})(\sum_{t=1}^Tr(s_{i,t}, a_{i,t})))$
![image.png-31.3kB][1]
 * Formalization of trial and error
![image.png-198kB][2]
 * Partial observability
* What is the wrong with policy gradient?
 `It is beyond my knownledge, and maybe future study will cover it.`
* To reduce the variance of policy gradient
 1. Exploiting causality(Future doesn't affect the past)`But how does it work in the mathmetical way?`
![image.png-49.2kB][3]
 2. Unbiased baseline
![image.png-216.7kB][4]
 3. Analyzing variance
![image.png-22.5kB][5]
* The off-policy gradient
![image.png-42.6kB][6]
  


  [1]: http://static.zybuluo.com/Counting/m87z0ywlpa7tkhnjnaddtloc/image.png
  [2]: http://static.zybuluo.com/Counting/ofu0xj3z6mo6r0okcl381256/image.png
  [3]: http://static.zybuluo.com/Counting/450uecbc0nr50o7121osh1rv/image.png
  [4]: http://static.zybuluo.com/Counting/e563qyjzva6nqz3h801u0i23/image.png
  [5]: http://static.zybuluo.com/Counting/6gzz4kfr3wnh7964c92we5r3/image.png
  [6]: http://static.zybuluo.com/Counting/b6jziwbodx9umoaebtint02c/image.png