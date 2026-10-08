
📖 1. Introduction

This project is a compact, from-scratch implementation of a generative network inspired by NVIDIA's StyleGAN (Style Generative Adversarial Network) architecture. Written using TensorFlow and Keras, it scales down the giant, high-resolution original StyleGAN concepts into a lightweight, educational script.
Instead of traditional GANs that feed noise directly into the generator, this model passes random noise (z) through an 8-layer Multi-Layer Perceptron (MLP) to create an intermediate style space (w). 
This style vector then controls the generator's layers using custom Adaptive Instance Normalization (AdaIN) blocks and added noise for fine-grain textures, synthesizing 32x32 images.


📚 Libraries Used
• TensorFlow
• Keras
• NumPy
• Matplotlib
• Python Standard Libraries (os, time, random)

🗄️ Dataset Used
• CIFAR-10

🛠️ Tools Required
• Python (3.9 - 3.11)
• Jupyter Notebook / JupyterLab (or VS Code with Jupyter Extension)
• Google Colab / Kaggle Notebooks (Optional for cloud execution)


⚙️Procedure

1. Preprocessing: Scales a 20,000-image subset of CIFAR-10 to [-1.0, 1.0] and loads them in optimized batches of 64.
2. Latent Mapping: A random noise vector z passes through an 8-layer MLP mapping network to generate an intermediate style vector w.
3. Style Synthesis: The generator discards standard noise inputs; it starts with a static, learned 4×4 constant tensor and upsamples it progressively to 32×32.
4. AdaIN & Noise: At each resolution tier, per-channel random noise is added for fine texturing, and the style vector w controls the features via Adaptive Instance Normalization (AdaIN).
5. Adversarial Training: Uses custom TensorFlow training steps (GradientTape) to optimize the model using the non-saturating logistic GAN loss.
6. Evaluation: Notebook plots cross-layer Style Mixing and smooth Latent Space Interpolation grids.
