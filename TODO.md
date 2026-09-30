# 复现 TODO

标签：🏛️ 经典 · 🚀 前沿 · 🎮 好玩
建议数据集：MNIST / Fashion-MNIST → CIFAR-10 → CelebA-64 → 2D toy（moons / 8-gaussians，用于可视化分布与轨迹）

## 0. 基础设施

- [ ] 统一训练框架（config、logging、checkpoint、seed）
- [ ] 数据集加载：MNIST、CIFAR-10、CelebA、2D toy
- [ ] 评估：FID、IS、NLL / bits-per-dim、采样可视化网格
- [ ] 2D toy 可视化工具（密度图、向量场、采样轨迹动画）

## 1. GAN —— 隐式博弈路线

- [ ] 🏛️ **GAN**（Goodfellow et al., 2014）— 原始 minimax，MLP on MNIST
- [ ] 🏛️ **DCGAN**（Radford et al., 2015）— 卷积架构的标准范式
- [ ] 🏛️ **Conditional GAN**（Mirza & Osindero, 2014）— 类别条件生成
- [ ] 🏛️ **WGAN / WGAN-GP**（Arjovsky et al., 2017; Gulrajani et al., 2017）— Wasserstein 距离 + 梯度惩罚
- [ ] 🏛️ **SN-GAN**（Miyato et al., 2018）— 谱归一化
- [ ] 🎮 **Pix2Pix**（Isola et al., 2017）— 成对图像翻译（草图→图片）
- [ ] 🎮 **CycleGAN**（Zhu et al., 2017）— 非成对图像翻译（马↔斑马、照片↔莫奈）
- [ ] 🏛️🎮 **StyleGAN2**（Karras et al., 2020）— 风格混合、隐空间插值
- [ ] 🚀 **R3GAN**（Huang et al., 2024）— “现代 GAN 基线”，去掉各种 trick

## 2. VAE —— 显式推断路线

- [ ] 🏛️ **Autoencoder**（baseline，对照用）
- [ ] 🏛️ **VAE**（Kingma & Welling, 2013）— 重参数化技巧 + ELBO
- [ ] 🏛️ **Conditional VAE**（Sohn et al., 2015）
- [ ] 🎮 **β-VAE**（Higgins et al., 2017）— 解耦表示，隐变量逐维遍历
- [ ] 🏛️ **VQ-VAE**（van den Oord et al., 2017）— 离散隐空间 + codebook
- [ ] 🚀 **NVAE**（Vahdat & Kautz, 2020）— 深层层级 VAE（可做缩小版）

## 3. 自回归 & Normalizing Flow（对照路线，理解显式似然）

- [ ] 🏛️ **PixelCNN**（van den Oord et al., 2016）— 逐像素自回归
- [ ] 🏛️ **RealNVP**（Dinh et al., 2016）— 耦合层，精确似然
- [ ] 🏛️ **Glow**（Kingma & Dhariwal, 2018）— 可逆 1×1 卷积
- [ ] 🎮 **Neural ODE / FFJORD**（Chen et al., 2018; Grathwohl et al., 2018）— 连续正则化流，Flow Matching 的前身

## 4. Diffusion / Score-based —— 马尔可夫链与 SDE 路线

- [ ] 🏛️ **NCSN**（Song & Ermon, 2019）— Score matching + Langevin 采样
- [ ] 🏛️ **DDPM**（Ho et al., 2020）— 核心必做
- [ ] 🏛️ **DDIM**（Song et al., 2020）— 确定性快速采样
- [ ] 🏛️ **Improved DDPM**（Nichol & Dhariwal, 2021）— cosine schedule、学习方差
- [ ] 🏛️ **Score SDE**（Song et al., 2021）— VP/VE SDE 与 probability flow ODE 的统一视角
- [ ] 🏛️ **Classifier / Classifier-Free Guidance**（Dhariwal & Nichol, 2021; Ho & Salimans, 2022）
- [ ] 🏛️ **Latent Diffusion**（Rombach et al., 2022）— VAE 压缩 + 隐空间扩散（Stable Diffusion 原理）
- [ ] 🚀 **EDM**（Karras et al., 2022）— 扩散设计空间的系统化梳理
- [ ] 🚀 **DiT**（Peebles & Xie, 2023）— Transformer 骨干
- [ ] 🚀 **Consistency Models**（Song et al., 2023）— 一步/少步生成
- [ ] 🚀 **DPM-Solver**（Lu et al., 2022）— 高阶 ODE 采样器
- [ ] 🎮 **SDEdit / Inpainting / RePaint** — 用预训练扩散模型做编辑与补全

## 5. Flow Matching —— 向量场与最优传输路线

- [ ] 🚀 **Flow Matching**（Lipman et al., 2022）— 核心必做，先在 2D toy 上可视化向量场
- [ ] 🚀 **Rectified Flow**（Liu et al., 2022）— 直线路径 + Reflow 拉直
- [ ] 🚀 **Stochastic Interpolants**（Albergo & Vanden-Eijnden, 2023）— 统一 Diffusion 与 Flow
- [ ] 🚀 **OT-CFM / Minibatch OT**（Tong et al., 2023）— 最优传输耦合
- [ ] 🚀 **SiT**（Ma et al., 2024）— Interpolant + Transformer
- [ ] 🚀 **Stable Diffusion 3 式 Rectified Flow Transformer**（Esser et al., 2024）— 缩小版 MM-DiT
- [ ] 🚀 **Shortcut Models / MeanFlow**（Frans et al., 2024; Geng et al., 2025）— 一步生成
- [ ] 🎮 **Discrete Flow Matching**（Gat et al., 2024）— 离散数据（文本/序列）上的流

## 6. 统一视角实验（本仓库的“灵魂”）

- [ ] 同一 2D toy 数据上，并排可视化 GAN / VAE / DDPM / Flow Matching 的采样过程
- [ ] 验证 “Diffusion = 层级马尔可夫 VAE”：从 ELBO 推导 DDPM 损失并实验对照
- [ ] 对比 DDPM(SDE) / DDIM(ODE) / Flow Matching / Rectified Flow 的采样轨迹曲率与步数-质量曲线
- [ ] 同一 backbone、同一数据集下各模型的 FID 与采样速度对比表

## 7. 好玩的 Demo 🎮

- [ ] 隐空间插值动画（VAE / StyleGAN / Diffusion）
- [ ] 人脸风格混合（StyleGAN）
- [ ] 文本条件的小型图像生成（CLIP 文本编码 + Latent Diffusion，Tiny 版）
- [ ] 扩散/流模型生成过程的 GIF：噪声一步步“流”成数字或人脸
- [ ] 音频生成小实验（如 DiffWave 缩小版）
