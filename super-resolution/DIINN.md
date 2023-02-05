# Paper

Title: Single Image Super-Resolution via a Dual Interactive Implicit Neural Network
Authors: Nguyen and Beksi, The University of Texas at Arlington, Robotic Vision Lab
Link: https://arxiv.org/abs/2210.12593
Code: https://github.com/robotic-vision-lab/Dual-Interactive-Implicit-Neural-Network
Keywords: super resolution, implicit neural representations

# Summary

## Background

Work in the area of the single image super resolution (SISR). More concretely, in the area of architectures that handles arbitrary scale factors. For this, they use neural fields (implicit neural networks).

LR - low resolution
HR - high resolution
LIIF - previous method this work is partially based on ([Learning Continuous Image Representation with Local Implicit Image Function](https://www.semanticscholar.org/paper/Learning-Continuous-Image-Representation-with-Local-Chen-Liu/767a6054796e2e6c1de453afab0e05e55aadf825))

PSRN - Peak Signal to Noise Ratio


## What
Main idea, innovations, practical applications

1. Innovation: new architecture for SISR task that handles arbitrary upscale target size with implicit decoder.
2. Main idea: have a separate processing branches for features and for spatial coordinates (with communication channels between them) 
3. Beyond SISR with arbitrary scale factors, I think this approach can be useful for other applications of neural fields (e.g. NERF) 
![](/attachments/Pasted%20image%2020230205200307.png)

## How

1. Encoder + Dual interactive implicit decoder. Encoder arch not very important, can be any CNN that outputs the same spatial size as input LR image
2. Use feature unfolding. Not completely sure, but it looks like making feature map deeper by concatenating features from 3x3 neighborhood
3. Decoder eats deep features from encoder, and coordinate features. Coordinates are both global for the image, and relative (to the nearest LR pixel)
4. MLP architecture is similar to work [Modulated Periodic Activations for Generalizable Local Functional Representations](https://www.semanticscholar.org/paper/Modulated-Periodic-Activations-for-Generalizable-Mehta-Gharbi/6151370f30790baaacd4835aa9f45b852b5f959a)
5. MLP has 4 layers with 256 hidden size. They implement the MLPs as convolutional layers with 256 kernels of size 1
6. Encoder outputs the feature map with 64 channels of the LR image size. Nearest interpolation upsamples it to the target HR size.


## Results

1. It is better then LIIF both in PSNR and speed (and other SR methods with arbitrary scale factors support)
2. Compared to LIIF, DIINN produces sharper edges and details.