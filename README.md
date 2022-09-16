# Detect Wheat Heads using YOLOv5 network
The YOLOv5s network was used to detect wheat clusters in the GWHD2021 database. The small version was chosen because the training process in COLAB had limited resources, and the larger YOLOv5 models could not be implemented with these resources.
Due to the limitation of RAM space in COLAB, it is not possible to use images with the original size of 1024*1024. For this reason, images with the size of 512*512 have been given to the network. It should be noted that if the images are too small, the characteristics of the image will not be precise. For example, in the 256x256 image, some clusters are not recognized even by humans. To speed up the training process, the batch size was set to 64. This value is selected according to the amount of available RAM.

The network weights were not randomly initialized at the beginning of the training, and the network weights that were previously trained on the COCO database were used. Starting training from this value will make the network learn faster and better. Also, the weights of the first 10 layers of the network, which are related to Backbone, have been frozen to reduce the number of trainable parameters. Finally, the training process was implemented for 100 epochs in about 60 minutes. And at the end, the best value of the coefficients and coefficients of the last stage were saved along with the results.

## Result
The following results were obtained by Training on 3655 train data and 1476 validation data. The results can be seen in the Figure. The mAP0.5 index for validation data has reached the value of 0.854 in the best case, which means that the box detected by the network meets the actual box with at least 50% of its area in 85% of the cases. We test an image from the test set using the best coefficients. The Below image shows the clusters detected by the network. It can be seen that all wheat clusters have been well recognized. Finally, for the final test of the network, we validate the network using all test data. We reach the mAP index value of 0.5, equal to 0.48. The confusion matrix diagram can be seen below.

<img src="https://github.com/alireza-montazeri/GWHD-YOLOv5/blob/master/Result/detect/exp2/032037a1be58cbb3d4bf5ae1d34721f4e88800b0c73b0d9dc965cc64e72fc4ef.png" />

<img src="https://github.com/alireza-montazeri/GWHD-YOLOv5/blob/master/Result/train/exp2/results.png" />

<img src="https://github.com/alireza-montazeri/GWHD-YOLOv5/blob/master/Result/val/exp2/confusion_matrix.png" />