[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-f059dc9a6f8d3a56e377f745f24479a46679e63a5d9fe6f495e02850cd0d8118.svg)](https://classroom.github.com/online_ide?assignment_repo_id=6339443&assignment_repo_type=AssignmentRepo)
# SBEN424-Advanced-CV-Lab-03
# Fuzzy C Means
## RGB Images
### Algorithm Analysis 
1- Read the RGB images

2- Analyze the image in different color spaces(L *a *b, HSV, YCrCb)

3- Reshape images from (Rows, Cols, Channels) to (Rows*Cols,Channels) to be able to pass it to FCM function.

4- In FCM, after fitting the image and predicting the centers and labels, we get the segmented image using labels which are the new values of pixels after clustering.

Ex. Num of clusters of the woman image is 5, so the output of labels array, whose shape is of one dimension and equals Rows*Cols of original image, consists of 5 numbers [0, 1, 2, 3, 4]

5- ApplY FCM on all color spaces of images

## RGB Images
### Image 1
In this image, best number of clusters is 5 as each object is defined well in all color spaces.

![Image 1](./output/woman.png)

---

### Image 2
In this image, number of clusters is 3 as each object is defined well in all color spaces

![Image 2](./output/color.png)

The num of clusters of 4 resulted in distinct colors for each object as well as the background, however it didn't work the same all the times and some color spaces didn't give output as shown below.

![Image 22](./output/color2.png)
![Image 22](./output/color3.png)

Also, the output, of the color space of HSV in 4 clusters, isn't satisfying.

---
### Image 3
In this image, best number of clusters is 3 as each object is defined well in all color spaces.

![Image 3](./output/image3.png)

---
## Gray Image
### Algorithm analysis 
1- Read the gray-scale images

2- Reshape images from (Rows, Cols, Channels) to (Rows*Cols, Channels) to be able to pass it to FCM function.

3- Apply FCM on the image with num of clusters = 2

### Output
![Image 4](./output/coins.png)

When we tried to enhance the image and adjust the contrast, the output wasn't satisfying compared to the output beore enhancement as show below. 

![Image 5](./output/gray.png) ![Image 6](./output/coins1.png)

---

# EM Algorithm
## One-Dimension
First, three different subsets were initialized with different means and variances, and then grouped in one dataset.

Initialize number of clusters with 3, then initialize three random means and varinces representing the mean and variance of each cluster.

EM is then used which estimates the mixture model’s parameters (means, variances, and weights).

### Expectation Step
Calculate the probability that a data point 𝑥𝑖 belongs to each cluster using this equation of Bayes' theorem:

![Image 11](./output/1.jpg) 

``` python
def pdf(data, mean: float, variance: float):
    s1 = 1 / (np.sqrt(2 * np.pi * variance))
    s2 = np.exp(-(np.square(data - mean) / (2 * variance)))
    return s1 * s2

for j in range(k):
    likelihood.append(pdf(X, means[j], np.sqrt(variances[j])))
likelihood = np.array(likelihood)
print(likelihood.shape)
```
### Maximization Step
Based on the estimated values, generated in Expectation step, update the means, variaces, weights of each cluster, till it fits the original data means, and variances.

![Image 11](./output/2.jpg)
``` python
b = []

for j in range(k):
    b.append((likelihood[j] * weights[j]) / (np.sum([likelihood[i] * weights[i] for i in range(k)], axis=0) + eps))

    means[j] = np.sum(b[j] * X) / (np.sum(b[j] + eps))
    variances[j] = np.sum(b[j] * np.square(X - means[j])) / (np.sum(b[j] + eps))

    weights[j] = np.mean(b[j])
```

### Algorithm Time
The algorithm takes **0.9914393424987793** seconds without saving figures after each update. However, it takes **7.161893844604492** seconds after saving each figure step. 

For showing each step figure, it took **21.164411067962646** seconds

### Final Output
![Image 7](./output/img_24.png) 

---

## Two-Dimension
The main difference between 1D and 2D is that in 1D, we use the variances of each cluster, while in the 2D, we use **the covariances instead**.

## Expectation Step
```python
for j in range(k):
        likelihood.append(multivariate_normal.pdf(x=X, mean=means[j], cov=cov[j]))
    likelihood = np.array(likelihood)
    assert likelihood.shape == (k, len(X))
```

## Maximization Step
``` python
for j in range(k):
        b.append((likelihood[j] * weights[j]) / (np.sum([likelihood[i] * weights[i] for i in range(k)], axis=0) + eps))

        means[j] = np.sum(b[j].reshape(len(X), 1) * X, axis=0) / (np.sum(b[j] + eps))
        cov[j] = np.dot((b[j].reshape(len(X), 1) * (X - means[j])).T, (X - means[j])) / (np.sum(b[j]) + eps)

        weights[j] = np.mean(b[j])

        assert cov.shape == (k, X.shape[1], X.shape[1])
        assert means.shape == (k, X.shape[1])
```
### Output
![Image 8](./output/img_391.png) 

### Algorithm Time
The algorithm takes **0.40268397331237793** seconds without saving figures after each update. However, it takes **15.313929080963135** seconds after saving each figure step. 

For showing each step figure, it took **22.190564393997192** seconds

---
## 2D-EM VS. GMM by Scikit-Learn
The Gaussian Mixture Model provided by scikit-learn takes **0.18382954597473145** seconds, which is less than the time required to run the algorithm from scratch. In addition, the output is more accurate and pleasing when visualising, as the output of the model implemented from scratch wasn't always correct as shown below.

![Image 9](./output/GaussianMixture.png) ![Image 10](./output/img_39.png) 

## Conclusion
Gaussian Mixture Model provided by scikit-learn works better and faster than the model implemented from scratch.
