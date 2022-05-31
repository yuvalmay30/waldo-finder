<img src="https://user-images.githubusercontent.com/83128966/171216384-1564cdc5-5e97-4c9e-89bc-be23d7b9410f.jpg" alt="drawing" width="400"/>


# Waldo Finder
In this repository I represent the "Waldo Finder".  

# Problem Definition
The target is to detect Waldo in the original images of "Where's Waldo" books.  
It is an hard task for humans because Waldo is extremely small and is hiding behind objects.  
Moreover, there are a lot of characters that are similar to waldo (wearing similar outfit for example).  

All in all, the target is to detect Waldo (say bbox-wise) ASAP and beat humans searching for Waldo.  
We can look at it like a recommendation system:  
* The user uploads an image to the system
* The system outputs the same image with bounding-boxes around possible Waldos

## Metrics
The system (or model) will be evaluated by the `Hit-Rate@k` metric (or `Recall@k`).  
'Recall@k' - Recall at k is the proportion of relevant items found in the top-k recommendations.  
A more intuitive explanation for this problem: The system recommend on `k` possible Waldos for each image, while each image contains no more than 1 Waldo. For each image we get a simple result, either the system recommended on Waldo or not (like a binary result). The final metric takes the mean of the results of all images.


# Data
The data consists of 70 images containg Waldos. I collected all the images by searching the internet, and tagged them myself (using `Roboflow` which is a great tool for tagging and processing images).  
The dataset is splitted by the following:
* Train Set - 42 images
* Validation Set - 20 images
* Test set - 8 images

# Research  
## Model
I chose to use YOLOv5 as a base model for this problem. The main reasons to choose YOLOv5 are:  
* It is the SOTA in terms of performance
* It is a good generalization model, means that the backbone of the network is great in "understanding the image" and can be used to understand images which the model didn't trained on (like pictures and animations)
YOLOv5 struggles with localization, but for this problem it doesn't hurt much because we "only" recommend on the location of Waldo and it doesn't have to be a perfect bounding-box.  

I tried out-of-the-box yolov5x model on a couple of images to examine if the model detects Waldo as "Person": 

<img src="https://user-images.githubusercontent.com/83128966/171216186-411d573d-aa72-4e1b-aa19-b5d0e276595c.png" alt="drawing" width="500"/>

<img src="https://user-images.githubusercontent.com/83128966/171216200-f51c44b8-e8cd-41d2-aaa6-97ae9602b82c.png" alt="drawing" width="500"/>



# Results
| Model | Metric | Result |
| ----- | ------ | ------ |
| pretrained yolov5x + fine-tune (unfreezed) | Hit-Rate@5 (resize=2400px) | 0.9% (18/20)
| pretrained yolov5x + fine-tune (unfreezed) | Hit-Rate@5 with rectangular padding | 0.85% (17/20)
| pretrained yolov5x + fine-tune (unfreezed) | Hit-Rate@5 with tiling | 0.85% (17/20)
| pretrained yolov5x + fine-tune (freezed backbone) | Hit-Rate@5 (resize=2400px) | 0.85% (17/20)
| pretrained yolov5x + fine-tune (freezed backbone) | Hit-Rate@5 with rectangular padding | 0.85% (17/20)
| pretrained yolov5x + fine-tune (freezed backbone) | Hit-Rate@5 with tiling | 0.85% (17/20)
