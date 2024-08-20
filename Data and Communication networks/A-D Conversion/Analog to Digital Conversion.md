1. Pulse Code Modulation
2. Delta Modulation

>After the digital data are created (digitization), we can use one of the Digital to Digital conversion techniques to convert the digital data to a digital signal.

## Pulse Code Modulation

>The most common technique to change an analog signal to digital data (digitization) is called pulse code modulation (PCM). A PCM encoder has three processes,

![[Pasted image 20240821002317.png]]

1. The analog signal is sampled. 
2. The sampled signal is quantized. 
3. The quantized values are encoded as streams of bits.

### Sampling (Pulse Amplitude Modulation)

#### Sampling rate

>According to the **Nyquist** theorem, to reproduce the original analog signal, one necessary condition is that the sampling rate be at least twice the highest frequency in the original signal

![[Pasted image 20240821003151.png]]

![[Pasted image 20240821003827.png]]

### Encoding

$$
Bit rate = sampling.rate * number.of.bits.per.sample = f_s X n_p
$$
