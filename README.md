Neural Style Transfer

To run this code you have to download 'imagenet-vgg-verydeep-19.mat' from this link: "https://www.kaggle.com/teksab/imagenetvggverydeep19mat?select=imagenet-vgg-verydeep-19.mat"
and extract the zip file to 'pretrained-model' folder.


# Architecture

  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/neural%20network%20arcitecture.jpeg)
  
Loss function
=

# 1. content loss:

  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/content_loss.png)
  
# 2.style loss

  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/style%20loss.png)

# where gram_matrix is being calculated by 

  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/gram_matrix.png)

# 3. Total loss

  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/total%20loss.png)


# Why we have used gram matrix in style loss
It’s great that we know how to compute the style loss. But you still haven’t been shown “why the style loss is computed using the Gram matrix”. The Gram matrix essentially captures the “distribution of features” of a set of feature maps in a given layer. By trying to minimise the style loss between two images, you are essentially matching the distribution of features between the two images.
  

So let me take a shot at explaining this a bit more intuitively. Say you have the following feature maps. For simplicity I assume only three feature maps, and two of them are completely inactive. You have one feature map set where the first feature map looks like a dog, and in the second feature map set, the first feature map looks like a dog upside down. Then if you try to manually compute content and style losses, you will get these values. This means that we haven’t lost style information between two feature map sets. However, the content is quite different.

![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/why.png)


# The result will look like this
  
 
![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/d4.jpg)  +  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/d6.jpg)   =  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/generated_image.jpg)

content_image   +   style_image     =   generated image

