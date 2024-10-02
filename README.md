# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.
## Program
```
Developed by : RIYA P L
Register no : 212223240141
```
i.) Input image and grayscale image
```
import numpy as np
import cv2
import matplotlib.pyplot as plt

# Read the gray image using imread
gray = cv2.imread('gray.jpeg', cv2.IMREAD_GRAYSCALE)  # Replace 'image_path.jpg' with the actual path

# Read the color image using imread
img_c = cv2.imread('rose.jpg')  # Replace 'image_path.jpg' with the actual path

# Convert the color from BGR to RGB
img_c = cv2.cvtColor(img_c, cv2.COLOR_BGR2RGB)

# Convert the gray image to RGB (this step is optional if you want to visualize the gray image in an RGB plot)
gray_rgb = cv2.cvtColor(gray, cv2.COLOR_GRAY2RGB)

# Apply Gaussian blur
gray_blurred = cv2.GaussianBlur(gray, (3, 3), 0)

# Display original and grayscale images
plt.figure(figsize=(13, 13))
plt.subplot(1, 2, 1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1, 2, 2)
plt.imshow(gray_blurred, cmap='gray')
plt.title("Gray Image")
plt.axis("off")
plt.show()
```
ii.) Canny Edge detector output
```
# Apply Canny edge detection
canny = cv2.Canny(gray_blurred, 120, 150)

# Display the Canny edge detector result
plt.imshow(canny, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
iii.) Display the result of Hough transform
```
# Find the edges in the image using canny detector and display
canny_edges = cv2.Canny(img_c, 50, 120)
cv2.imshow('canny',canny_edges)
cv2.waitKey(0)
cv2.destroyAllWindows()


# Detect points that form a line using HoughLinesP
lines =cv2.HoughLinesP(canny_edges, 1, np.pi/180,threshold = 15, minLineLength =5 ,
maxLineGap = 7)

# Draw the detected lines on the color image
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(img_c, (x1, y1), (x2, y2), (255, 0, 0), 3)

# Display the result image with lines
plt.imshow(img_c)
plt.title("Result Image with Detected Lines")
plt.axis("off")
plt.show()
```
## Output

### Input image and grayscale image
![Screenshot 2024-10-02 185358](https://github.com/user-attachments/assets/846bdae1-4a89-4466-9261-9ebcaeb67153)

### Canny Edge detector output
![Screenshot 2024-10-02 185430](https://github.com/user-attachments/assets/2284d7a8-0af6-4d9e-b6df-89031ed646a4)

### Display the result of Hough transform
![Screenshot 2024-10-02 191811](https://github.com/user-attachments/assets/a65ba336-594e-4a62-9cc8-09a0c3a3df7a)

## Result
Thus, To write a Python program to detect the lines using Hough Transform is executed successfully.
