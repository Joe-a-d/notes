- in the mathematical sense convolutions are .. 
	- [ ] insert function multiplication see DF notes
# ML
- w.r.t to ML such as when they are used in [[Convolutional Layer|convolutional layers]] you can think of them as applying *element-wise* multiplication between the filter and the image. Sliding the kernel across the entire image and outputting the result to the resulting matrix
	- ![[Pasted image 20211012161149.png]] ^412357
	- note how for a $I_{j \times k}$ and $K_{m \times n}$ the resulting convolution $C$ has dimensions $(j-m+1) \times (k-n+1)$ if we assume no padding, i.e. we can only move inside the image ^26cd04
	- in conv layers often more than one filter is applied and the tensor is ND, in that case the process is repeated for each of the filters but the same rule applies with the new dimension being equal to the number of filters 