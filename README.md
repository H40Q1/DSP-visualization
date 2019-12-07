# DSP visualization: Noise Separation with python
Mini Porject 3 of EC601

## Introduction
In this mini project, a python file used to visualize DSP is represented. It firstly generated a 1000Hz signal and a 50Hz noise, and combined them together into a signal. Then it uses filtering and IFFT to find and convert out the original signal. 

## Generate wave and add noise to it

The SW part firstly generated a non-noise wave and a noise wave by using the wave library. The wave module provides a convenient interface to the WAV sound format. It does not support compression/decompression, but it does support mono/stereo.

The figure 1 shows below contains a generated sine wave. The non-noise frequency is 1000Hz, and we generated a 50Hz noise input.

The noise is added to the signal. Library numpy has such a convenient way to accumulate. If it is a normal python list, we need to write a for loop. In short, numpy is very convenient.

As showed in figure 1, the Original + Noise shows the combined signal of two input signals.

Figure 1:

![alt text](https://github.com/H40Q1/EC601MiniPro3/blob/master/figure1.png)

## Filtering two signals
Now let's filter the signal. It can be realized by using a FFT to create a simple filter. As showed in figure 2, a signal of 50Hz and 1000Hz is separated from the combined signal. 

Figure 2:
![alt text](https://github.com/H40Q1/EC601MiniPro3/blob/master/figure2.png)

Since we know my target signal frequency is 1000Hz, the code above will search for it near this value. The lower limit of 950 and the upper limit of 1050 are used here. The code checks whether the frequency of our loop is within this range.

## Finding single and clean the noise
Because I know that my target signal frequency is 1000Hz, as for the if else part, although all frequencies will have values to represent, their absolute values will be small, usually less 1. So once it find a value greater than 1, it will save it to the filtered frequency array.

If our frequency is not in the range we are looking for, or if the value is too low, it will just go to 0. This is designed to remove all frequencies we don't want. Then we move the index to the next value.

Now we use IFFT, the inverse of the FFT. This will take our signal and convert it back to the time domain. We can now compare it to the original noise signal. The figure 3 shows the result of the third part.



Figure 3:

![alt text](https://github.com/H40Q1/EC601MiniPro3/blob/master/figure3.png)

