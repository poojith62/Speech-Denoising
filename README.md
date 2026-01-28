# 🎙️ Speech Denoising using Deep Learning (U-Net)

## 📌 Overview
This project implements a **speech denoising system** using a **U-Net–based deep learning model**. The goal is to remove background noise from speech signals and enhance audio clarity. The model is trained on **spectrogram representations** of clean and noisy speech and learns to predict and remove noise components from corrupted audio.

---

## 🎯 Problem Statement
Speech recordings captured in real-world environments often contain background noise that reduces intelligibility. Traditional filtering techniques are limited in handling complex noise patterns. This project uses a **data-driven deep learning approach** to effectively denoise speech.

---

## 🧠 Methodology

### 1. Data Preparation
- Clean speech and noise audio files are stored separately
- Audio is resampled to **8 kHz**
- Short audio files are filtered based on minimum duration
- Clean and noise signals are randomly mixed at different noise levels

**Dataset Summary**
- Clean speech files: 2703 (~323 minutes)
- Noise files: 2000 (~166 minutes)

---

### 2. Audio Processing
- Audio is split into fixed-length frames (`8064 samples`)
- Short-Time Fourier Transform (STFT) is applied
- Magnitude spectrograms are converted to **decibel (dB) scale**
- Phase information is preserved for reconstruction
- Final spectrogram size: **128 × 128**

---

### 3. Model Architecture
- **U-Net convolutional neural network**
- Encoder–decoder structure with skip connections
- LeakyReLU activations and dropout for regularization
- Input shape: `(128, 128, 1)`
- Loss function: Mean Squared Error (MSE)
- Optimizer: Adam

Total parameters: ~1.94 million

---

### 4. Training
- Train–test split: 90% / 10%
- Epochs: 20
- Batch size: 10
- Best model saved using validation loss

**Best validation loss:** ~0.0166

---

### 5. Inference
- Test audio is converted to spectrograms
- Model predicts the noise component
- Predicted noise is subtracted from noisy spectrogram
- Clean speech is reconstructed using inverse STFT
- Output saved as `.wav` file

---

## 🛠️ Technologies Used
- Python  
- TensorFlow / Keras  
- Librosa  
- NumPy  
- SciPy  
- Matplotlib  
- SoundFile  

---

✅ Results

Significant reduction of background noise

Improved speech clarity

Works on different noisy audio samples

Produces perceptually cleaner speech output

🚀 Future Work

Add objective metrics (SNR, PESQ, STOI)

Train on larger and more diverse datasets

Optimize for real-time speech denoising

Explore GAN-based speech enhancement models

