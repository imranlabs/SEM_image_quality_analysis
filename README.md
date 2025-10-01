
# SEM Image Quality Assessment & Tool-to-Tool Matching

A comprehensive Python toolkit for assessing Scanning Electron Microscope (SEM) image quality and ensuring consistency between different SEM tools. Designed for semiconductor manufacturing and metrology workflows where stable image quality is critical for accurate measurements.

![SEM IQA](https://img.shields.io/badge/SEM-Image%20Quality%20Assessment-blue)
![Python](https://img.shields.io/badge/Python-3.7%2B-green)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-orange)

## Overview

Modern CD-SEM workflows depend on stable image quality. This toolkit provides:

- **Image Quality Assessment (IQA)**: Quantitative metrics to detect focus drift, stigmation, detector noise, and operating-point drift
- **Tool-to-Tool Matching**: Statistical comparisons to verify operating-point consistency across multiple SEM tools
- **Comprehensive Analysis**: Both full-reference and no-reference metrics with explainable visualizations



## This README provides:

1. **Clear overview** of the project's purpose and capabilities
2. **Easy installation** instructions
3. **Quick start** examples for immediate use
4. **Comprehensive documentation** of all major features
5. **Practical application** scenarios for semiconductor professionals
6. **Professional formatting** with badges and clear structure
7. **Proper attribution** to academic sources
8. **Modular organization** that's easy to navigate

The README emphasizes the practical industrial applications while maintaining academic credibility through proper citations and methodological explanations.

## Features

### Full-Reference Metrics
- **Normalized Variance Focus Score** (Normvar) - Adapted from [Yu Sun et al.](https://doi.org/10.1002/jemt.20118)
- **Structural Similarity Index** (SSIM)
- **Peak Signal-to-Noise Ratio** (PSNR)

### No-Reference Metrics
- **Laplacian Variance** (Sharpness measurement)
- **FFT High-Frequency Ratio** (Fine-detail energy)
- **Contrast-to-Noise Ratio** (CNR) on fixed ROIs

### Tool Matching
- **Histogram Analysis** (Brightness/Contrast/Shape comparison)
- **Statistical Summary** 
- **Quality Assessment Categories** (Excellent/Good/Fair/Poor)

### Synthetic Degradations
- Gaussian blur (defocus simulation)
- Stigmation-like anisotropic blur
- Poisson noise (shot noise simulation)
- Gaussian noise (read noise simulation)
- Contrast/Brightness drift

## Installation

### Prerequisites
- Python 3.7+
- OpenCV
- scikit-image
- NumPy
- Matplotlib
- SciPy

### Install Dependencies
```bash
pip install opencv-python scikit-image numpy matplotlib scipy tabulate pandas
```

### Optional: BRISQUE Support
For BRISQUE no-reference quality assessment:
```bash
pip install opencv-contrib-python
```

## Quick Start

```python
import SEM_IQA

# Load your SEM images
reference_image = 'path/to/reference.bmp'
test_image = 'path/to/test.bmp'

# Calculate comprehensive quality metrics
metrics = calculate_all_metrics(reference_image, test_image)

# Generate quality report
generate_quality_report(metrics, "Your Distortion Type")

# Compare tool-to-tool histograms
hist_results = compare_histograms(reference_image, test_image, plot_histograms=True)
```

## Usage Examples

### 1. Focus Assessment with Gold-on-Carbon
```python
# Demo with Gold-on-Carbon reference image
results = create_focus_assessment_demo('Gold_on_Carbon.jpg')
```

### 2. FFT Sharpness Analysis
```python
# Compare FFT sharpness between reference and test images
fft_results = fft_sharpness_comparative(reference_image, test_image)
plot_fft_comparison(fft_results)
```

### 3. Apply SEM-like Degradations
```python
# Apply stigmation (anisotropic blur)
stigmatized = apply_stigmation(original_image, ksize_x=9, ksize_y=3, angle=45)

# Add Poisson noise (simulates electron shot noise)
noisy_image = add_poisson_gaussian(original_image, peak=20, read_std=0.002)
```

## Project Structure

```
SEM_IQA/
├── SEM_IQA.ipynb          # Main Jupyter notebook
├── figures/
│   ├── reference_images/  # Clean reference images
│   └── distorted_images/  # Images with various degradations
├── opencv_models/         # BRISQUE model files
│   ├── brisque_model_live.yml
│   └── brisque_range_live.yml
└── README.md
```

## Core Functions

### Image Quality Assessment
- `calculate_all_metrics()` - Comprehensive metric calculation
- `NormvarFocus()` - Normalized variance focus score
- `BrisqueScore()` - No-reference quality assessment
- `compute_sharpness_lap()` - Laplacian sharpness

### Tool Matching
- `compare_histograms()` - Statistical histogram comparison
- `fft_sharpness_comparative()` - Frequency domain analysis

### Degradation Simulation
- `apply_stigmation()` - SEM stigmation simulation
- `add_poisson_gaussian()` - Realistic SEM noise simulation

## Output Examples

The toolkit provides:
- **Quantitative Metrics**: Numerical scores for all quality dimensions
- **Visual Comparisons**: Side-by-side image and histogram plots
- **Quality Reports**: Structured assessment with insights
- **Tool Matching Scores**: Correlation metrics and quality ratings

## Applications

- **SEM Tool Qualification**: Post-maintenance validation
- **Process Control**: Continuous image quality monitoring
- **Multi-Tool Matching**: Ensure measurement consistency across tools
- **Troubleshooting**: Identify specific degradation types
- **Preventive Maintenance**: Early detection of tool drift

## Methodology

### Why These Metrics?
The selected metrics are intentionally simple, explainable, and fast. They capture main SEM failure modes without requiring heavy models or opaque tuning. Visual overlays (SSIM maps, FFT magnitude views) help reviewers see where quality diverges—not just get a number.

### Gold-on-Carbon Standard
Gold sputtered on carbon substrate images (GoC) are typically the first images acquired after SEM tool maintenance. The Normalized Variance method is stable and coincides with human perception of focus.

## Contributing

Contributions are welcome! Please feel free to submit pull requests for:
- Additional IQA metrics
- Improved visualization
- Performance optimizations
- Documentation improvements

## License

- This project is licensed under the MIT License. See LICENSE file for details.

## Citation
If you use this notebook or code, please cite:

> Khan, I. (2025). *SEM Image Quality Assessment & Tool-to-Tool Matching (Jupyter notebook)*. Version 1.0. GitHub. https://github.com/imranlabs/SEM_image_quality_analysis/tree/main



## Acknowledgments

- Normalized Variance Focus Score adapted from [Yu Sun et al.](https://doi.org/10.1002/jemt.20118)
- Public domain SEM images from various sources
- OpenCV and scikit-image communities
- The non-proprietary distortions used and inspired from the [TID2013 paper.](https://doi.org/10.1016/j.image.2014.10.009)

## 📞 Support

For questions or issues:
1. Check the example usage in the notebook
2. Review the function documentation
3. Open an issue on GitHub

---


