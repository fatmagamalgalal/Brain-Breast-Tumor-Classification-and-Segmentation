# Multi-Cancer Identification and Segmentation

This project aims to identify different cancer diseases using deep learning techniques such as image classification and segmentation. The first step in disease detection is to determine the type of scan, which is either a breast or brain scan in our case. Then, we determine whether the scan is normal or has a tumor, and if a tumor exists, we identify its type.

## The objectives of this project are as follows:

- Apply different image preprocessing techniques.
- Apply image classification to classify each image as a brain scan or a breast scan and then determine if the scan is normal or if it has a tumor.
- Apply image segmentation to determine the exact location of the infected area.
- Determine the width and height of the tumor in the scan if it exists.

## Dataset Description
The dataset for this project can be found [<a href = "https://drive.google.com/file/d/1z-qAHlyhfeCCTdKnwvC9iAV2lOEXL_X3/view?usp=share_link">here</a>]. 

The dataset consists of the following folders/files:

1- Brain Cancer

* Tumor
  - Train (images for training the model)
  - Test (images for testing the model)
  - Train_masks (segmentation masks for the Train folder Images)
  - Test_masks (segmentation masks for the Test folder Images)

* No Tumor
  - Train (images for training the model)
  - Test (images for testing the model)

2- Breast Cancer

* Benign
  - Train (consists of the training images with their corresponding segmentation masks)
  - Test (consists of the testing images with their corresponding segmentation masks)

* Malignant
  - Train (consists of the training images with their corresponding segmentation masks)
  - Test (consists of the testing images with their corresponding segmentation masks)

* Normal
  - Train (consists of the training images)
  - Test (consists of the testing images)

Example of a benign breast cancer with its corresponding mask

![image](https://user-images.githubusercontent.com/43317809/235371913-2dcd3710-7493-4c2b-8042-e090f7bc9cf6.png)
![image](https://user-images.githubusercontent.com/43317809/235372047-38cd8910-7ccf-40b7-ae29-822085834d00.png)

Example of a brain cancer with tumor with its corresponding mask

![image](https://user-images.githubusercontent.com/43317809/235372083-4e893c23-2208-480b-b8bb-de769be0b403.png)
![image](https://user-images.githubusercontent.com/43317809/235372090-6e19ee42-234d-4389-b3ff-09576ed732bd.png)


## Project Deliverables
The following deliverables are expected from this project:

- Apply image classification to classify the given scan as "Breast" or "Brain" (1st stage classification).
- After determining the type of scan from the previous step, determine whether the scan is normal or has an infection (2nd stage classification).
- Apply image segmentation to identify the pixels of the infected area.
- Determine the width and height of the tumor in the scan if it exists.

## Brief description of the classification and segmentation models used.

### 1st stage classification:
- Architecture: MobileNet
- Train time:1m24s || 3 epochs
- Loss : 0.0725
- Accuracy: 1.0000 
- Precision: 1.0000 
- Recall: 1.0000 
- Output: 

![image](https://user-images.githubusercontent.com/43317809/235372248-aea0ef82-cec2-49b1-987a-58832c8fa9a5.png)


### 2nd stage classification:
#### Model 1: Brain tumor
- Architecture: CNN
- Train size: 1001 sample 
- Val size: 200 sample
- Train time: 68.61288213729858 seconds
-	Loss: 0.2292 
- Accuracy: 0.9062
- Output: 

![image](https://user-images.githubusercontent.com/43317809/235373025-d6d8dd9d-f68c-45dc-9524-a63dea8e1fcc.png)

![image](https://user-images.githubusercontent.com/43317809/235373090-31d58424-54ba-486b-8b8b-0e91bf2374a1.png)


	
#### Model 2: Breast tumor
- Architecture: MobilNet
- Train time: in range 20 sec GPU per epoch
- AUC: 86.7
- Loss: 0.8 

### Segmentation:

#### Model 1: Brain tumor

- Train size 500 sample 
- Val size 100 sample
- The best result of our experiments: Unet + VGG19 as encoder & cusom_loss='dice_iou_loss'


- Visulization output:

![image](https://user-images.githubusercontent.com/43317809/235372513-98a760c7-3837-4723-b016-b7328e3f0671.png)


#### Model 2: Breast tumor
- Train size 577 sample 
- Val size 69 sample
-	The Vgg19 as encoder gives best accuracy but takes more time to train on each epoch
	
  The MobileNet as expected was faster but gives a bad accuracy compared to VGG19

- The best result of our experiments: Unet + VGG19 as encoder & cusom_loss='dice_iou_loss'


- Visualization of the output 

![image](https://user-images.githubusercontent.com/43317809/235372621-f1e7cbef-8648-46dc-9391-5fe5c70432b5.png)

