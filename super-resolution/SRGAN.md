# Paper

Title: **Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network**

Authors: Twitter (Christian Ledig et al)
Link: https://arxiv.org/pdf/1609.04802v5.pdf
Code: https://github.com/Lornatang/SRGAN-PyTorch

Keywords: super resolution, GAN



# Summary

## Interesting previous work

- **Single image super-resolution from transformed self-exemplars**
	- This paradigm of self-similarity is also employed in Huang et al.[[31](https://ar5iv.labs.arxiv.org/html/1609.04802v5#bib.bib31)], where self dictionaries are extended by further allowing for small transformations and shape variations.
- **Convolutional sparse coding for image super-resolution.**
	- Gu et al. [[25](https://ar5iv.labs.arxiv.org/html/1609.04802v5#bib.bib25)] proposed a convolutional sparse coding approach that improves consistency by processing the whole image rather than overlapping patches.
- **Multi-scale dictionary for single image super-resolution.**
	- Zhang et al. [[70](https://ar5iv.labs.arxiv.org/html/1609.04802v5#bib.bib70)] propose a multi-scale dictionary to capture redundancies of similar image patches at different scales.


## What

- Upscaling images up to x4 
- New SoTa (09 2016) for x4 SR (PSNR/SSIM) with 16 block SRResNet for MSE
- SRGAN - new sota, but can't measure directly, with people (mean opinion score)

## How

### Loss

- content_loss + $10^{-3}$ adversarial_loss
	- Content loss is MSE of VGG features, or simply MSE in non-top run

### Architecture

![](Pasted%20image%2020230306174008.png)

### Training details

- 350k images from ImageNet
- Batch: 16 random 96x96
- Input images [0, 1], Output: [-1, 1]
- SRResNet: $10^{-4}$ for $10^6$ iterations

## Results

- They make a hypothesis that MSE pushes reconstruction out of the manifold, as a mean between all possible HR images
- Their SRResNet was SoTa in terms of PNR/SSIM, and GAN - SoTa in terms of human-measured mean opinion score (MOS)
