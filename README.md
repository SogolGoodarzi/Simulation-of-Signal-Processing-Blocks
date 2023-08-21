# Simulation-of-Signal-Processing-Blocks

## DTFT Block:
For creating this block we wrote a function called DTFT which calculates the DTFT of signals with the following expression:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/09439693-77b9-4dc0-bfbb-4eab7aaca054)

Now through this function we want to calculate the DTFT of the following two signals and plot the results:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/7c0f8a60-cbde-40b8-8dce-951522c0711a)

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/8502fed5-73d6-4209-8017-0003dc3e52dc)
![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/aba1bc07-651d-405d-9075-72a3edba9ad1)

## Compressor Block:
<p align="justify"> We have simulated the compressor block with a function called Compressor which takes the signal and compression factor and returns the compressed signal that is calculated with the following formula: </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/75abb86a-645a-4a64-90a1-7da6cf307588)

<p align="justify"> Now we want to test this function for an example. Consider $x_{c}(t)=sinc^2(t)$. Sample this signal in the interval [-4 sec, 4 sec] with sampling frequency of 10Hz and then compress the signal with these factors: M:{2,4} and plot the results. </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/1bb149b8-ab5e-42a0-92e1-0ca8b438c851)

## Expander Block:
We do the same thing we done for the compressor function and create Expander function with the following formula:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/2ba089fa-61c4-4ea8-9efe-ad6fdb9d69d3)

So the result of using this function for the previous example with expansion factors L=2 and L=4 is as follows:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/5a6f11b1-2d4a-4a1a-b05d-bdbf0a08e540)

## Interpolation Block:
<p align="justify"> In this part we aim to simulate interpolation block with three different methods. So, first of all consider the following block diagram: </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/2db9865f-0887-4a7f-94f1-94e5e6061273)

<p align="justify"> The reason for using the interpolator block after the expander block is that when the expansion operation is performed, L-1 zeros is actually placed between both samples in the main signal. These zeros cause the overall shape of the original signal to change. So, in order to preserve the overall shape of the original signal to a good extent and not to have very strong fluctuations between two samples of the signal, we use interpolation. </p>

<p align="justify"> Now we consider a variable called "mode" which can select the interpolation method. Before simulating the methods, it's better to define each method briefly. </p>

#### Ideal Interpolation:
<p align="justify"> In this interpolation method, according to the conversion function given in the project, it can be seen that its function is that it convolutes the desired signal in the sinc function to obtain the interpolated or recovered signal. The following formula can be used to simulate this method:</p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/697836e0-5b1c-4327-a140-9536da282df0)

#### Linear Interpolation:
<p align="justify"> In this method, the interpolation is linear, which means that the interpolation is done by a line that passes through any two points we have. That is, first, the equation of the line that passes through the two mentioned points is obtained, and with a relatively good approximation, it can be said that the samples between these two points are placed on that line. The following formula can express the process as well. </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/e4c54a3a-8b59-4f6c-b9ab-38268b05c4aa)

#### Spline Interpolation:
<p align="justify"> In this interpolation method, we perform the interpolation by means of a 3rd degree polynomial that is placed between two points. The algorithm of this method is as follows: </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/dec8321e-1415-4819-a3dd-7d681810431b)

We have done the simulation of this method with "spline" function of MATLAB. 

<p align="justify"> Because the ideal interpolator uses the sink function for interpolation, it is better not to use it as much as possible. The reason for this is that the sinc function does not exist in reality because an infinite domain is required to describe it. In order to increase the accuracy of interpolation in this method, it is better to have a large range of this function, which is not easily possible. </p>

<p align="justify"> Now consider an example. $s(t)=cos(2\pi f_{c}t)$ in t:[0,1]. With the sampling frequency $F_{s}=20Hz$, sample $s(t)$ to reach $s_{d}[n]$. Then apply DTFT function on this signal. The results is shown in the following figure: </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/a42c4771-3398-4202-8e05-ad10852e7fa8)

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/6047b56f-3d14-4962-9936-6eedb79979e2)

Now we do the interpolation with all of the three methods for the previous signal.

* Ideal Interpolation Results:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/fa10f49c-5b5a-4250-a713-802dd41de1ba)

Mean-Squared Error: 

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/9142a167-8cdd-44ea-b9f2-a37f77ffda3d)

* Linear Interpolation Results:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/24f238de-8323-4b81-8794-320934fc6f77)

Mean-Squared Error: 

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/9bf50342-e9dd-44c4-bb0e-2ea8f07c7805)

* Spline Interpolation Results:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/c0fbbfbc-4c40-4f32-9534-368b1bf8df84)

Mean-Squared Error: 

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/1249be61-6de0-4d19-9795-e3495703cf0e)

<p align="justify"> According to the errors of different methods, it can be seen that the error of the linear method is less than the other two methods. The reason for this is that with fewer samples, this method performs better for interpolation. We have the most error for the spline method. In this section, because the number of samples was small, this method cannot accurately recover the function or the initial signal. In fact, this method is more effective for signals that are sampled with a higher frequency. The ideal method is also, as mentioned in part C, because it needs an unlimited range to be able to perform the recovery correctly, so here, where we have considered a limited range for it, its error is somewhat high. </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/080daaf4-0c78-45d4-a956-cb5cff977346)

Now for better insight, we do the previous parts with $F_{s}=200hz$. 

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/8990855d-4189-4152-b0d0-0a404723bbc8)

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/f8afd536-e2fc-44de-91b3-61e509f9b607)

* Ideal Interpolation Results:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/e2bb625f-b48b-41e4-a6f8-e81ea344d222)

Mean-Squared Error: 

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/3848d612-9167-4d72-afa5-bac2558d888d)

* Linear Interpolation Results:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/ef576e3b-8bac-4f01-bb0c-d5544d12f93c)

Mean-Squared Error: 

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/96e99ecc-2f31-405f-b12c-3cbd77b88f5a)

* Spline Interpolation Results:

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/d9a8a3de-19a9-4764-b3cc-add043af27ea)

Mean-Squared Error: 

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/f613ddb9-e8e9-455d-abdd-c251e92a3069)

  <p align="justify"> According to the errors reported for this part, we can see that all the errors have decreased from the errors obtained in the previous part, due to the increase in sampling frequency. We also see that the error of the linear method is the least, so it is the most effective method for recovering the initial signal. The error of the ideal method is the most, the reason for which was explained in the previous sections. The error of the spline interpolator has decreased compared to the previous mode, and here it recovers the signal with a good approximation because the number of samples is more. </p>

![image](https://github.com/SogolGoodarzi/Simulation-of-Signal-Processing-Blocks/assets/125180530/56f06156-c076-49b0-a2ea-24b507608a1d)

###### Final Conclusion: 

<p align="justify"> The more we increase the signal's sampling frequency, the better the interpolation methods are performed and the accuracy increases because the distance between the samples decreases so, the recovered signals will be closer to the original signal. </p>
