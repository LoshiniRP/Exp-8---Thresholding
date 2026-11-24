# Image Segmentation Using Thresholding Techniques in OpenCV

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

- Global Thresholding
- Adaptive Thresholding
- Otsu's Thresholding

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Load the input image using OpenCV.

### Step 3:

Convert the input image into grayscale format.

### Step 4: Global Thresholding

- Select a fixed threshold value.
- Apply thresholding to separate foreground and background pixels.
- Display the thresholded image.

### Step 5: Adaptive Thresholding

- Compute threshold values for small regions of the image.
- Apply Adaptive Mean Thresholding.
- Apply Adaptive Gaussian Thresholding.
- Display the segmented images.

### Step 6: Otsu's Thresholding

- Automatically determine the optimal threshold value.
- Apply Otsu's thresholding technique.
- Display the segmented image.

### Step 7:

Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods.

## Program

## Developed By

**Name:** R P Loshini

**Register No:** 212225230155

```
# Step 1: Import the required libraries: OpenCV, NumPy, and Matplotlib
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load the input image using OpenCV
image_path = r"C:\Users\acer\DIPT\Dog.jpg"
img_bgr = cv2.imread(image_path)
img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)

# Step 3: Convert the input image into grayscale format
gray_img = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2GRAY)

# Display Original RGB and Original Grayscale Image
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Color Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(gray_img, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')

plt.tight_layout()
plt.show()

# Step 4: Global Thresholding
# Select a fixed threshold value (e.g., 127) and apply cv2.threshold()
_, global_thresh = cv2.threshold(gray_img, 127, 255, cv2.THRESH_BINARY)

# Display Original Grayscale and Global Thresholded Image
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(gray_img, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(global_thresh, cmap='gray')
plt.title("Global Thresholding (T = 127)")
plt.axis('off')

plt.tight_layout()
plt.show()

# Step 5: Adaptive Thresholding
# Apply Adaptive Mean Thresholding
adaptive_mean = cv2.adaptiveThreshold(
    gray_img, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2
)

# Apply Adaptive Gaussian Thresholding
adaptive_gaussian = cv2.adaptiveThreshold(
    gray_img, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2
)

# Display Original, Adaptive Mean, and Adaptive Gaussian Thresholded Images
plt.figure(figsize=(15, 5))
plt.subplot(1, 3, 1)
plt.imshow(gray_img, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(adaptive_mean, cmap='gray')
plt.title("Adaptive Mean Thresholding")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(adaptive_gaussian, cmap='gray')
plt.title("Adaptive Gaussian Thresholding")
plt.axis('off')

plt.tight_layout()
plt.show()

# Step 6: Otsu's Thresholding
# Automatically determine optimal threshold value using cv2.THRESH_OTSU
otsu_val, otsu_thresh = cv2.threshold(
    gray_img, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU
)

print(f"Optimal Threshold Value determined by Otsu's method: {otsu_val}")

# Display Original Grayscale and Otsu Segmented Image
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(gray_img, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(otsu_thresh, cmap='gray')
plt.title(f"Otsu's Thresholding (Optimal T = {int(otsu_val)})")
plt.axis('off')

plt.tight_layout()
plt.show()

# Step 7: Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods
fig, axes = plt.subplots(2, 3, figsize=(15, 9))

axes[0, 0].imshow(gray_img, cmap='gray')
axes[0, 0].set_title("1. Original Grayscale Image")
axes[0, 0].axis('off')

axes[0, 1].imshow(global_thresh, cmap='gray')
axes[0, 1].set_title("2. Global Thresholding (T=127)")
axes[0, 1].axis('off')

axes[0, 2].imshow(otsu_thresh, cmap='gray')
axes[0, 2].set_title(f"3. Otsu's Thresholding (T={int(otsu_val)})")
axes[0, 2].axis('off')

axes[1, 0].imshow(adaptive_mean, cmap='gray')
axes[1, 0].set_title("4. Adaptive Mean Thresholding")
axes[1, 0].axis('off')

axes[1, 1].imshow(adaptive_gaussian, cmap='gray')
axes[1, 1].set_title("5. Adaptive Gaussian Thresholding")
axes[1, 1].axis('off')

# Hide unused 6th subplot slot
axes[1, 2].axis('off')

plt.tight_layout()
plt.show()
```

## Output

### Original Grayscale Image

- The grayscale version of the input image is displayed.
- Serves as the input for thresholding operations.

<img width="834" height="476" alt="image" src="https://github.com/user-attachments/assets/b30452fd-afdd-445b-9672-ccdf9b8bb5f5" />


### Global Thresholding

- Original image is displayed.
- Thresholded image is displayed.
- A fixed threshold value is used for segmentation.
- Pixels are classified as foreground or background.

<img width="836" height="479" alt="image" src="https://github.com/user-attachments/assets/92216f10-dc79-49de-8ccd-7e7fa306fbfd" />


### Adaptive Thresholding

- Original image is displayed.
- Adaptive Mean Thresholded image is displayed.
- Adaptive Gaussian Thresholded image is displayed.
- Threshold values vary across different regions of the image.
- Suitable for images with uneven illumination.

<img width="1078" height="386" alt="image" src="https://github.com/user-attachments/assets/660f28e0-ff61-41c7-ab5d-a509b820f620" />


### Otsu's Thresholding

- Original image is displayed.
- Otsu segmented image is displayed.
- Optimal threshold value is calculated automatically.
- Produces improved segmentation for bimodal histograms.

<img width="844" height="502" alt="image" src="https://github.com/user-attachments/assets/d4ac753c-69f3-45f5-b183-050234135cf5" />

### Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods

<img width="1018" height="685" alt="image" src="https://github.com/user-attachments/assets/fa733f87-1f88-46a3-953c-a90158fad9c6" />



## Result

Thus, image segmentation is successfully performed using **Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding** techniques in OpenCV. 
