In this project, a deep learning based automated nuclei segmentation method is applied to four types of cancerous cells:
glioblastoma (GBM), log grade glioma (LGG), non small cell lung cancer (lung), head and neck squamous cell carcinoma cancer (HNSC).

## Methodology

The methodology followed in this project can be mainly broken down into five phases:
image resizing, binary label production, patch extraction from the training set, data augmentation of the patches, and, lastly, nuclei segmentation.

**Test and Training Set Division of Images**
The entire image dataset consists of 32 images and their corresponding labels. Among those 32 images 8 are of GBM cells, 8 are of HNSC cells, 8 are of LGG cells, and, the rest are of lung cells. 

The division of images into test set and training set is done in two different ways. In first way, the test set is heterogeneous collection of images. Among 8 test images, 2 are of GBM, 2 are of HNSC, 2 are of LGG and, the remaining 2 are of lung. The remaining 24 are chosen to form the training set. In second way too the training set contains 24 images and the test set contains 8 images, but, the test set is homogeneous. It consists of only lung images, with which the model is not trained at all. Hence, it makes the segmentation task much more challenging for the model than the first way of division.


