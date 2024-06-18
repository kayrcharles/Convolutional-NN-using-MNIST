# Convolutional-NN-using-MNIST
This is a convolutional neural network (CNN) that uses the MNIST dataset provided by the PyTorch library. The model is able to predict the number shown with a 96% success rate. However, this could be the first time you are interacting with a CNN. Below I added personal notes on websites I have read. 

**What is a convolution neural network? Why do we need them?**

In traditional neural networks, there are three main layers: an input layer, a hidden layer, and an output layer. However, not all datasets benefit from this three-layer approach. For instance, consider creating a program to recognize the surroundings of a self-driving car. The model needs to read the road ahead, analyze the relationships between features on the road, and make a prediction based on this analysis. This process, known as image classification, is similar to various other datasets that require image analysis, ranging from dog classification to satellite photo analysis. The three-layer approach often falls short for these complex tasks due to the intricate relationships between features. This challenge extends to video and audio recognition as well. This is where convolutional neural networks (CNNs) come into play.

**Math**

Before diving into the layers of a CNN, it's crucial to understand its basic function. Convolution is a mathematical operation where a filter (or kernel) is applied to the weights of a network, typically in matrix form for multiplication. This kernel slides across the entire image, analyzing each pixel. A good rule of thumb is to choose a 3x3 or 5x5 matrix to move across the image. Then, in the end, a value is calculated based on the filter using a convolution operation, and a feature map is generated for each filter. This allows us to take them through the activation functions and decide whether a certain feature is present at the given location in the image.  

How is this useful? In standard neural networks, there is no inherent mechanism to discern the relationships between features in images. Applying a kernel allows the model to extract these features effectively. The result is generally a 2x2 matrix. However, padding can be used to increase the size of the output matrix by adding zeros around its edges, this also allows for image sharpening. With this understanding of convolutions and their mathematical operations, we can dive into the layers and architecture of a CNN.

**Convolutional Layers**

A CNN is composed of five main layers: input, convolution, max pooling, fully connected, and output layers. The input layer receives the data and prepares it for the model. Each convolutional layer aims to extract increasingly complex features from the images. The next layer which is a part of this model, and most important, would be the convolutional layer. When the data is passing through this layer, this is where the convolutional computation we discussed earlier is happening. The use of kernels, aka filters, are applied across the image being taken in and detect edges, textures, and more complex patterns. Having this layer is important because it helps to maintain the relationship between the pixels in an image. 
The next layer which happens right after the convolutional layer is the pooling layer. In this part of the process, the number of parameters is reduced to learn the amount of computation that has been performed in the network, which reduces the complexity. In simpler terms, the goal of the pooling layers is to divide the input into small regions which makes the computations easier to avoid overfitting. This is possible through pooling windows which perform the operation of finding the maximum value within each of these windows, or chunks that the data is split into. While these are vital for these networks, some possible issues can occur, for example, the loss of information and insensitivity to small shifts.
Lastly, the fully connected layers make the final predictions, which are then presented in the output layer. The goal of these layers is to make predictions based on the information and numbers that have been given from convolutional and pooling layers. During the forward pass, the fully connected layers must be flattened after the convolution and pooling layers. All layers, except the output layer, pass through an activation function such as ReLU to introduce nonlinearity.
