# DMCMC

Official PyTorch implementation of [Denoising MCMC for Accelerating Diffusion-Based Generative Models](https://arxiv.org/abs/2209.14593).

We propose a general sampling framework, Denoising MCMC (DMCMC), that combines Markov chain Monte Carlo (MCMC) with reverse-SDE/ODE integrators / diffusion models to accelerate score-based sampling. MCMC is used to produces samples in the product space of data and diffusion time, and reverse-SDE/ODE integrators are used to denoise the MCMC samples. Since MCMC travels close to the data manifold, DMCMC can produce high-quality data with reduced computation cost. The figure below illustrates the general idea of DMCMC.

<p align="center">
  <img src="https://github.com/1202kbs/DMCMC/blob/main/assets/main.png" />
</p>

Our framework is compatible with any choice of MCMC, variance-exploding score model, and reverse-SDE/ODE integrator. In particular, combined with integrators of Karras et al. (2022) and pre-trained score models of Song et. al (2021b), DMCMC achieves state-of-the-art results. In the limited number of score function evaluation (NFE) settings on CIFAR10, we have $3.86$ FID with $\approx 10$ NFE and $2.63$ FID with $\approx 20$ NFE. On CelebA-HQ-256, we have $6.99$ FID with $\approx 160$ NFE, which beats the current best record of Kim et al. (2022) among score-based models, $7.16$ FID with $4000$ NFE. Figures below illustrate how Denoising Langevin Gibbs (DLG), which is an instance of DMCMC, successfully accelerates six reverse-SDE/ODE integrators on the task of CIFAR10 and CelebA-HQ-256 image generation.

<p align="center">
  <img src="https://github.com/1202kbs/DMCMC/blob/main/assets/cifar10.png" />
</p>

<p align="center">
  <img src="https://github.com/1202kbs/DMCMC/blob/main/assets/celeba.png" />
</p>
