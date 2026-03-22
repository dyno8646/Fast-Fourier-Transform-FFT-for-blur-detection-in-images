================================================================
FFT-Based Blur Detection
DSM 410 Computer Vision | IIT Indore
Team: Lavanth Surada (2404107029) | Deepika M (2404107030)
================================================================


REQUIRED LIBRARIES
------------------
Python 3.x

Install all required packages using:
    pip install opencv-python numpy matplotlib pandas scikit-learn

Package list:
- opencv-python   : Image loading and preprocessing
- numpy           : FFT computation and array operations
- matplotlib      : Visualization and plots
- pandas          : Results summary table
- scikit-learn    : Logistic Regression, SVM, and metrics


DATASET DETAILS
---------------
The code automatically clones the dataset from GitHub at runtime.

Repository : https://github.com/dyno8646/Fast-Fourier-Transform-FFT-for-blur-detection-in-images
Images     : Located in the images/ folder of the cloned repository
Formats    : .png, .jpg, .jpeg, .bmp, .tif, .tiff

No manual download is required.


STEPS TO RUN THE CODE
---------------------

Option A - Google Colab (Recommended):
  1. Open https://colab.research.google.com
  2. Create a new notebook
  3. Copy and paste the contents of fft_blur_detection_complete.py
  4. Run all cells
  The dataset will be cloned automatically.

Option B - Local Machine:
  1. Install Python 3.x if not already installed
  2. Open command prompt and run:
         pip install opencv-python numpy matplotlib pandas scikit-learn
  3. Run the script:
         python fft_blur_detection_complete.py
  The dataset will be cloned automatically via git.
  Make sure git is installed on your machine.

Code Structure
---------------------
```
fft_blur_detection_complete.py
│
├── preprocess()           # Grayscale + normalization + Hann windowing
├── compute_fft()          # 2-D FFT, fftshift, log magnitude spectrum
├── compute_hf_ratio()     # High-frequency energy ratio (primary metric)
├── compute_radial_decay() # Radial avg + log-linear slope fitting
├── compute_sparsity()     # Spectral sparsity measure
├── compute_masked_spectrum()  # Low-freq masked spectrum (visualisation)
├── detect_blur()          # Full pipeline for one image → feature dict
├── visualise_image()      # 2-row per-image figure
└── Main loop              # Processes all images + summary + classifier
```


TUNEABLE PARAMETERS
-------------------
The following parameters can be adjusted at the top of the script:

  MASK_SIZE        = 30     Radius (px) of low-freq region zeroed out
  FREQ_THRESHOLD   = 0.25   Fraction of max radius for low/high split
  HF_THRESHOLD     = 0.50   HF ratio below this -> classified as Blurred
  SPARSITY_STD_MUL = 1.0    Std multiplier for sparsity threshold
  USE_WINDOWING    = True   Apply Hann window before FFT
  RUN_CLASSIFIER   = True   Train LR and SVM (requires >= 6 images)


OUTPUT DESCRIPTION
------------------
For each image the code produces:
  - Input image with color-coded border (green = Sharp, red = Blurred)
  - FFT magnitude spectrum
  - High-frequency masked spectrum
  - Radial spectral decay curve with fitted slope

After all images:
  - Results summary table
  - Feature comparison bar chart (HF Ratio, Decay Slope, Sparsity)
  - Classifier confusion matrices (if >= 6 images available)


================================================================