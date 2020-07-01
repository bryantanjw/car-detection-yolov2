# Car Detection with YOLO

### This was intended for the Week 3 programming assignment on Convolutional Neural Network for [deeplearning.ai](https://www.coursera.org/specializations/deep-learning?).

## Summary for YOLO
Input image (608, 608, 3)

The input image goes through a CNN, resulting in a (19, 19, 5, 85) dimensional output.

After flattening the last two dimensions, the output is a volume of shape (19, 19, 425). Each cell in a 19 x 19 grid over the input image gives 425 numbers: 425 = 5 x 85 because each cell contains predictions for 5 boxes, corresponding to 5 anchor boxes; 85 = 5 + 80 where 5 is because (pc, bx, by, bh, bw) has 5 numbers, and 80 is the number of classes we'd like to detect.

We then select only a few boxes based on score-thresholding--discarding boxes that have detected a class with a score less than the threshold, and non-max suppression - computing the Intersection over Union (IOU) and avoiding selecting overlapping boxes.

This gives the YOLO's final output.

## Citations & References
The ideas presented in the notebook came primarily from the two YOLO papers. The implementation here also took significant inspiration and used many components from Allan Zelener's GitHub repository. The pre-trained weights used in this exercise came from the official YOLO website.

* Joseph Redmon, Santosh Divvala, Ross Girshick, Ali Farhadi - [You Only Look Once: Unified, Real-Time Object Detection] (https://arxiv.org/abs/1506.02640)(2015)

* Joseph Redmon, Ali Farhadi - [YOLO9000: Better, Faster, Stronger](https://arxiv.org/abs/1612.08242) (2016)

* Allan Zelener - [YAD2K: Yet Another Darknet 2 Keras](https://github.com/allanzelener/YAD2K)

* [The official YOLO website](https://pjreddie.com/darknet/yolo/)

**Car detection dataset**: The Drive.ai Sample Dataset (provided by drive.ai) is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).
