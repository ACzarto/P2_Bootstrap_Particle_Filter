# P2_Bootstrap_Particle_Filter
This repository contains the code that implements and test the Bootstrap Particle Filter, a type of sequential Monte Carlo method for non-linear state estimation. 

In the framework of Stochastic Filtering Algorithms, such as the Kalman-Bucy Filter, one depends on the hypothesis of linearity and gaussian noises. In the situation that we do not, we have as an alternative the so-called Bootstrap Particle Filter, that uses the Sequential Importance Sampling (SIS) technique to estimate the hidden state. 

Unlike analytical filters, the Bootstrap Particle Filter represents the posterior probability density function $p(x_n | y_{0:n})$ empirically through a set of $J$ random samples, called particles, each associated with a specific importance weight. By leveraging the system's dynamic equations as the proposal distribution, the algorithm recursively updates these weights based on the likelihood of the incoming observable measurements. To prevent the classic issue of weight degeneracy—where all but a few particles end up with negligible weights—a multinomial resampling step is adaptively triggered based on the effective number of particles ($N_{eff}$).

In this code, we test the algorithm in the following non-linear, non-Gaussian state-space system of equations:

Dynamical Model:

$$x_{n+1} = 3 \tanh(y_n) + x_n + \sin(y_n) + u_{1,n}$$

$$y_{n+1} = 0.5 \tanh(x_n) + y_n + \sin(y_n) + u_{2,n}$$

and the noise is $$\mathbf{u}_{n,i}  \sim \mathcal{U}(-1, 1)$$

Observation Model:

$$o_n = \frac{1}{x_n} + y_n^2 + v_n$$

and the noise $$v_n \sim \text{Cauchy}(0, 0.02)$$
