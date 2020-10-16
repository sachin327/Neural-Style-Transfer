Neural Style Transfer

To run this code you have to download 'imagenet-vgg-verydeep-19.mat' from this link: "https://www.kaggle.com/teksab/imagenetvggverydeep19mat?select=imagenet-vgg-verydeep-19.mat"
and extract the zip file to 'pretrained-model' folder.

The result will look like this
=
  
 
![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/d4.jpg)  +  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/d6.jpg)   =  ![alt text](https://github.com/sachin327/Neural-Style-Transfer/blob/master/generated_image.jpg)

content_image   +   style_image     =   generated image

  
Loss function
=

# 1. content loss:

  a_C -- tensor of dimension (1, n_H, n_W, n_C), hidden layer activations representing content of the image C 
  
  
  a_G -- tensor of dimension (1, n_H, n_W, n_C), hidden layer activations representing content of the image G
 
  J_content = 1/(4*n_H*n_W*n_C) *tf.reduce_sum((a_C - a_G)**2)
  
# 2.style loss

  a_S -- tensor of dimension (1, n_H, n_W, n_C), hidden layer activations representing style of the image S 
  
  
  a_G -- tensor of dimension (1, n_H, n_W, n_C), hidden layer activations representing style of the image G
  
  
  GS = gram_matrix(a_S)
  GG = gram_matrix(a_G)

  
  J_style_layer = 1/(4*((n_H*n_W)**2)*(n_C**2)) *tf.reduce_sum((GS - GG)**2)

# where gram_matrix is being calculated by 

  GA = tf.matmul(A, A, transpose_b=True)

# 3. Total loss

  J = alpha*J_content+ beta*J_style

