# **Finding Lane Lines on the Road** 


### The goal is to find lane lines on the road
---

### Method

The steps are the following:
1. Load image
2. Given an image, convert to grayscale
3. Use **canny** to detect edges of objects
4. Among the edges, find out straight lines using **Hough Transformation**
5. Extrapolate and average the line segments found in previous step

---
Method Visualization:

1. Load image
![step1][image1]

2. Convert to grayscale
![step2][image2]

3. Canny edge detection
![step3][image3]

4. Apply Hough Transformation (to above image) to find straight lines in image
![step4][image4]

5. Extrapolate and average the line segments using slopes and linear regressions
![step5][image5]


[//]: # (Image References)
[image1]: ./test_images/solidWhiteCurve.jpg "input"
[image2]: ./gray_images_output/solidWhiteCurve.jpg "input"
[image3]: ./edges_output/solidWhiteCurve.jpg "input"
[image4]: ./straightlines_output/solidWhiteCurve.jpg "input"
[image5]: ./test_images_output/solidWhiteCurve.jpg "input"

---

### Tools
* Python 3, Numpy, OpenCV, Matplotlib, Jupyter Notebook

---




### 1. Remarks

* In Step 5, only straight lines of certain slopes are collected for line averaging. *i.e,* lane lines are assumed to have slopes in certain range.

* When collecting lines, the symmetric appearance of left and right lanes in images are considered.

* Linear regression is used for many line segments averaging.

* In some cases, yellow lines are not easy to be observed in gray-scaled images. Additional information from HSL color space is helpful for yellow line detection.


### 2. Potential drawbacks of current pipeline

* One potential shortcoming is that the current pipeline requires clean and nonvanishing lane lines. In many cases, lane lines are obscure or dated. 

* It was observed that the detection can sometimes fail due to interference of tree shades, background lighting, or noise in images.


### 3. Potential improvements

Possible improvements are:

* Add HSL color space to locate yellow and white lines on top of canny edge detection of the grayscale image.

* Use histories of lane line (slope and intercept) changes for future (time) frame prediction, to prevent from sudden changes due to false detection.

