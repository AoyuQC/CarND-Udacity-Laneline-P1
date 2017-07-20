# Finding Lane Lines on the Road

The goals/steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

## Reflection
##### 1. Description about my pipeline
My pipeline consisted of 5 steps: 
1. Converted the image to **grayscale**;

![raw](/images_for_writesup/raw_writeup.png)
![grayscale](/images_for_writesup/gray_writeup.png)

2. Applied **Guassian smoothing** ;
3. **Canny function** to detect all the possible edges;

![canny](/images_for_writesup/canny_writeup.png)
4. Defined a four sided polygon to **mask** these edges; 
5. The **Hough function** (hough_lines) can work easily after step 4. hough_lines consisted of cv2.HoughLinesP and draw_line(). In order to draw a single line on the left and the right lanes, I modified **draw_line()** this way:
* iterate the output "lines" of cv2.HoughLinesP;
* find good candidate of slope and put it in `slope_bak`: no vertical or horizontal line; the absolute value of solpe should be bigger than 0.2
* I averaged all the slope and points for the positive slope and negative slope separately
* with the averaged slope and point, I drawed the line inside the polygon
![result](/images_for_writesup/result_writeup.png)
##### 2. Potential shortcomings
* Sometimes, I cannot detect lines with curves(that's why I haven't finished **optional challenge** yet)
* The side part of line sometimes was considered as a potential line, this may lead to a bigger slope than real one
![fail](/images_for_writesup/fail_writeup.png)
##### 3. Possible improvements
