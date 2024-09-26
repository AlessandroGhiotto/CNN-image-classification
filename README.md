# CNN image classification

We are given a dataset containing $186$ images which are categorized
into three classes, depending on the main object they contain. The following
inputs are available:

1. $\textit{input image}$, a $227 \times 227 \times 3$ real-valued tensor. The last dimension
   denotes the number of input channels $(RGB)$. Each pixel is a value in
   $[0, 255]$;
2. $\textit{image label}$, integer in the set ${1, 2, 3}$ denoting one of three possible
   objects an image can contain. There are $63$, $62$, and $61$ images belonging
   to the class $1$, $2$ and $3$, respectively;
3. $\textit{image bounding box}$, four integers $x_1$, $y_1$, $x_2$, $y_2$ in the range $1-227$, where
   $(x_1, y_1)$ and $(x_2, y_2)$ are the bottom-left and the top-right corners of the
   box containing the object, respectively.

Design a deep neural network model (with Keras) to predict the class of an image along
with the corresponding bounding box coordinates.

## Description

### Data

Here we can take a quick look at the three different classes of the images in the data:

![classes](https://github.com/AlessandroGhiotto/CNN-image-classification/blob/main/img/1-classes.png)

### Model

The model is constituted by a convolutional part made of inception blocks, followed by two classification heads. The two heads have the following output layers:

- _'output_label'_ : `Dense(n_classes, activation='softmax')` $\rightarrow$ probability distribution over the $3$ classes
- _'output_bbox'_ : `Dense(4, activation='sigmoid')` $\rightarrow$ predict a value in $[0, 1]$ for each coordinate of the corners of the bounding box

![classes](https://github.com/AlessandroGhiotto/CNN-image-classification/blob/main/img/2-model.png)

### Result

Here we can visualize the result. The dashed red bbox is the one predicted by the model, the green one is the true bbox.

![classes](https://github.com/AlessandroGhiotto/CNN-image-classification/blob/main/img/3-result1.png)

![classes](https://github.com/AlessandroGhiotto/CNN-image-classification/blob/main/img/3-result2.png)
