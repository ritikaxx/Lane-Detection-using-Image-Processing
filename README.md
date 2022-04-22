# Lane-and-Pedestrian-Detection-and-Tracking

Apart from all the good the Self Driving vehicles boast of there is still a question about pedestrian safety. How and what better technologies can be equipped to ensure pedestrian safety remains the need of the hour. This project aims to be solving this problem by adopting use of several transformation techniques for providing a finite lane path for smooth commute of the self driving cars.


# METHODOLOGY

In this project we are going to solve this problem of pedestrian and road lane detection for self-driving cars using various image processing techniques. 
We will be using HOG (Histogram of Oriented Gradients) for the detection and Kalman Filter for tracking and prediction of pedestrians. For lane detection, Bilateral filter will be used for reducing noise followed by edge detection and mapping of these edge points in finite lines for lane detection using thresholding and Hough transform .


![image](https://user-images.githubusercontent.com/68536395/164646839-338a6467-2240-41a4-9190-6169cc6b58ab.png)


# A)For Lane Detection-

The various processes which will be carried out are-

## 1)EDGE DETECTION-

Edges are significant local changes of brightness or intensity in a digital image. An edge can be defined as a set of connected pixels that forms a boundary between two disjoint regions. Edge Detection is a method of segmenting an image into regions of discontinuity. It allows users to observe the features of an image for a significant change in the gray level. This texture indicates the end of one region in the image and the beginning of another. It reduces the amount of data in an image and preserves the structural properties of an image.

Applying an edge detection algorithm to an image significantly reduces the amount of data to be processed and may therefore filter out information that may be regarded as less relevant, while preserving the important structural properties of an image.

Edge Detection Operators which can be used are of two types: 

    ● Gradient – based operator which computes first-order derivations in a digital image like, Sobel operator, Prewitt operator, Robert operator.
    ● Gaussian – based operator which computes second-order derivations in a digital image like, Canny edge detector, Laplacian of Gaussian.
    Canny Edge Detection:

It comes under Gaussian edge detection Canny Operator: It is a gaussian-based operator in detecting edges. This operator is not susceptible to noise. It extracts image features without affecting or altering the feature. Canny edge detector have advanced algorithms derived from the previous work of Laplacian of Gaussian operator.

The Canny edge detection algorithm is composed of 5 steps:
●	Noise reduction using Gaussian Filter
●	Gradient calculation using Sobel’s operator
●	Non-maximum suppression for making the edges thin
●	Double threshold
●	Edge Tracking by Hysteresis.


2)SELECTING REGION OF INTEREST USING MASKING-

There are a lot of unnecessary edges that we don’t require for our image. Hence masking out the unnecessary section and getting our region of interest. Masking the region of interest detected on the original image using operators like BITWISE_AND and other operators for next steps. 

3)HOUGH TRANSFORMATION-

The Hough Transform is a method that is used in image processing to detect any shape, if that shape can be represented in mathematical form. It can detect the shape even if it is broken or distorted a little bit. 

WORKING-
        ●	Image is first converted into binary image using thresholding. 
        ●	Each point (d, T) in Hough space matches to a line at angle T and distance d from the origin in the data space. 
        ●	The value of a function in Hough space gives the point density along a line in the data space.
        ●	For each point in the Hough space, consider all the lines which go through that point at an actual discrete set of angles.
        ●	 For each angle T, calculate the distance to the line through the point at that angle and discretize that distance using a priori chosen discretization, giving value d. 
        ●	Now make a corresponding discretization of the Hough space. This will result in a set of boxes in Hough space. These boxes are called the Hough accumulators.
        ●	For each line it considers above, we increment a count (initialized at zero) in the Hough accumulator at point (d, T). 
        ●	After considering all the lines through all the points, a Hough accumulator with a high value will probably correspond to a line of points.

# B)For Pedestrian Detection-

The main objective behind this detection is to devise an algorithm to identify and track pedestrians from the eyes of a moving vehicle.
2 main steps which will be used are-

## 1)	HOG (Histogram of Oriented Gradients) for detection

In the HOG feature descriptor, the distribution ( histograms ) of directions of gradients ( oriented gradients ) are used as features.
 HOG calculates the horizontal and vertical component of the gradient’s magnitude and direction of each individual pixel and then organizes the information into a 9-bin histogram to determine shifts in the data. 
The main takeaway that you should get from gradients are that the magnitude of the gradient increases wherever there is a sharp change in intensity.

## 2) Kalman Filter for tracking and prediction

The Kalman filter is a corrective predictor filter. In the tracking system objects, this filter looks at an object as it moves, that is, it takes information on the state of the object at the precise moment. 
Then, it uses this information to predict where the object is in the next frame. The KF is very powerful in several aspects: it supports estimates of past, present and even future states and it can do so even when the exact nature of the modeled system tracking and detection objects.
For this, it takes as input a measurement vector (position in x, in y, width and height of the object).
 
