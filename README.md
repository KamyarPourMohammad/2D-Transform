# Image Processing: 2D Unitary Transforms - DCT Analysis

## Overview

This project explores the fundamental concepts of 2D Unitary Transforms, specifically the **Discrete Cosine Transform (DCT)**, through practical implementation in Python. The notebook provides a comprehensive analysis of:

- **Basis Images**: Understanding the frequency decomposition of DCT
- **Energy Compaction**: Demonstrating the efficiency of DCT for image compression
- **Transform-Domain Filtering**: Low-pass and high-pass filtering in the frequency domain
- **Perfect Reconstruction**: Verifying the unitary property of orthonormal DCT

## Features

### Part 1: Basis Images
- Generates all 64 basis images for an 8×8 DCT
- Visualizes the frequency decomposition in a grid format
- Demonstrates the relationship between indices $(k_1, k_2)$ and frequency content

### Part 2: 2D Transform Implementation
- Implements 2D DCT and inverse DCT using `scipy.fftpack`
- Verifies perfect reconstruction with MSE $\approx 5.78 \times 10^{-32}$
- Explains the importance of orthonormal normalization (`norm='ortho'`)

### Part 3: Energy Compression
- Compresses images by retaining only top $p\%$ of DCT coefficients
- Reconstructs images with 1%, 5%, 10%, 25%, and 50% of coefficients
- Computes PSNR for each compression level
- Visualizes logarithmic spectrum vs. linear spectrum

### Part 4: Transform-Domain Filtering
- Implements low-pass filters with radii $r = N/8$ and $r = N/4$
- Implements high-pass filtering ($r = N/8$)
- Analyzes visual effects of frequency-domain filtering

## 📊 Results

### Compression Performance

| Coefficients Kept | PSNR (dB) | Visual Quality |
|-------------------|-----------|----------------|
| 1%                | ~25-28    | Blurry, major detail loss |
| 5%                | ~30-35    | Good quality, slight blurring |
| 10%               | ~35-38    | Very good quality |
| 25%               | ~40+      | Almost perfect |
| 50%               | ~45+      | Nearly indistinguishable |

### Key Findings

- **Energy Compaction**: 5% of coefficients retain ~95% of signal energy
- **Perfect Reconstruction**: MSE $\approx 5.78 \times 10^{-32}$ confirms unitary property
- **Low-Pass Filtering**: Larger radius preserves more details
- **High-Pass Filtering**: Reveals edges, textures, and contours