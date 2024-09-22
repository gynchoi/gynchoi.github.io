---
title: "DragText: Rethinking Text Embedding in Point-based Image Editing"
date: 2024-08-31
description: "WACV 2025 Round 1 Early Acceptance Paper"
tags: ["wacv", "conference-paper"]
---
{{< katex >}}
{{< lead >}}
We propose <b>DragText</b>, which optimizes text embedding in conjunction with the dragging process to pair with the modified image embedding.
{{< /lead >}}

<div align="left" style="margin-top: -50px;">
<a href="https://arxiv.org/abs/2407.17843" style="display: inline-block;"><img alt='arXiv' src="https://img.shields.io/badge/arXiv-b31b1b.svg?style=flat-square&logo=arxiv"></a>
<a href="https://github.com/MICV-yonsei/DragText" style="display: inline-block;"><img alt='Code' src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github"></a>
<a href="https://micv-yonsei.github.io/dragtext2025/" style="display: inline-block;"><img alt='Project Page' src="https://img.shields.io/badge/Project page-orange?style=flat-square&logo="></a>
</div>

## Abstract
Point-based image editing enables accurate and flexible control through content dragging. However, the role of text embedding in the editing process has not been thoroughly investigated. A significant aspect that remains unexplored is the interaction between text and image embeddings. 

In this study, we show that during the progressive editing of an input image in a diffusion model, the text embedding remains constant. As the image embedding increasingly diverges from its initial state, the discrepancy between the image and text embeddings presents a significant challenge. Moreover, we found that the text prompt significantly influences the dragging process, particularly in maintaining content integrity and achieving the desired manipulation. 

To utilize these insights, we propose DragText, which optimizes text embedding in conjunction with the dragging process to pair with the modified image embedding. Simultaneously, we regularize the text optimization process to preserve the integrity of the original text prompt. Our approach can be seamlessly integrated with existing diffusion-based drag methods with only a few lines of code.

## Method
<img src="./thumb.png">
During the edit, the original image embedding \( \mathbf{z}_t \) naturally deviates to the dragged image latent vector \( \bar{\mathbf{z}}_t \). With no text optimization, the corresponding text embedding \(\mathbf{c}\) is decoupled from \( \bar{\mathbf{z}}_t \). Hence, optimal text embedding \(\hat{\mathbf{c}} \)coupled with dragged images has to be acquired to make the optimal latent vector \( \hat{\mathbf{z}}_t \)which then holds the related semantics via text.  


<img src="./pipeline.png">
In DragText, the image \(\mathbf{x}_0\) is mapped to a low-dimensional space through a VAE encoder, and the text is encoded by a CLIP text encoder as the text embedding \(\mathbf{c}\). Through DDIM inversion with \(\mathbf{c}\), the latent vector \( \mathbf{z}_t \) is obtained. At time step \(t=35\), \( \mathbf{z}_t^0 \) and \(\mathbf{c}\) are optimized to \( \hat{\mathbf{z}}_t^k \) and \(\hat{\mathbf{c}} \) by iterating with motion supervision (M.S.) and point tracking (P.T.) \(k\)-times.

### Citation
```
@article{choi2024dragtext,
  title={DragText: Rethinking Text Embedding in Point-based Image Editing},
  author={Choi, Gayoon and Jeong, Taejin and Hong, Sujung and Joo, Jaehoon and Hwang, Seong Jae},
  journal={arXiv preprint arXiv:2407.17843},
  year={2024}
}
```