# Awesome 3D Reconstruction Papers

A curated list of papers on 3D reconstruction from top venues (CVPR, ICCV, ECCV, NeurIPS, SIGGRAPH, TPAMI, IJCV, etc.).

> Papers are organized by research topic. Each entry includes the problem addressed, proposed method, and key contributions.

---

## Table of Contents

- [Neural Implicit Representations](#neural-implicit-representations)
- [Neural Radiance Fields (NeRF)](#neural-radiance-fields-nerf)
- [3D Gaussian Splatting](#3d-gaussian-splatting)
- [Multi-View Stereo (MVS)](#multi-view-stereo-mvs)
- [Depth Estimation](#depth-estimation)
- [Point Cloud Processing](#point-cloud-processing)
- [Dynamic Scene Reconstruction](#dynamic-scene-reconstruction)
- [Human Body & Face Reconstruction](#human-body--face-reconstruction)
- [Large-Scale Scene Reconstruction](#large-scale-scene-reconstruction)
- [Generative 3D Reconstruction](#generative-3d-reconstruction)

---

## Format

Each paper entry follows this structure:

| Field | Description |
|---|---|
| **Title** | Paper title with link |
| **Venue** | Conference/Journal + Year |
| **Problem** | What problem does it solve? |
| **Method** | How does it solve it? (1-2 sentences) |
| **Key Contribution** | What's novel? |
| **Code** | Official / third-party implementation |

---

## Neural Implicit Representations

### [Occupancy Networks: Learning 3D Reconstruction in Function Space](https://arxiv.org/abs/1812.03828)
- **Venue:** CVPR 2019
- **Problem:** Traditional 3D representations (voxels, point clouds, meshes) are limited in resolution or topology flexibility.
- **Method:** Represents 3D geometry as the decision boundary of a neural network that predicts occupancy probability for any continuous 3D point.
- **Key Contribution:** First work to use implicit neural functions for 3D reconstruction, enabling arbitrary resolution and topology.
- **Code:** [autonomousvision/occupancy_networks](https://github.com/autonomousvision/occupancy_networks)

---

### [DeepSDF: Learning Continuous Signed Distance Functions for Shape Representation](https://arxiv.org/abs/1901.05103)
- **Venue:** CVPR 2019
- **Problem:** Compact and continuous 3D shape representation that generalizes across shape categories.
- **Method:** Learns a latent-conditioned SDF via auto-decoder; shape is represented as the zero-level set of the learned function.
- **Key Contribution:** Auto-decoder framework for shape embedding without an encoder; enables shape completion and interpolation.
- **Code:** [facebookresearch/DeepSDF](https://github.com/facebookresearch/DeepSDF)

---

## Neural Radiance Fields (NeRF)

### [NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis](https://arxiv.org/abs/2003.08934)
- **Venue:** ECCV 2020
- **Problem:** Novel view synthesis from a sparse set of input images.
- **Method:** Encodes scene as a continuous volumetric radiance field using an MLP; renders via differentiable ray marching.
- **Key Contribution:** Photorealistic novel view synthesis using purely implicit neural representation.
- **Code:** [bmild/nerf](https://github.com/bmild/nerf)

---

### [Instant-NGP: Instant Neural Graphics Primitives with a Multiresolution Hash Encoding](https://arxiv.org/abs/2201.05989)
- **Venue:** SIGGRAPH 2022
- **Problem:** NeRF training is extremely slow (hours per scene).
- **Method:** Replaces MLP input with a multiresolution hash grid encoding, drastically reducing network size and training time.
- **Key Contribution:** Reduces NeRF training from hours to seconds without quality loss.
- **Code:** [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp)

---

### [Mip-NeRF: A Multiscale Representation for Anti-Aliasing Neural Radiance Fields](https://arxiv.org/abs/2103.13415)
- **Venue:** ICCV 2021
- **Problem:** NeRF produces aliasing artifacts when rendering at different scales/resolutions.
- **Method:** Casts conical frustums instead of rays and uses integrated positional encoding to represent regions rather than points.
- **Key Contribution:** Anti-aliased NeRF rendering with improved multi-scale consistency.
- **Code:** [google/mipnerf](https://github.com/google/mipnerf)

---

## 3D Gaussian Splatting

### [3D Gaussian Splatting for Real-Time Radiance Field Rendering](https://arxiv.org/abs/2308.04079)
- **Venue:** SIGGRAPH 2023
- **Problem:** NeRF-based methods are slow at inference/rendering.
- **Method:** Represents scenes as a set of 3D Gaussians with learnable attributes; renders via differentiable tile-based rasterization.
- **Key Contribution:** Real-time (>100 FPS) high-quality novel view synthesis; explicit representation enables fast editing.
- **Code:** [graphdeco-inria/gaussian-splatting](https://github.com/graphdeco-inria/gaussian-splatting)

---

## Multi-View Stereo (MVS)

### [MVSNet: Depth Inference for Unstructured Multi-view Stereo](https://arxiv.org/abs/1804.02505)
- **Venue:** ECCV 2018
- **Problem:** Traditional MVS pipelines require hand-crafted cost volumes and are slow.
- **Method:** Builds a 3D cost volume via differentiable homography warping and regularizes it with a 3D CNN to predict depth maps.
- **Key Contribution:** End-to-end learnable MVS pipeline; cost volume formulation became the standard for learning-based MVS.
- **Code:** [YoYo000/MVSNet](https://github.com/YoYo000/MVSNet)

---

### [IterMVS: Iterative Probability Estimation for Efficient Multi-View Stereo](https://arxiv.org/abs/2112.05126)
- **Venue:** CVPR 2022
- **Problem:** High memory cost of 3D cost volumes in MVS limits resolution and scalability.
- **Method:** Replaces 3D cost volume with a GRU-based iterative depth estimator that maintains a compact per-pixel depth distribution.
- **Key Contribution:** Memory-efficient MVS with competitive accuracy via recurrent depth refinement.
- **Code:** [FangjinhuaWang/IterMVS](https://github.com/FangjinhuaWang/IterMVS)

---

## Depth Estimation

### [DPT: Vision Transformers for Dense Prediction](https://arxiv.org/abs/2103.13413)
- **Venue:** ICCV 2021
- **Problem:** CNN-based depth estimators lose global context due to limited receptive fields.
- **Method:** Uses a ViT backbone with a dense prediction head that reassembles tokens at multiple scales.
- **Key Contribution:** Transformer-based monocular depth estimation with strong global-local feature fusion.
- **Code:** [isl-org/DPT](https://github.com/isl-org/DPT)

---

### [Depth Anything: Unleashing the Power of Large-Scale Unlabeled Data](https://arxiv.org/abs/2401.10891)
- **Venue:** CVPR 2024
- **Problem:** Monocular depth models generalize poorly to unseen scenes due to limited labeled training data.
- **Method:** Trains on 62M unlabeled images via a teacher-student framework with semantic-guided auxiliary supervision.
- **Key Contribution:** State-of-the-art zero-shot monocular depth estimation through large-scale semi-supervised training.
- **Code:** [LiheYoung/Depth-Anything](https://github.com/LiheYoung/Depth-Anything)

---

## Point Cloud Processing

### [PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation](https://arxiv.org/abs/1612.00593)
- **Venue:** CVPR 2017
- **Problem:** Deep networks cannot directly process unordered 3D point clouds.
- **Method:** Applies shared MLPs per point + symmetric aggregation (max pooling) to achieve permutation invariance.
- **Key Contribution:** First deep learning framework directly operating on raw point clouds; foundational for all subsequent work.
- **Code:** [charlesq34/pointnet](https://github.com/charlesq34/pointnet)

---

## Dynamic Scene Reconstruction

### [D-NeRF: Neural Radiance Fields for Dynamic Scenes](https://arxiv.org/abs/2011.13961)
- **Venue:** CVPR 2021
- **Problem:** Standard NeRF cannot handle non-rigid dynamic scenes.
- **Method:** Adds a deformation network that maps each point in observation space to a canonical space before querying the radiance field.
- **Key Contribution:** Extends NeRF to monocular dynamic scene reconstruction via canonical + deformation field decomposition.
- **Code:** [albertpumarola/D-NeRF](https://github.com/albertpumarola/D-NeRF)

---

## Human Body & Face Reconstruction

### [SMPL: A Skinned Multi-Person Linear Model](https://dl.acm.org/doi/10.1145/2816795.2818013)  
- **Venue:** SIGGRAPH Asia 2015
- **Problem:** Realistic and controllable parametric human body model.
- **Method:** Learns a low-dimensional shape + pose parameter space from thousands of registered body scans; deforms via blend skinning.
- **Key Contribution:** The de facto standard parametric body model; used in virtually all human reconstruction and generation work.
- **Code:** [https://smpl.is.tue.mpg.de](https://smpl.is.tue.mpg.de)

---

## Large-Scale Scene Reconstruction

### [Block-NeRF: Scalable Large Scene Neural View Synthesis](https://arxiv.org/abs/2202.05263)
- **Venue:** CVPR 2022
- **Problem:** NeRF cannot scale to city-level scenes due to memory and capacity limits.
- **Method:** Decomposes large scenes into independently trained block-level NeRFs; merges them at inference via appearance matching.
- **Key Contribution:** First NeRF system for city-scale reconstruction from in-the-wild driving data.
- **Code:** N/A (Google internal)

---

## Generative 3D Reconstruction

### [Zero-1-to-3: Zero-shot One Image to 3D Object](https://arxiv.org/abs/2303.11328)
- **Venue:** ICCV 2023
- **Problem:** Single-image 3D reconstruction requires understanding of 3D geometry from 2D priors.
- **Method:** Fine-tunes a diffusion model on synthetic data to generate novel views conditioned on camera pose; lifts to 3D via SDS.
- **Key Contribution:** Leverages 2D diffusion priors for zero-shot single-image novel view synthesis and 3D reconstruction.
- **Code:** [cvlab-columbia/zero123](https://github.com/cvlab-columbia/zero123)

---

## Contributing

Feel free to open a PR to add papers. Please follow the format above and place the paper in the correct category.

## License

MIT
