# Canny Edge Detection Implementation

### AIM

To implement the Canny Edge Detection algorithm on a sample image using Python and observe how different parameters affect the edge detection results.

### PROCEDURE

1) Import Required Libraries
Import OpenCV, NumPy, and Matplotlib for image processing and visualization.

2) Load the Input Image
Read the sample image using cv2.imread().

3) Convert to Grayscale
Convert the image to grayscale for intensity-based processing.

4) Apply Gaussian Blur
Apply Gaussian smoothing (e.g., kernel size 5×5) to reduce noise and avoid false edge detection.

5) Apply Canny Edge Detector
Use the cv2.Canny() function with chosen lower and upper threshold values.

6) View and Compare Results
Plot the original, blurred, and edge-detected images using Matplotlib.

7) Experiment with Parameter Variations
Change Gaussian kernel sizes and threshold values to observe differences in detected edges.

### PROGRAM
```py
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('archery1.jpg') 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
blur = cv2.GaussianBlur(gray_image, (5, 5), 0)

image2 = cv2.imread('raccoon1.jpg') 
gray_image2 = cv2.cvtColor(image2, cv2.COLOR_BGR2GRAY)
blur2 = cv2.GaussianBlur(gray_image2, (5, 5), 0)

# Display the images

plt.figure(figsize=(20,10))
plt.subplot(131);plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB));plt.title("Original Image");plt.axis('off')
plt.subplot(132);plt.imshow(gray_image, cmap = 'gray');plt.title("Gray Image");plt.axis('off')
plt.subplot(133);plt.imshow(blur, cmap = 'gray');plt.title("Blur Image");plt.axis('off')


edges1 = cv2.Canny(blur, threshold1 = 180, threshold2 = 200)

plt.figure(figsize = (12, 16))
plt.subplot(121); plt.axis('off'); plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB)); plt.title('Input image')
plt.subplot(122);plt.imshow(edges, cmap='gray');plt.axis('off'); plt.title('Canny Edge Map')

edges2 = cv2.Canny(blur2, threshold1 = 180, threshold2 = 200)

plt.figure(figsize = (12, 16))
plt.subplot(121); plt.axis('off'); plt.imshow(cv2.cvtColor(image2, cv2.COLOR_BGR2RGB)); plt.title('Input image')
plt.subplot(122);plt.imshow(edges2, cmap='gray');plt.axis('off'); plt.title('Canny Edge Map')

edges1 = cv2.Canny(blur, 50, 150)
edges2 = cv2.Canny(blur, 100, 200)
edges3 = cv2.Canny(blur, 150, 250)

plt.figure(figsize = (12, 6))
plt.subplot(221); plt.axis('off'); plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB)); plt.title('Input image')
plt.subplot(222);plt.imshow(edges1, cmap='gray');plt.axis('off'); plt.title('Edge Map(Lower)')
plt.subplot(223);plt.imshow(edges2, cmap='gray');plt.axis('off'); plt.title('Edge Map(Middle)')
plt.subplot(224);plt.imshow(edges3, cmap='gray');plt.axis('off'); plt.title('Edge Map(Upper)')

edges1 = cv2.Canny(blur2, 50, 150)
edges2 = cv2.Canny(blur2, 100, 200)
edges3 = cv2.Canny(blur2, 150, 250)

plt.figure(figsize = (16, 12))
plt.subplot(221); plt.axis('off'); plt.imshow(cv2.cvtColor(image2, cv2.COLOR_BGR2RGB)); plt.title('Input image')
plt.subplot(222);plt.imshow(edges1, cmap='gray');plt.axis('off'); plt.title('Edge Map(Lower)')
plt.subplot(223);plt.imshow(edges2, cmap='gray');plt.axis('off'); plt.title('Edge Map(Middle)')
plt.subplot(224);plt.imshow(edges3, cmap='gray');plt.axis('off'); plt.title('Edge Map(Upper)')

```

### How do different parameter settings impact the result?

Canny Edge Detection mainly depends on three parameters, and each influences the output differently.

1)  Gaussian Blur Kernel Size (Noise Reduction Step)

Gaussian blur smooths the image before edge detection.

Effect:
  - Smaller kernel (3×3):
    - Less smoothing
    - More edges detected
    - More noise appears as edges

  - Larger kernel (7×7 or 9×9):
    - Strong smoothing
    - Fewer, cleaner edges
    - Fine details may disappear

A larger kernel gives cleaner but fewer edges; a smaller kernel preserves details but may detect noise.

2) Lower Threshold (T1) in Canny

Used for detecting weak edges.

Effect:
  - Low T1 (e.g., 30–70):
    - Very sensitive
    - Many edges detected, including weak/noisy ones

  - High T1 (e.g., 120–150):
    - Only stronger gradient changes are considered
    - Fewer edges appear


3) Upper Threshold (T2) in Canny

Used for detecting strong edges.

Effect:
  - Low T2 (100–150):
    - Many strong and semi-strong edges kept
    - Output may look cluttered

  - High T2 (200–250):
    - Only strongest edges retained
    - Very clean but may miss important boundaries

## RESULT
The Canny edge detection algorithm successfully extracted clear and sharp edges from the input image.
