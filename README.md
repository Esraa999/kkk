[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-f059dc9a6f8d3a56e377f745f24479a46679e63a5d9fe6f495e02850cd0d8118.svg)](https://classroom.github.com/online_ide?assignment_repo_id=6222227&assignment_repo_type=AssignmentRepo)
# SBEN424-Advanced-CV-Lab-02-Template
* Rokaia Mohamed
* Doaa Sherif

# Requirements
* cv2
* os
* math
* numpy
* scipy.io
* pandas
* matplotlib.pyplot
* confusion_matrix **from** sklearn.metrics
* directed_hausdorff **from** scipy.spatial.distance
* threshold_otsu **from** skimage.filters
* data **from** skimage

# Segmentation Evaluation in 2D
First, we collect all of the outputs of each algorithm in an array, along with the ground truth images in another.

To evaluate the algorithms, we binarized each algorithm to predefined thresholds, then generated the confusion matrix for each algorithm at these different thresholds and compared it to its corresponding ground truth image to obtain TP, TN, FP, FN, TPR, and FPR at all thresholds.

### Evaluation Critera
The first three criteria are obtaines at best threshold for each algorithm:
* Jaccard and Dice at best threshold
* Sensitivity and specificity at best threshold
* Hausdorff distance
* Area under the curve

## Results
## Image 1
| Algorithms | Jaccard |Dice | Sensitivity | Specificity | AUC |Best Threshold|
| :---  |    :----:   |    :----:   |    :----:   |    :----:   |    :----:   |---: |
Alg1|	0.141876|	0.248496|	0.292752|	0.991382|	0.712172|	30.0
Alg2|	0.044023|	0.084334|	0.631579|	0.891846|	0.800162|	80.0
Alg3|	0.725658|	0.841022|	0.810916|	0.999048|	0.958712|	20.0
Alg4|	0.122997|	0.219052|	0.597200|	0.968757|	0.788847|	100.0
Alg5|	0.284419|	0.442876|	0.422470|	0.996067|	0.934047|	70.0
Alg6|	0.075241|	0.139952|	0.760943|	0.926149|	0.786155|	10.0

| Algorithms | Hausdorff Distance |
| :---   | ---: |
Alg1|	9.273618
Alg2|	13.564660
Alg3|	4.472136
Alg4|	10.099505
Alg5|	5.744563
Alg6|	9.797959

### ROC Curve
![Image 1](./Captures/Capture1.JPG)

From the above curve, we can see that **algorithm 3** is the closest one to (0, 1) point which indicates that it's the best for **image 1**.

---

## Image 2
| Algorithms | Jaccard |Dice | Sensitivity | Specificity | AUC |Best Threshold|
| :---       |    :----:   |    :----:   |    :----:   |    :----:   |    :----:   |---: |
Alg1|	0.000753|	0.001504|	0.011465|	0.936049|	0.345928|	10.0
Alg2|	0.109168|	0.196847|	0.775478|	0.972577|	0.938987|	120.0
Alg3|	0.000000|	0.000000|	0.000000|	1.000000|	0.000000|	0.0
Alg4|	0.091307|	0.167336|	0.730255|	0.968559|	0.814342|	90.0
Alg5|	0.000000|	0.000000|	0.000000|	0.999382|	0.000000|	250.0
Alg6|	0.033112|	0.064101|	0.809873|	0.894598|	0.781586|	10.0

| Algorithms | Hausdorff Distance |
| :---   | ---: |
Alg1|	11.401754
Alg2|	9.746794
Alg3|	7.681146
Alg4|	10.344080
Alg5|	7.681146
Alg6|	12.688578

### ROC Curve
![Image 2](./Captures/Capture2.JPG)

From the above curve, we can see that **algorithm 2** is the closest one to (0, 1) point which indicates that it's the best for **image 2**.

---

## Image 3
| Algorithms | Jaccard |Dice | Sensitivity | Specificity | AUC |Best Threshold|
| :---       |    :----:   |    :----:   |    :----:   |    :----:   |    :----:   |---: |
Alg1|	0.468384|	0.637959|	0.493384|	0.998963|	0.713261|	20.0
Alg2|	0.062647|	0.117907|	0.651043|	0.817549|	0.770083|	100.0
Alg3|	0.347853|	0.516159|	0.619646|	0.984822|	0.836435|	20.0
Alg4|	0.101272|	0.183919|	0.358227|	0.950712|	0.643861|	90.0
Alg5|	0.428000|	0.599440|	0.456156|	0.998722|	0.963043|	70.0
Alg6|	0.106990|	0.193299|	0.755999|	0.882162|	0.772648|	10.0

| Algorithms | Hausdorff Distance |
| :---   | ---: |
Alg1|	7.937254
Alg2|	17.464249
Alg3|	11.180340
Alg4|	11.916375
Alg5|	8.306624
Alg6|	14.594520

### ROC Curve
![Image 3](./Captures/Capture3.JPG)

From the above curve, we can see that **algorithm 5** is the closest one to (0, 1) point which indicates that it's the best for **image 3**.

---

## Image 4
| Algorithms | Jaccard |Dice | Sensitivity | Specificity | AUC |Best Threshold|
| :---       |    :----:   |    :----:   |    :----:   |    :----:   |    :----:   |---: |
Alg1|	0.329706|	0.495908|	0.439091|	0.994699|	0.659876|	30.0
Alg2|	0.082787|	0.152914|	0.746581|	0.871877|	0.841897|	100.0
Alg3|	0.725990|	0.841245|	0.820216|	0.997926|	0.948469|	20.0
Alg4|	0.249066|	0.398804|	0.567793|	0.979552|	0.635565|	90.0
Alg5|	0.524839|	0.688386|	0.552124|	0.999169|	0.958839|	120.0
Alg6|	0.098336|	0.179063|	0.736890|	0.896237|	0.720465|	10.0

| Algorithms | Hausdorff Distance |
| :---   | ---: |
Alg1|	8.000000
Alg2|	16.062378
Alg3|	6.244998
Alg4|	9.486833
Alg5|	6.082763
Alg6|	12.609520

### ROC Curve
![Image 4](./Captures/Capture4.JPG)

From the above curve, we can see that **algorithm 5** is having the biggest area under the curve which indicates that it's the best for **image 4**.

---

# Segmentation Evaluation in 3D

## Results
|    |Hausdorff Distance| Jaccard |Dice |
| :---  |    :----:   |    :----:   |    ---: |
Min|	0.000000|	0.000000|	0.000000
Max|	4.000000|	0.680851|	0.81012
Mean|	1.450212|	0.217072|	0.286856

# What Evaluation Measure is the Best?
* The probability of Jaccard getting the best algorithm in 2D is 2/4
* The probability of Dice getting the best algorithm in 2D is 3/4
* The probability of Hausdorff Distance getting the best algorithm in 2D is 3/4

From the stated points above, we see that Dice and Hausdorff Distance are the best evaluation measures.

# Troubles Encountered in the Assignment
One of the major issues encountered while working is the running time, which can exceed 5 minutes for a single cell, particularly when obtaining the confusion matrix:

We could mitigate this issue by implementing two functions for obtaining the confusion matrix at various thresholds:
* one implemented on our own *get_confusion*
* another one using built-in function *get_confusion_faster*

The 2 function have the same output, but we continued our work with *get_confusion_faster* to address the time issue.

Another issue is calculating the Hausdorff distance when the best threshold for the image is 0, which would cause the code to stop running:
* To avoid this issue, we used a built in function *directed_hausdorff* to obtain the correct output in this case.

# Suggestions
We recommend using additional metrics in addition to the ones already in use for better evaluation, such as: Hamming Distance, Cosine Index.

In addition, to address the time issue, we recommend using built-in functions to obtain the output faster.
