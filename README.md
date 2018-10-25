In this project, a deep learning based automated nuclei segmentation method is applied to four types of cancerous cells:
glioblastoma (GBM), log grade glioma (LGG), non small cell lung cancer (lung), head and neck squamous cell carcinoma cancer (HNSC). The proposed technique is motivated by the need to identify pixels in background (outside all nuclei) and in foreground (inside any nucleus). Thus, the problem is reduced to a binary classification problem for every pixel.

## Methodology

The methodology followed in this project can be mainly broken down into seven phases:

**1. Test and Training Set Division of Images**

The entire image dataset consists of 32 images and their corresponding labels. Among those 32 images 8 are of GBM cells, 8 are of HNSC cells, 8 are of LGG cells, and, the rest are of lung cells. 

The division of images into test set and training set is done in two different ways. In first way, the test set is heterogeneous collection of images. Among 8 test images, 2 are of GBM, 2 are of HNSC, 2 are of LGG and, the remaining 2 are of lung. The remaining 24 are chosen to form the training set. In second way too the training set contains 24 images and the test set contains 8 images, but, the test set is homogeneous. It consists of only lung images, with which the model is not trained at all. Hence, it makes the segmentation task much more challenging for the model than the first way of division.

**2. Image Resizing**

The sizes of the images in the dataset are unevenly spanned from 603×603 to 495×495. So, all the images are resized to 500×500.

**3. Binary Label Production**

The labels of all training images and test images are RGB images. All the label images are first converted to gray images. Now the gray image is converted to binary image by simple thresholding.

**4. Patch Extraction from the Training Set**

As the number of images for training the model is very scanty, only 24, patch extraction and data augmentation are used to increase the number of images for training. From each training image, five patches (total 120 patches from 24 images) of size 256×256 are extracted.

**5. Data Augmentation**

Data augmentation is a technique to generalize the model and reduce over-fitting. So it is applied to data before training to increase data. Augmented data is generated by applying rotation, width shift, height shift, zoom, horizontal flip, shearing. After data augmentation the size of training set increases to 3112.

**6. Data Preprocessing**

Two common forms of data preprocessing are used:

**Mean Subtraction**
It involves subtracting the mean across every individual feature in the data, and has the geometric interpretation of centering the cloud of data around the origin along every dimension. With images specifically, it is common to subtract the mean from all pixels, or to do so separately across the three color channels.

**Normalization**
It refers to normalizing the data dimensions so that they are of approximately the same scale. To achieve this normalization, each dimension is divided by its standard deviation, once it has been zero-centered after mean subtraction.

**7. Nuclei Segmentation**

The nuclei segmentation is performed with a Fully Convolutional Neural Network (FCN). Such a network can take an image as input and produces a prediction score matrix of the same size. This prediction score matrix is used to contruct the binary segmentation output. The network architecture used in the proposed approach is inspired by Ronneberger’s U-Net architecture. This FCN captures both local and global features from the input image to construct an accurate segmentation map. Global features indicate the exact location and relative size of the nucleus region, whereas the local features determine the exact boundaries.

**Network Architecture**

The model is set to work on images of size 256 × 256. In the analysis/downsampling phase, there are two 3 × 3 convolutions before a 2 × 2 max pooling layer which reduces the resolution of the image exactly by half. All the convolutions are followed by a Rectified Linear Unit (ReLU) activation function. The number of filters in each convolutional layer are also doubled after every
stage. The second phase of the network upsamples the activations using upconvolution which is basically an upsampling operation of size 2 × 2, followed by a 2 × 2 convolution. The last layer in the network is a 1 × 1 convolution layer with sigmoid activation function which maps the signal to a probability map having the same dimensions as the input image.

![alt text](https://github.com/tintin85/Nuclei-Segmentation/blob/master/Architecture%20of%20proposed%20model.png)

## Result

The mean value of all the Dice Coefficient values for images in heterogeneous test set is 0.7900695389088697, and, for images in homogeneous test set the mean is 0.6844246242424419.

**Sample Result**

![alt text](https://github.com/tintin85/Nuclei-Segmentation/blob/master/result.png)








  















