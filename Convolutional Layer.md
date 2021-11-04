- where most of the computation happens
- transforms 3D -> 3D via a differentiable function, a  [[convolutions|convolution]] by  computing a dot product between their weights and a small region they are connected to in the input volume
	- you can think of as [[convolutions#^412357|sliding the kernel matrix through the image]] 
- the function doesn't depend only on the activations in the input volume, but also of the parameters (the weights and biases of the neurons)

# Understanding the parameters of `conv2d`

- I was confused about the first 2 args of the function  `conv2D(IN,OUT)`. For a convolution, I expected the output to be smaller than the input  (see [[convolutions#^26cd04]]).  However, this refers to a layer and to the number of channels not features, and not the number of pixels/features. So, ignoring the other parameters for now (i.e. stride (1,1), padding(0,0), dilation(1,1,)) looking at only the number of kernels being applied and their size, we can see that for an RGB image with 3 channels if I decide to apply 4 kernels to the image. I'll get an output of 4 whose dimensions are still given by the formula  ![[convolutions#^26cd04]] , so there will be a total of 12 convolutions being applied (4 KERNELS * 3 CHANNELS) , resulting in an output layer of the 4 convolutions (the interim convolutions of each kernel for each channel are added up together to form the output)
	- ![[Pasted image 20211104123909.png]]
- If we take all the parameters into account then the output dimension can be expressed as a function of the input and these parameters as $$
\begin{array}{l}H_{\text {out }}=\frac{H_{\text {in }}+2 P_{H}-D_{H}\left(K_{H}-1\right)-1}{S_{H}} \\ W_{\text {out }}=\frac{W_{\text {in }}+2 P_{W}-D_{W}\left(K_{W}-1\right)-1}{S_{W}}\end{array}
$$
- Most of this content was taken from this [excellent post](https://towardsdatascience.com/conv2d-to-finally-understand-what-happens-in-the-forward-pass-1bbaafb0b148?gi=73a0f8867a56) which goes into more depth, and also speaks about why you might want to change the other parameters and a visualisation of what they do see this 