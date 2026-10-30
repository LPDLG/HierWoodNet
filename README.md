# HierWoodNet

**HierWoodNet: HierStyle Multi-scale Semantic Style Transfer Method for Chinese Woodblock Painting**

Project page for our manuscript, currently under review at *Scientific Reports*.

## Abstract

Woodblock painting, a traditional Chinese intangible cultural heritage, is known for its vivid colors and distinctive textures. However, modern lifestyles and declining cultural inheritance have led to risks of style loss and discontinuity. AI-based image style transfer offers a promising avenue for preserving and creating woodblock art. However, existing methods struggle with semantic feature extraction, style consistency, and color modeling in this domain. To address these challenges, we propose a hierarchical woodblock style transfer network. Our approach introduces a Content-Aware Positional Encoder based on the Transformer architecture, which enhances multi-scale feature representation and global structural perception. This helps preserve content during style transfer. We further present a HierStyle Encoder that learns rich, hierarchical style features from data, enabling fine-grained control over the transfer process and improving semantic and textural coherence. A progressive decoder integrates multi-stage upsampling with cross-layer connections to preserve semantic structure while injecting detailed style features. Finally, the ChromaNova Color Decoder dynamically optimizes color representation through a multi-dimensional color loss function that considers both color contrast and distribution differences. Quantitative experiments show that our method achieves the best PSNR, FID, LPIPS, and NIMA scores among the evaluated methods, supported by qualitative comparisons on multi-color woodblock style transfer.

## Code and data availability

The source code, trained models, and data resources will be made publicly available after the paper is accepted. This repository currently provides the project overview and selected experimental results.

The data release will include dataset documentation, data splits, and access instructions. Third-party datasets will be accessed through their original sources and remain subject to their original terms of use.

## Selected experimental results

The following values are reported in the current manuscript. The main quantitative comparison uses CelebA content images and WoodCut style references. Higher values are better for SSIM, PSNR, NIMA, and CLIP. Lower values are better for FID and LPIPS. PSNR is reported in dB. Best results in each column are shown in **bold**.

### Comparison with existing methods

| Method | SSIM ↑ | PSNR ↑ | FID ↓ | LPIPS ↓ | NIMA ↑ | CLIP ↑ |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: |
| CAST | 0.849 | 25.416 | 121.416 | 0.271 | 4.77 | 0.2157 |
| StyTr² | 0.856 | 26.133 | 120.467 | 0.250 | 4.83 | 0.2113 |
| AdaAttN | 0.825 | 23.092 | 125.902 | 0.268 | 5.16 | 0.1983 |
| SANet | 0.817 | 22.783 | 124.433 | 0.284 | 5.33 | 0.2022 |
| StyleDiffusion | **0.882** | 25.417 | 121.102 | 0.253 | 5.49 | **0.2256** |
| ContextDiff | 0.853 | 26.593 | 119.734 | 0.244 | 5.28 | 0.2145 |
| StyleSSP | 0.844 | 25.954 | 118.537 | 0.251 | 5.32 | 0.2227 |
| HierWoodNet (Ours) | 0.873 | **27.101** | **118.032** | **0.241** | **5.54** | 0.2238 |

HierWoodNet achieves the highest PSNR and NIMA, the lowest FID and LPIPS, and the second-highest SSIM and CLIP scores among the evaluated methods.

[Download comparison results (CSV)](results/main_comparison.csv)

### Component ablation

| Variant | SSIM ↑ | PSNR ↑ | FID ↓ | LPIPS ↓ | NIMA ↑ | CLIP ↑ |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: |
| w/o HierStyle | 0.830 | 24.416 | 183.611 | 0.273 | 5.32 | 0.2079 |
| w/o ChromaNova | 0.849 | 21.182 | 162.402 | 0.291 | 4.99 | 0.1917 |
| w/o MDC Loss | 0.865 | 23.184 | 159.930 | 0.287 | 5.44 | 0.2106 |
| HierWoodNet (Ours) | **0.873** | **27.101** | **118.032** | **0.241** | **5.54** | **0.2238** |

Removing ChromaNova reduces PSNR by 5.919 dB, while omitting the MDC loss reduces PSNR by 3.917 dB. The full model achieves the best scores across all six metrics in this ablation.

[Download component ablation results (CSV)](results/component_ablation.csv)
