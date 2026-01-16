# Image Colorization using CNN and GAN (U-Net + PatchGAN)

## Overview
This repository presents a deep learning–based approach for automatic image colorization. Two models are implemented and compared:

- A CNN-based colorization model serving as a baseline  
- A GAN-based colorization model using U-Net as the generator and PatchGAN as the discriminator  

The project focuses on understanding how adversarial learning improves perceptual quality over traditional regression-based approaches.

---

## Objective
Image colorization is an ill-posed problem where multiple valid color mappings may exist for a single grayscale image. The objectives of this project are:

- To establish a stable CNN baseline for grayscale-to-color mapping  
- To apply a GAN framework to enhance visual realism  
- To analyze differences in sharpness, texture, and color diversity between CNN and GAN models  

---

## Dataset
The experiments are conducted on the CIFAR-10 dataset, which consists of 60,000 RGB images of size 32×32.

- 50,000 images for training  
- 10,000 images for validation  

Images are converted from RGB to LAB color space, where:
- The **L channel** represents luminance and is used as input  
- The **ab channels** represent chrominance and are used as targets  

---

## Methodology

### CNN-Based Colorization
The CNN model follows a supervised learning approach:

- Input: L channel  
- Output: ab channels  
- Architecture: Convolutional encoder–decoder  
- Loss function: Mean Squared Error (MSE)  

This model produces stable color predictions but tends to generate smooth and conservative results.

---

### GAN-Based Colorization

#### Generator
- Architecture: U-Net  
- Input: L channel  
- Output: ab channels  
- Skip connections preserve spatial and structural information  

#### Discriminator
- Architecture: PatchGAN  
- Evaluates realism at the patch level  
- Input: Concatenation of L and ab channels  

#### Loss Functions
- Adversarial loss to encourage realistic color distributions  
- L1 loss to enforce similarity with ground-truth colors  

The combination of these losses balances correctness and perceptual realism.

---

## Results and Observations
- The CNN model provides consistent but less vivid colorization results  
- The GAN model produces sharper, more vibrant, and visually realistic outputs  
- Adversarial training significantly improves texture and contrast representation  

---

## Key Takeaways
- Pixel-wise losses alone are insufficient for perceptually realistic colorization  
- GANs enhance realism by learning data distributions rather than averages  
- A CNN baseline is essential for meaningful comparison  
- Combining reconstruction and adversarial losses yields superior results  

