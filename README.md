# DMCMC

Official PyTorch implementation of [Denoising MCMC for Accelerating Diffusion-Based Generative Models](https://arxiv.org/abs/2209.14593), **ICML 2023 Oral Paper**.

<p align="center">
  <img src="https://github.com/1202kbs/DMCMC/blob/main/assets/sample_gif.gif" />
</p>

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

## How to Run This Code

All main experiments of this paper were performed using the code in the `Demo.ipynb` file. To run this code,

1. Install required packages,
2. Create the directory `./exp/ve` and place score model checkpoints in that directory. We used pre-trained VE NCSN checkpoints provided by Song et al. in [this repository](https://github.com/yang-song/score_sde). Our method is compatible with RVE NCSN models of Kim et al. as well, provided in [this repository](https://github.com/Kim-Dongjun/Soft-Truncation).

## Acknowledgements

- Our code is heavily based on the code of Song et al. in [this repository](https://github.com/yang-song/score_sde).
- FID in our paper was measured using the code in [this repository](https://github.com/mseitzer/pytorch-fid).

## References

If you find the code useful for your research, please consider citing
```bib
@article{
  kim2022dmcmc,
  title={Denoising MCMC for Accelerating Diffusion-Based Generative Models},
  author={Beomsu Kim and Jong Chul Ye},
  journal={arXiv preprint arXiv:2209.14593},
  year={2022}
}
```
