# Report
In the following model we demonstrate the weiner filter and an algorithm to help optimize parameters taken while constructing the weiner filter 

## Wiener Filter

Wiener filter is a signal filter which tries to minimze the mean square error between the input image and the output image. Thus given an image with blur and noise added, we can create a filter which restores the image. Thus considering the mean square minimization 

<img src="trailset/mean-square.png" width="250" />

simplifying the following equation in terms of Values we know, we get the following 

    W = H`/(|H|^2 + |N|^2/|F|^2)

where 
- H is the impulse response in the fourier domain
- N is the Power Spectral Density of the input signal 
- F is the Power Spectral Density of the Noise function

However given we don't we have the input image and the noise function, we require an estimate for **N** and **F** , thus in our given formula we substitute 

    |N|^2/|F|^2 = k

Thus our task now is to find the optimum **k** value for a general the filter we have produced. 

In order to that, we first define our metric. We define the **SNR Improvement** as the following 

    Spectral Density of input noise / Spectral Density of Output noise

Where input noise is simply and the mod difference of the corrupted image and the input image and the output noise is the mod difference between the corrupted image and restored image



#### Optimisation-1

In the first optimization we assume k to be a scalar vector. We then vary the value of k, and find the optimum value for our training set. 

We then apply the following k for all other images.

The short coming for this optimization is that we are assuming a constant values for all values of the k-matrix

#### Optimization-2

In the second optimization, given our training set, we find the value optimum value of k, assuming that we have the power spectral density of the input image, along with that of the noise. 

We then average this value and take this as our general

The short coming for this, is that we are using input image and noise data. Although by using a large number of images, this value of k can be genralised for all images, and can be used as a general k.