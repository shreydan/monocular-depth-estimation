# Monocular Depth Estimation

- Kaggle notebook:  [shreydan/monocular-depth-estimation-nyuv2](https://www.kaggle.com/code/shreydan/monocular-depth-estimation-nyuv2)
- Model details:
  - encoder model: resnext50 (Imagenet pretrained)
  - decoder model: UNet++ ([PyTorch Segmentation Models](https://github.com/qubvel/segmentation_models.pytorch))
- dataset: [NYUv2 depth](https://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html)
- metrics: 
  - Structural Similarity Index Measure: SSIM is used for measuring the similarity between two images.
  - Mean Squared Error
- training parameters:
  - AdamW optim
  - lr: 1e-3 scheduled with OneCycleLR
  - mixed-precision training with fp16
  
## Metrics

| epoch | loss_train | loss_val | ssim_train | ssim_val | mse_train | mse_val |
|---|---|---|---|---|---|---|
| 0 | 0.095343 | 0.009658 | 0.575013 | 0.769732 | 0.095367 | 0.009678 |
| 1 | 0.010186 | 0.005739 | 0.841523 | 0.867149 | 0.010186 | 0.005754 |
| 2 | 0.010407 | 0.004536 | 0.872432 | 0.888866 | 0.010409 | 0.004553 |
| 3 | 0.006833 | 0.003201 | 0.897906 | 0.903832 | 0.006834 | 0.003213 |
| 4 | 0.005041 | 0.0028 | 0.91009 | 0.90911 | 0.005041 | 0.002806 |


## Results on test dataset:

- brighter the area, farther away it is in the image. brighter => more depth
- predicted depth maps are grayscale, a color gradient map is applied for visual purposes only.

![results](results.png)