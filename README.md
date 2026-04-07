# Awesome 3D Reconstruction Papers

A curated list of papers on 3D reconstruction from top venues (CVPR, ICCV, ECCV, NeurIPS, SIGGRAPH, TPAMI, IJCV, etc.).

> Papers are organized by research topic and roughly follow the historical development of the field. Each entry includes the problem addressed, proposed method, and key contributions.

---

## Table of Contents

- [Point Cloud Processing](#point-cloud-processing) ← The starting point for deep learning in 3D processing
- [Multi-View Stereo (MVS)](#multi-view-stereo-mvs) ← Classic geometry + learning transformation
- [Depth Estimation](#depth-estimation) ← The foundation of 2D to 3D perception
- [Neural Implicit Representations](#neural-implicit-representations) ← The revolution of implicit representations
- [Neural Radiance Fields (NeRF)](#neural-radiance-fields-nerf) ← The pinnacle of rendering with implicit representations
- [Dynamic Scene Reconstruction](#dynamic-scene-reconstruction) ← Temporal extension of NeRF
- [Human Body & Face Reconstruction](#human-body--face-reconstruction) ← Parameterized modeling branch
- [Large-Scale Scene Reconstruction](#large-scale-scene-reconstruction) ← Scale expansion of NeRF
- [Generative 3D Reconstruction](#generative-3d-reconstruction) ← Involvement of generative models
- [3D Gaussian Splatting](#3d-gaussian-splatting) ← A new explicit representation paradigm
- [Hybrid Representations](#hybrid-representations) ← Exploration of explicit and implicit fusion
- [Feed-Forward 3D Reconstruction](#feed-forward-3d-reconstruction) ← Current frontier: unified end-to-end approach
- [Remote Sensing 3D Reconstruction](#remote-sensing-3d-reconstruction) ← Aerial/satellite/uav imagery meets neural rendering
- [3D Reconstruction with CAD](#3d-reconstruction-with-computer-aided-design-cad) 
- [3D Reconstruction with Uncertainty Quantification](#3d-reconstruction-with-uncertainty-quantification)
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

## 📝 Conventional Commits

This project adopts the [Conventional Commits](https://www.conventionalcommits.org/) specification, please use the following format to submit:

| Type | Icon | Des | Example |
|------|------|------|------|
| `docs` | 📝 | update doc | `📝 docs: update API documentation` |

---

## Point Cloud Processing

### [PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation](https://arxiv.org/abs/1612.00593)
- **Venue:** CVPR 2017
- **Problem:** Deep networks cannot directly process unordered 3D point clouds.
- **Method:** Applies shared MLPs per point + symmetric aggregation (max pooling) to achieve permutation invariance.
- **Key Contribution:** First deep learning framework directly operating on raw point clouds; foundational for all subsequent work.
- **Code:** [charlesq34/pointnet](https://github.com/charlesq34/pointnet)

---

### [PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space](https://arxiv.org/abs/1706.02413)
- **Venue:** NeurlPS 2017
- **Problem:** Point cloud data is of great importance in fields such as 3D scanning, but existing deep learning methods, such as PointNet, have failed to effectively capture the local structure of point clouds, limiting their application in complex scenes.
- **Method:** To address the above issues, the author proposed PointNet++, a novel hierarchical neural network architecture that recursively applies PointNet on nested partitions of point sets to learn local features of different scales.
- **Key Contribution:** Hierarchical Point Set Feature Learning; Robust Feature Learning under Non-Uniform Sampling Density; Point Feature Propagation for Set Segmentation.
- **Code:** [charlesq34/pointnet](https://github.com/charlesq34/pointnet2)

---

## Multi-View Stereo (MVS)

### [MVSNet: Depth Inference for Unstructured Multi-view Stereo](https://arxiv.org/abs/1804.02505)
- **Venue:** ECCV 2018
- **Problem:** Traditional MVS pipelines require hand-crafted cost volumes and are slow.
- **Method:** Builds a 3D cost volume via differentiable homography warping and regularizes it with a 3D CNN to predict depth maps.
- **Key Contribution:** End-to-end learnable MVS pipeline; cost volume formulation became the standard for learning-based MVS.
- **Code:** [YoYo000/MVSNet](https://github.com/YoYo000/MVSNet)

---

### [Recurrent MVSNet for High-resolution Multi-view Stereo Depth Inference](https://arxiv.org/abs/1902.10556)
- **Venue:** CVPR 2019
- **Problem:** The scalability issue of Learning-based multi-view stereo matching (MVS) when dealing with high-resolution scenes.
- **Method:** The paper solves the scalability problem of high-resolution MVS reconstruction by proposing the R-MVSNet (Recurrent Multi-view Stereo Network) framework.
- **Key Contribution:** Sequential Regularization; Depth-oriented stacked GRU architecture.
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

### [Vision Transformers for Dense Prediction](https://arxiv.org/abs/2103.13413)
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
- **Venue:** ECCV 2020 (oral)
- **Problem:** Novel view synthesis from a sparse set of input images.
- **Method:** Encodes scene as a continuous volumetric radiance field using an MLP; renders via differentiable ray marching.
- **Key Contribution:** Photorealistic novel view synthesis using purely implicit neural representation.
- **Code:** [bmild/nerf](https://github.com/bmild/nerf)

---

### [Mip-NeRF: A Multiscale Representation for Anti-Aliasing Neural Radiance Fields](https://arxiv.org/abs/2103.13415)
- **Venue:** ICCV 2021
- **Problem:** NeRF produces aliasing artifacts when rendering at different scales/resolutions.
- **Method:** Casts conical frustums instead of rays and uses integrated positional encoding to represent regions rather than points.
- **Key Contribution:** Anti-aliased NeRF rendering with improved multi-scale consistency.
- **Code:** [google/mipnerf](https://github.com/google/mipnerf)

---

### [Instant-NGP: Instant Neural Graphics Primitives with a Multiresolution Hash Encoding](https://arxiv.org/abs/2201.05989)
- **Venue:** SIGGRAPH 2022
- **Problem:** NeRF training is extremely slow (hours per scene).
- **Method:** Replaces MLP input with a multiresolution hash grid encoding, drastically reducing network size and training time.
- **Key Contribution:** Reduces NeRF training from hours to seconds without quality loss.
- **Code:** [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp)

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

## 3D Gaussian Splatting

### [3D Gaussian Splatting for Real-Time Radiance Field Rendering](https://arxiv.org/abs/2308.04079)
- **Venue:** SIGGRAPH 2023
- **Problem:** NeRF-based methods are slow at inference/rendering.
- **Method:** Represents scenes as a set of 3D Gaussians with learnable attributes; renders via differentiable tile-based rasterization.
- **Key Contribution:** Real-time (>100 FPS) high-quality novel view synthesis; explicit representation enables fast editing.
- **Code:** [graphdeco-inria/gaussian-splatting](https://github.com/graphdeco-inria/gaussian-splatting)

---

### [Proxy-GS: Unified Occlusion Priors for Training and Inference in Structured 3D Gaussian Splatting](https://visionary-laboratory.github.io/Proxy-GS/)
- **Venue:** CVPR 2026
- **Problem:** The original 3DGS often generates a large number of redundant Gauss and ignores the scene geometry.
- **Method:** Building a lightweight proxy mesh that can obtain the occlusion depth map within 1ms at a resolution of 1000×1000, and serve two things: anchor/Gaussian culturing during inference and proxy-guided densification during training.
- **Key Contribution:** Proxy-guided training pipeline; Proxy-guided densification.
- **Code:** [Visionary-Laboratory/Proxy-GS](https://github.com/Visionary-Laboratory/Proxy-GS)

---

## Hybrid Representations

### [NeRF Is a Valuable Assistant for 3D Gaussian Splatting](https://openaccess.thecvf.com/content/ICCV2025/html/Fang_NeRF_Is_a_Valuable_Assistant_for_3D_Gaussian_Splatting_ICCV_2025_paper.html)
- **Venue:** ICCV 2025
- **Problem:** Although 3DGS is fast, its quality is highly dependent on initialization and lacks spatial perception and correlation between Gauss, resulting in an unsmooth spatial transition.
- **Method:** It proposes a "joint optimization" framework that enables NeRF to "assist" 3DGS throughout the training process to overcome its inherent flaws.
- **Key Contribution:** Sharing & Initialization; Residual Vectors; Joint Optimization.
- **Code:** None.

---

### [HyRF: Hybrid Radiance Fields for Memory-efficient and High-quality Novel View Synthesis](https://arxiv.org/abs/2509.17083)
- **Venue:** NeurlPS 2025
- **Problem:** Another fatal weakness of 3DGS is its huge memory overhead. Each Gaussian point needs to store a large number of parameters (48 SH coefficients for color and 7 for shape), resulting in models often taking hundreds of MB or even over GB.
- **Method:** HyRF (Hybrid Radiation Field) presents an extremely ingenious hybrid representation, perfectly combining the "compactness" of NeRF and the "rapidity" of 3DGS.
- **Key Contribution:** Hybrid Decomposition; Decoupled Architecture; Background Rendering.
- **Code:** [wzpscott/hybrid-radiance-fields](https://github.com/wzpscott/hybrid-radiance-fields).

---

## Feed-Forward 3D Reconstruction

### [VGGT: Visual Geometry Grounded Transformer](https://openaccess.thecvf.com/content/CVPR2025/html/Wang_VGGT_Visual_Geometry_Grounded_Transformer_CVPR_2025_paper.html)
- **Venue:** CVPR 2025 (Best Paper)
- **Problem:** Existing 3D reconstruction methods require per-scene optimization or complex multi-stage pipelines, making them slow and hard to generalize.
- **Method:** A feed-forward transformer that takes an arbitrary number of images as input and directly regresses all 3D scene attributes (camera poses, depth maps, point maps, 3D points) in a single forward pass.
- **Key Contribution:** Unified feed-forward architecture for multi-view 3D reconstruction without any test-time optimization; achieves state-of-the-art across multiple 3D tasks simultaneously.
- **Code:** [facebookresearch/vggt](https://github.com/facebookresearch/vggt)

---

### [LESS GAUSSIANS, TEXTURE MORE: 4K FEED-FORWARD TEXTURED SPLATTING](https://arxiv.org/abs/2603.25745)
- **Venue:** LCLR 2026
- **Problem:** Feed-forward Gaussian splatting methods scale poorly to high-resolution inputs because they tie geometry and appearance to per-pixel primitives, causing the number of Gaussians and computation to explode with image resolution.
- **Method:** The paper predicts a compact set of textured Gaussian primitives that decouple geometry from appearance by attaching learned texture maps to each primitive.
- **Key Contribution:** It enables high-resolution, optimization-free feed-forward novel view synthesis with far fewer Gaussians while preserving or improving rendering quality.
- **Code:** [coming soon](https://yxlao.github.io/lgtm/)

---

## Remote Sensing 3D Reconstruction

### [ShadowGS: Shadow-Aware 3D Gaussian Splatting for Satellite Imagery](https://arxiv.org/abs/2601.00939)
- **Venue:** arxiv 2026
- **Problem:**  In multi-temporal satellite images, prevalent shadows exhibit significant inconsistencies due to varying illumination conditions.
- **Method:**  The paper propose ShadowGS, a novel framework based on 3DGS. It leverages a physics-based rendering equation from remote sensing, combined with an efficient ray marching technique, to precisely model geometrically consistent shadows while maintaining efficient rendering. 
- **Key Contribution:** ShadowGS; Shadow consistency constraint; Shadow map prior.
- **Code:** Not yet disclosed.

---
## 3D Reconstruction with Computer-Aided Design (CAD)

### [DeepCAD: A Deep Generative Network for Computer-Aided Design Models](https://openaccess.thecvf.com/content/ICCV2021/papers/Wu_DeepCAD_A_Deep_Generative_Network_for_Computer-Aided_Design_Models_ICCV_2021_paper.pdf)
- **Venue:** ICCV 2021
- **Problem:** Point cloud to CAD
- **Method:** This paper is the **first** 3D generative model for a sequence of computer-aided design (CAD) operations, rather than voxels, point clouds, and polygon meshes, like the previous works did. The network is based on Transformer and CAD operations are treated as natural languages.
- **Key Contributions:** Transformer-based CAD generator; A publicly available dataset on learning-based CAD designs.
- **Code:** [rundiwu/DeepCAD](https://github.com/rundiwu/DeepCAD)


### [CADTalk: An Algorithm and Benchmark for Semantic Commenting  of CAD Programs](https://openaccess.thecvf.com/content/CVPR2024/papers/Yuan_CADTalk_An_Algorithm_and_Benchmark_for_Semantic_Commenting_of_CAD_CVPR_2024_paper.pdf)
- **Venue:** CVPR 2024
- **Problem:** OpenSCAD Code to Comments
- **Method:** The paper first introduces the problem of semantic commenting CAD programs, wherein the goal is to segment the input program into code blocks corresponding to semantically meaningful shape parts and assign a semantic label to each block. It solves the problem by combining program parsing with visual-semantic analysis afforded by recent advances in foundational language and vision models.
- **Key Contribution:** A new task of semantic commenting CAD programs.
- **Code:** [CADTalk](https://enigma-li.github.io/CADTalk/)


### [CADCrafter: Generating Computer-Aided Design Models from Unconstrained Images](https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_CADCrafter_Generating_Computer-Aided_Design_Models_from_Unconstrained_Images_CVPR_2025_paper.pdf)
- **Venue:** CVPR 2025
- **Problem:** Image to CAD
- **Method:** The paper proposes an image-to-parametric CAD model generation framework that trains solely on synthetic textureless CAD data while testing on real-world images. To impose geometric validity constraints, the direct preference optimization (DPO) is employed to fine-tune our model with the automatic code checker feedback on CAD sequence quality. A real-world dataset is also collected
- **Key Contribution:** A latent diffusion-based image-to-CAD framework; An automatic code checker; A dataset of unconstrained 3D printed CAD images paired with CAD commands.
- **Code:** Not yet disclosed.


### [CADDreamer: CAD Object Generation from Single-view Images](https://openaccess.thecvf.com/content/CVPR2025/papers/Li_CADDreamer_CAD_Object_Generation_from_Single-view_Images_CVPR_2025_paper.pdf)
- **Venue:** CVPR 2025
- **Problem:** Image to CAD
- **Method:** The paper proposes a novel approach for generating boundary representations (B-rep) of CAD objects from a single image. CADDreamer employs a primitive-aware multi-view diffusion model that captures both local geometric details and high-level structural semantics during the generation process.
- **Key Contribution:** CADDreamer Framework; Semantic-enhanced Multi-view 2D Diffusion; Geometry Optimization Algorithm; Topology-preserving B-rep Construction.
- **Code:** Not yet disclosed.


### [CAD-Llama: Leveraging Large Language Models for Computer-Aided Design  Parametric 3D Model Generation](https://openaccess.thecvf.com/content/CVPR2025/html/Li_CAD-Llama_Leveraging_Large_Language_Models_for_Computer-Aided_Design_Parametric_3D_CVPR_2025_paper.html)
- **Venue:** CVPR 2025
- **Problem:** Text to CAD
- **Method:** This study investigates the generation of parametric sequences for computer-aided design (CAD) models using LLMs. The paper presents CAD-Llama, a framework designed to enhance pretrained LLMs for generating parametric 3D CAD models.
- **Key Contributions:** A novel unified framework to generate CAD based on LLMs; A hierarchical annotation pipeline; An adaptive pretraining paradigm.
- **Code:** Not yet disclosed.

---
## 3D Reconstruction with Uncertainty Quantification


### [Stochastic Neural Radiance Fields: Quantifying Uncertainty in Implicit 3D Representations](https://ieeexplore.ieee.org/document/9665942)
- **Venue:** 3DV 2021
- **Problem:** UQ for NVS
- **Method:** This study proposes a generalization of standard NeRF that learns a probability distribution over all the possible radiance fields modeling the scene. This distribution allows to quantify the uncertainty associated with the scene information provided by the model. Optimization is posed as a **Bayesian learning problem** that is efficiently addressed using the **Variational Inference framework**.
- **Key Contributions:** First paper to incorporate uncertainty estimation into NeRF, a learning procedure based on Variational Inference
- **Code:** Not found


### [Conditional-Flow NeRF: Accurate 3D Modelling with Reliable Uncertainty Quantification](https://arxiv.org/abs/2203.10192)
- **Venue:** ECCV 2022
- **Problem:** UQ for NVS
- **Method:** This study proposes a novel probabilistic framework to incorporate uncertainty quantification into NeRF-based approaches. In contrast to previous approaches enforcing strong constraints over the radiance field distribution, This method learns it in a flexible and fully data-driven manner by coupling **Latent Variable Modelling** and **Conditional Normalizing Flows**.
- **Key Contributions:** Modelling Radiance-Density Distributions with Normalizing Flows, Latent Variable Modelling for Radiance Fields Distributions.
- **Code:** [poetrywanderer/CF-NeRF](https://github.com/poetrywanderer/CF-NeRF?tab=readme-ov-file)



---

## Contributing

Feel free to open a PR to add papers. Please follow the format above and place the paper in the correct category.

## License

MIT
