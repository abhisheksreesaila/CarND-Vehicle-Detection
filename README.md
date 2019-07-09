# CarND-Vehicle-Detection

The goals / steps of this project are the following:

1. Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images and train a classifier Linear SVM classifier
2. Optionally, you can also apply a color transform and append binned color features, as well as histograms of color, to your HOG feature vector. Note: for those first two steps don't forget to normalize your features and randomize a selection for training and testing.
3. Implement a sliding-window technique and use your trained classifier to search for vehicles in images.
4. Run your pipeline on a video stream (start with the test_video.mp4 and later implement on full project_video.mp4) and create a heat map of recurring detections frame by frame to reject outliers and follow detected vehicles.
5. Estimate a bounding box for vehicles detected.

# Step 1 : Histogram of Oriented Gradients (HOG)
The code for this step is contained in the section named “PROFILE DATA” of the IPython notebook 
I started by reading in all the `vehicle` and `non-vehicle` images.  Here is an example of one of each of the `vehicle` and `non-vehicle` classes:


I then explored different color spaces and different `skimage.hog()` parameters (`orientations`, `pixels_per_cell`, and `cells_per_block`).  I grabbed random images from each of the two classes and displayed them to get a feel for what the `skimage.hog()` output looks like.

Here is an example using the `YCrCb` color space and HOG parameters of `orientations=12`, `pixels_per_cell=(16, 16)` and `cells_per_block=(2, 2)`:


# Step 2 : Trained a classifier using the selected HOG features 
I trained a linear SVM using color features as well as HOG features. Using 32 spatial bins and HOG features specified above. The classifier used the labeled data for vehicle and non-vehicle examples but because of the time-series images present, it did not yield satisfactory results. Hence, I downloaded the smaller subset of the vehicle data given in the lesson and appended the data to the existing dataset. It improved the results. I think the quality of the data in the smaller subset is better.

# Step 3 : Sliding Window Search
I decided to start with 50% overlap and (64, 64) windows size (since the images we have trained on were 64x64). The window we decided to search between the Y values =  (350, 656). This skips the top half of the image and only search a portion of the image. Then I tested on 6 given test images.  Gradually, increasing the overlap from 50 – 85% to get the best results. I kept the scales constant at 1.25. There were many false positives still. 

# Inference (photos)

# Video

