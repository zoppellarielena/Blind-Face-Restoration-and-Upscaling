# Simulating Real-World Challenges: Blind Face Restoration and Upscaling

This project focuses on Blind Face Restoration (BFR), aiming to reconstruct high-quality face images from blind images—images that underwent an unknown degradation process. Unlike non-blind tasks, the degree of deterioration may vary among training images, since different standard image degradation techniques are applied in random combinations of intensities. Thus, the model aims to build a model applicable in real-world scenarios where the degradation process is unknown.

To increase the model's applicability to truly degraded images, we chose to work with the [Labeled Faces in the Wild dataset (LFW)](https://vis-www.cs.umass.edu/lfw/), which lacks facial alignment. This characteristic allows the dataset to capture faces in various natural poses, sometimes partially covered by hands or hats.

The project focuses on two main objectives:

1. The restoration of 16x16 blind face images to 128x128, simulating scenarios with distant or challenging conditions.
2. Reconstruction of standard 128x128 face images.
   
The employed models adapt [Kim et al.'s]([https://website-name.com](https://arxiv.org/abs/1908.08239)) progressive 3-step architecture, initially designed for Face Super Resolution. The adaptation includes incorporating facial landmarks and introducing an encoder for 128x128 input image performance.

Model training employs perceptual and attention on landmarks losses, dynamically weighted to achieve a balance between stability and emphasis on attention to facial details.

The project's success is measured using a broad range of evaluation metrics, including PSNR, SSIM, MS-SIM, LPIPS, NIQE, and FID, to evaluate both image similarity and image realism. The overall batch metric results, shown in the table below, indicate that although the model was not always capable of increasing pixel-wise distances, it significantly improved the realism of deteriorated images.

|                 | PSNR $\uparrow$ | SSIM $\uparrow$ | MS-SIM $\uparrow$ | LPIPS $\downarrow$ | NIQE $\downarrow$ | FID $\downarrow$ |
| --------------- | ---- | ---- | ------ | ----- | ---- | --- |
| blind img 16x16 | 20.1 $\pm$ 0.2 | 0.59 $\pm$ 0.01 | 0.818 $\pm$ 0.002 | 0.468 $\pm$ 0.003 | 16.78 $\pm$ 0.05 | 240 $\pm$ 4 |
| pred img 16x16 | 20.6 $\pm$ 0.3 | 0.65  $\pm$ 0.01 | 0.862  $\pm$ 0.004 | 0.295  $\pm$ 0.006 | 7.9  $\pm$ 0.3 | 40  $\pm$ 2 |
| blind img 128x128 | 21.1 $\pm$ 0.7 | 0.57 $\pm$ 0.03 | 0.83 $\pm$ 0.02 | 0.52 $\pm$ 0.03 | 9.8 $\pm$ 0.5 | 151 $\pm$ 14 |
| pred img 128x128 | 22.0 $\pm$ 0.4 | 0.65 $\pm$ 0.01 | 0.862 $\pm$ 0.009 | 0.31 $\pm$ 0.01 | 6.8 $\pm$ 0.2 | 35 $\pm$ 2 |

The project was conducted as part of the exam of *Vision and Cognitive Systems* course of University of Padova, academic year 2023-2024. It was developed in January 2024 by the team composed by:
* Golan Rodrigo
* Zoppellari Elena
