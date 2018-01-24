# **Traffic Sign Recognition** 


## Rubric Points


---
### Writeup / README
#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

* Code:   J-TSC02.ipynb
* Html:   J-TSC02.html
* Report: J-TSC-writeup.md
* Result: ./result

### Data Set Summary & Exploration

#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is ? 34799
* The size of the validation set is ? 4410
* The size of test set is ? 12630
* The shape of a traffic sign image is ? (32, 32, 3)
* The number of unique classes/labels in the data set is ? 43

#### 2. Include an exploratory visualization of the dataset.

* Here is an exploratory visualization of the data set. 
[image1]: ./result/01-SampleDataSet.png "Visualization"
![Alt text](/result/01-SampleDataSet.png "Visualization")

* It is a bar chart showing how 

[image2]: ./result/02-BarChart.png "Bar Chart"

### Design and Test a Model Architecture

#### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)

I sharp the image before training
The difference between the original image and the sharped image is shown as below:

[image3]: ./result/03-ProcessedImage.png "PreProcessed Image"


#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the following layers:

1. Input:        26x26 px preprocessed image.             (26x26x3)
2. Convolution1: same padding (26x26x3)
   Convolution2: same padding (26x26x32)
   Inception1:   (26x26x256)
   MaxPooling1:  (13x13x256)
   Inception2:   (13x13x512)
   MaxPooling2:  (6x6x512)
   Convolution3: (6x6x256)
   full connected0 (flatten Convolution3)
   full connected1 (drop out 50% --> output 512)
   full connected2 (512 --> 43)
2. Output:       43 neurons for all traffic sign classes.

 

#### 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

Due to my computer is slow, I only test set EPOCHS as 4 with (BATCH_SIZE = 128, Learning Rate = 0.0005)

#### 4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

My final model results were:
* training set accuracy of ? 0.979
* validation set accuracy of ? 0.952
* test set accuracy of ? 0.942


### Test a Model on New Images

#### 1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are five German traffic signs that I found on the web:

[image3]: ./result/04-NetPic.png "Six German traffic signs found on the web"

![alt text][./net-pic/CurveRoad.jpeg] 
![alt text][./net-pic/NoEntry.jpeg] 
![alt text][./net-pic/SpeedLimit-50.jpeg] 
![alt text][./net-pic/SpeedLimit-100.jpeg] 
![alt text][./net-pic/Stop.jpeg]
![alt text][./net-pic/TurnRight.jpeg]



#### 2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

Here are the results of the prediction:

[image4]: ./result/05-PredictResult.png "Prediction result for traffic signs found on the web"

No Entry and Turn riight ahead are correct predicted.
The Accuracy rate is only 2/6 (~33%)
Ihe accuracy might be improved by cropping the area of traffic sign before doing traffic sign classifier. 

#### 3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

[image5]: ./result/06-Top5.png "Top 5 probabilities for each image"

### (Optional) Visualizing the Neural Network (See Step 4 of the Ipython notebook for more details)
#### 1. Discuss the visual output of your trained network's feature maps. What characteristics did the neural network use to make classifications?


