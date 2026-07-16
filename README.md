# Image Denoising Using FFT and DnCNN
- **Supervisor:** [Dr. Esmaeel Tahanian](https://scholar.google.com/citations?user=oiGyCF4AAAAJ&hl=en) <br>
- **Course:** Engineering Mathematics <br>
- **Organization:** [Shahrood University of Technology](https://www.shahroodut.ac.ir/en/) <br>

---

## 📖 Overview

This project implements and compares various image denoising techniques, ranging from classical spatial and frequency-domain filters to a modern deep‑learning approach (DnCNN). The goal is to demonstrate the effectiveness of each method on grayscale images corrupted by additive noise.

We evaluate:
- **Spatial filters:** Median, Bilateral, Moving Average, and Laplacian.
- **Frequency-domain filters:** Gaussian, Median, Bilateral, Moving Average, and Laplacian implemented via Fast Fourier Transform (FFT).
- **Deep learning:** A lightweight Denoising Convolutional Neural Network (DnCNN) trained on synthetic noise.

All results are visualized side‑by‑side for two different input images to facilitate visual comparison.

---

## ⚙️ Methodologies

### Spatial-Domain Filters

These filters operate directly on pixel intensities. The following are implemented:

| Filter            | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| **Median**        | Replaces each pixel with the median of its neighbourhood; excellent for salt‑and‑pepper noise. |
| **Bilateral**     | Preserves edges while smoothing by combining a spatial and a intensity Gaussian kernel. |
| **Moving Average**| Averages pixels in a local window; simple but blurs edges.                  |
| **Laplacian**     | A second‑order derivative operator used for edge detection (sharpening).    |

### Frequency-Domain Filters (FFT)

Images are transformed into the frequency domain using FFT. A low‑pass mask is applied to suppress high‑frequency noise, then the inverse FFT reconstructs the denoised image. The following filters are implemented:

- FFT Median
- FFT Gaussian
- FFT Bilateral
- FFT Moving Average
- FFT Laplacian

> **Note:** In this implementation, all FFT‑based filters use the same circular low‑pass mask with a fixed radius (30 pixels). This simplifies comparison but may not be optimal for every filter type.

### Deep Learning Denoising (DnCNN)

A compact convolutional neural network is trained to predict the residual noise from a noisy input. The architecture consists of:

- **Input:** Noisy image (grayscale, normalized to [0,1]).
- **Layers:** 5 convolutional layers with ReLU activations and batch normalization.
- **Output:** Estimated clean image (noise residual subtracted from input).

---

## 📊 Results

### 🎯 FFT‑Based Denoising

The following figure shows the original image alongside the outputs of all FFT‑based filters. The low‑pass mask effectively removes high‑frequency noise but also blurs fine details.

![Denoising Image Data Using FFT](https://github.com/YasinRezvani/Denoising_Image_Data_Using_FFT_And_DnCNN/assets/77124662/88818129-9276-4414-b08f-8cf1f3d7c720)

**Observations:**
- **FFT Median & Gaussian:** Smoother but lose texture.
- **FFT Laplacian:** Enhances edges (sharpening effect).
- **FFT Moving Average:** Strong blurring.

---

### 🧠 DnCNN Denoising

The DnCNN model produces significantly cleaner results, preserving edges and fine structures while effectively removing noise. The training loss decreased steadily over 5 epochs.

![Denoising Image Data Using DnCNN](https://github.com/YasinRezvani/Denoising_Image_Data_Using_FFT_And_DnCNN/assets/77124662/b0153122-c46b-49d5-9e17-a7811effd511)

**Observations:**
- Superior noise suppression compared to classical filters.
- Better retention of edges and textures.
- Generalizes well to unseen noise patterns.

---

## 🚀 Installation & Usage

### Requirements
- Python 3.8+
- TensorFlow 2.x
- OpenCV
- NumPy
- Matplotlib

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/YasinRezvani/Image_Denoising_Using_FFT_and_DnCNN.git
   cd Image_Denoising_Using_FFT_and_DnCNN
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the Jupyter Notebook:
   ```bash
   jupyter notebook main.ipynb
   ```

---

## 📚 References

- [DnCNN: Beyond a Gaussian Denoiser](https://arxiv.org/abs/1608.03981) – Zhang et al., 2017.
- OpenCV Documentation – [Image Filtering](https://docs.opencv.org/4.x/d4/d86/group__imgproc__filter.html)
- NumPy FFT – [Fast Fourier Transform](https://numpy.org/doc/stable/reference/routines.fft.html)

---


## 🙏 Acknowledgements

We would like to express our sincere gratitude to:

- **Dr. Esmaeel Tahanian** for his invaluable guidance, continuous support, and constructive feedback throughout this project as part of the Engineering Mathematics course.
- **Shahrood University of Technology** for providing the academic environment and computational resources necessary to conduct this research.
- The open‑source community for developing and maintaining the powerful libraries (TensorFlow, OpenCV, NumPy) that made this work possible.
- All contributors and researchers whose previous work on image denoising and deep learning laid the foundation for this study.

---


## 🤝 Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request for improvements, additional filters, or better training strategies.

---

## 📄 License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.


