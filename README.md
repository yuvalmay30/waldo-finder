# waldo-finder
In this repository I represent the "Waldo Finder".  

# Problem Definition
The target is to detect Waldo in the original images of "Where's Waldo" books.
It is an hard task for humans because Waldo is extremely small, hiding behind objects and 


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
