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
A more intuitive explanation foe this problem: The system recommend on `k` possible Waldos for each image, while each image contains no more than 1 Waldo. For each image we get a simple result, either the system recommended on Waldo or not (like a binary result). The final metric takes the mean of the results of all images.


# Data




# Results
| Model | Metric | Result |
| ----- | ------ | ------ |
| pretrained yolov5x + fine-tune (unfreezed) | Hit-Rate@5 (resize=2400px) | 0.9% (18/20)
| pretrained yolov5x + fine-tune (unfreezed) | Hit-Rate@5 with rectangular padding | 0.85% (17/20)
| pretrained yolov5x + fine-tune (unfreezed) | Hit-Rate@5 with tiling | 0.85% (17/20)
| pretrained yolov5x + fine-tune (freezed backbone) | Hit-Rate@5 (resize=2400px) | 0.85% (17/20)
| pretrained yolov5x + fine-tune (freezed backbone) | Hit-Rate@5 with rectangular padding | 0.85% (17/20)
| pretrained yolov5x + fine-tune (freezed backbone) | Hit-Rate@5 with tiling | 0.85% (17/20)
