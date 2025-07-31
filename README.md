# Foreground Detection and Image Binarization using Classical CV

---

## Project Overview

This project demonstrates two classical computer vision techniques for motion and image analysis:

1. **Task 1 – Foreground Detection from Video using Running Average**
2. **Task 2 – Image Binarization using the Expectation-Maximization (EM) Algorithm**

Both tasks are implemented in Python using OpenCV and NumPy, and designed to run in Google Colab.

---

## Task 1: Foreground Detection using Running Average

### Objective
Separate dynamic foreground objects from static backgrounds in video streams using a time-dependent background model.

### Methodology
- Maintained a running average background model:
  
$$
B G_{t+1} = (1 - \beta) B G_t + \beta I_t \quad 0 \leq \beta \leq 1
$$
  
- Detected motion by subtracting the current frame from the background.
- Applied thresholding and masking to extract the foreground.

### Output
- `foreground_images/`: Extracted moving objects  
- `mask_images/`: Binary motion masks  
- `background_images/`: Updated background models

### Before You Run
Update these paths in the notebook:
```bash
video_files = [
  '/content/drive/My Drive/your_video1.avi', #you can include only one video
  '/content/drive/My Drive/your_video2.avi'
]

output_base_dir = '/content/drive/My Drive/AVP/'  # Change as needed
```
## Task 2: Galaxy Image Binarization using EM Algorithm

### Objective

Classify each pixel in a grayscale galaxy image as either foreground or background using the Expectation-Maximization (EM) algorithm.



### Methodology

- **Preprocessing**:
  - Converted the galaxy image to grayscale
  - Resized and applied Gaussian blur to reduce noise

- **EM Algorithm**:
  - Initialized Gaussian parameters (mean and standard deviation) for two classes:
    - Background: μ₁ = 50, σ₁ = 20  
    - Foreground: μ₂ = 200, σ₂ = 30  
  - For each pixel:
    - Estimated probability of belonging to background or foreground
    - Assigned to the class with higher probability
  - Recomputed mean and variance for each class
  - Iterated until parameter convergence (using tolerance threshold)
  - Final step: Binarized image based on final pixel classification


### Output

- `binarized_image.png`: Final image with foreground (galaxy) in white and background in black



### Before You Run

Update this path in the notebook before running:
```python
image_path = '/content/drive/My Drive/AVP/galaxy.jpg'
```

Then run the EM algorithm code to generate the binarized output.

### Notes
- This method is unsupervised and works purely on pixel intensity distribution
- Suitable for astronomical images or similar grayscale segmentation tasks
