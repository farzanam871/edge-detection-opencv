# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** FARZANA M 
- **Register No:** 212225040087

---
### ORIGINAL IMAGE
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread("BMW4.jpg")

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
plt.show()
```
<img width="711" height="432" alt="Screenshot 2026-11-17 090232" src="https://github.com/user-attachments/assets/3d4b3c08-b419-4f27-a16d-bd20f69ef842" />



###  Sobel Edge Detector
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
### OUTPUT
<img width="742" height="443" alt="Screenshot 2026-11-17 090240" src="https://github.com/user-attachments/assets/8c25e697-9900-4a67-918f-d98f49fffff0" />


###  Prewitt Edge Detector
```


image = cv2.imread("BMW4.jpg")

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, cv2.CV_32F, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, cv2.CV_32F, prewitt_y)

prewitt = cv2.magnitude(prewitt_x_edge, prewitt_y_edge)

plt.imshow(prewitt, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
plt.show()

```
### OUTPUT 
<img width="738" height="446" alt="Screenshot 2026-11-17 090247" src="https://github.com/user-attachments/assets/ef1d0f2c-559f-437e-82e5-ad0cda1e8297" />

###  Roberts Edge Detector
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(BMW4.jpg")
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

roberts_x = np.array([[1, 0],
                      [0, -1]], dtype=np.float32)

roberts_y = np.array([[0, 1],
                      [-1, 0]], dtype=np.float32)

gx = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
gy = cv2.filter2D(gray, cv2.CV_32F, roberts_y)

roberts = cv2.magnitude(gx, gy)
roberts = cv2.normalize(roberts, None, 0, 255, cv2.NORM_MINMAX)
roberts = roberts.astype(np.uint8)

plt.imshow(roberts, cmap="gray")
plt.title("Roberts Edge Detection")
plt.axis("off")
plt.show()
```
### OUTPUT

<img width="772" height="442" alt="Screenshot 2026-11-17 090254" src="https://github.com/user-attachments/assets/30922b12-c4d2-41ee-ac3f-ca3091bd2fbe" />


###  Laplacian Edge Detector
```
import cv2
import matplotlib.pyplot as plt
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian_8bit = cv2.convertScaleAbs(laplacian)
plt.imshow(laplacian_8bit, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
### OUTPUT
<img width="725" height="442" alt="Screenshot 2026-11-17 090301" src="https://github.com/user-attachments/assets/67c2ab04-f17e-404f-a221-21cc89df62d0" />


###  Canny Edge Detector
```
import cv2
import matplotlib.pyplot as plt
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```
### OUTPUT
<img width="735" height="442" alt="Screenshot 2026-11-17 090306" src="https://github.com/user-attachments/assets/4e7f61bb-2040-43fe-990f-b06602c22d3f" />


---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
