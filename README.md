# DMCMC

Official PyTorch implementation of [Denoising MCMC for Accelerating Diffusion-Based Generative Models](https://arxiv.org/abs/2209.14593).

We propose a general sampling framework, Denoising MCMC (DMCMC), that combines Markov chain Monte Carlo (MCMC) with reverse-SDE/ODE integrators / diffusion models to accelerate score-based sampling. MCMC is used to produces samples in the product space of data and diffusion time, and reverse-SDE/ODE integrators are used to denoise the MCMC samples. Since MCMC travels close to the data manifold, DMCMC can produce high-quality data with reduced computation cost. The figure below illustrates the general idea of DMCMC.

<p align="center">
  <img src="https://github.com/1202kbs/DMCMC/blob/main/assets/diag.png" />
</p>

<p align="center">
  <img src="https://github.com/1202kbs/DMCMC/blob/main/assets/1a-min.png" width="100" />
  <img src="https://github.com/1202kbs/DMCMC/blob/main/assets/1b-min.png" width="100" />
</p>
