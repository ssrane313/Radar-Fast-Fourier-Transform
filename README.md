# Radar-Fast-Fourier-Transform
 Implementing Fast Fourier Transform on a sample signal
In the following exercise, you will use a Fourier transform to find the frequency components of a signal buried in noise. Specify the parameters of a signal with a sampling frequency of 1 kHz and a signal duration of 1.5 seconds.

To implement the 1st stage FFT, you can use the following steps:

Define a signal. In this case (amplitude = A, frequency = f)

signal = A*sin(2*pi*f*t)

Run the FFT for the signal using the MATLAB FFT function for the dimension of samples N.

signal_fft = fft(signal,N);

This returns the N-point DFT. If N is not specified, signal_fft is the same size as signal.

The output of FFT processing of a signal is a complex number a+jb. Since we just care about the magnitude we take the absolute value sqrt(a^2+b^2) of the complex number.

signal_fft = abs(signal_fft);

FFT output generates a mirror image of the signal. But we are only interested in the positive half of signal length L since it is the replica of the negative half and has all the information we need.

signal_fft  = signal_fft(1:L/2+1)       

Plot this output against frequency.

Fs = 1000;            % Sampling frequency                    
T = 1/Fs;             % Sampling period       
L = 1500;             % Length of signal
t = (0:L-1)*T;        % Time vector
A1 = 0.7;             % Amplitude
A2 = 2;               % Amplitude
