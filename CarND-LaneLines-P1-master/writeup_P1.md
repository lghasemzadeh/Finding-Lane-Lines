**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[//]: # (Image References)

[image1]: ./writeup_Res/solidWhiteCurve.jpg "Solid White Curve"
[image2]: ./writeup_Res/solidWhiteRight.jpg "Solid White Right"
[image3]: ./writeup_Res/solidYellowCurve.jpg "Solid Yellow Curve"
[image4]: ./writeup_Res/solidYellowCurve2.jpg "Solid Yellow Curve2"
[image5]: ./writeup_Res/solidYellowLeft.jpg "Solid Yellow Left"
[image6]: ./writeup_Res/whiteCarLaneSwitch.jpg "White Carla"

----------------------------------------------------------------------------------------------------

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 2 main steps. First step, containing IP techniques which we learned so far in the course such as canny, ROI. the second step is the method which enables us to detect yellow lines.

To detect the yellow lines I convert the input image to HSV image then mask the yellow and white colors. The pipline overall is as follows:
1) input image to HSV conversion
2) masking the whitw and yellow colors over the HSV image
3) using bitwise OR operation to combine the white and yellow  masked image
4) using Gaussian filter to smooth the combined image 
5) using Canny to apply edge detection
6) determine a trapezoid ROI
7) using Hough transformation to detect the lane lines
8) Drawing the linear lane lines and put the lines over the original image

Here are the output of some of the above steps on different images: 

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]


### 2. Identify potential shortcomings with your current pipeline


There are two potential shortcoming for this pipline which the first one can be improved/corrected but the second one won't be eliminated completely. first, the pipile is able to detect only straight lines, second, Since most of image processing techniques (IPTs) suffer from light conditions or illuminations changes which cause decreasing the robustness, this pipline is not exceptional.

### 3. Suggest possible improvements to your pipeline

A possible improvement might be using fuzzy logic methods (e.g. alpha cut) in order to preserving edges instead of using canny method refering to this paper: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4583179/
I have not tried it yet but I am curious about the result.
