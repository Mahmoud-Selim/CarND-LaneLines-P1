# **Finding Lane Lines on the Road** 

## Writeup File

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./Steps/1-gray.jpg "Grayscale"
[image2]: ./Steps/2-edges.jpg "Edges"
[image3]: ./Steps/3-masked.jpg "Masked edges"
[image4]: ./Steps/4-LineImage.jpg "Lane lines"
[image5]: ./Steps/5-result.jpg "result"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
1. I converted the images to grayscale.
![alt text][image1]
2. I applied gaussian blue to the gray image to emliminate noise.
3. I applied canny edge detection to detect edges in the image.
![alt text][image2]
4. I masked that image with a mask image to detect only the lane lines in the road.
![alt text][image3]    
5. I applied hough transform to get the lines in the image.
6. I drew the lane lines using the function draw_lines after editing it. Here is how it works:
    1. It gets the slope of the line.
    2. It seperates the postive slope from the negative one as one line will have a positive slope and the other will                               have a negative one.
    3. It gets the average of the positive slope, the average of the negative slope, the average of the intersection 
    with the intersection with the y-axis for both lines. y = mx + c.
    4. It uses the most far away points at the end of the lane line and the height of the image to draw a staright line.
![alt text][image4]
![alt text][image5] 



---

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when a car is just infront of our vechile ?? 

Another shortcoming could be if there are drawings or something spilled on the road ( say oil or something!).

Another shortcoming could be if the camera is moved to another spot !! our way of detection lane lines relies heavily on a constant spot for
    the camera!.

---

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to run some color filtering and keep important parts of the picture and remove other things that won't  
    matter while detecting lane lines.

Another potential improvement could be to train a deeplearning model to help with drawing the lane lines in the image.
