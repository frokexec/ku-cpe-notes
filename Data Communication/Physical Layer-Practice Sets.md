# Physical Layer-Practice Sets

1. What is the relationship between period and frequency?
	- f = 1/T, T=1/f
2. What does the amplitude of a signal measure? What does the frequency of a signal measure? What does the phase of a signal measure?
	1. Amplitude - The value
	2. Frequency - How many period in 1 s
	3. Phase - Position of the waveform
3. How can a composite signal be decomposed into its individual frequencies?
	1. Use fourier transform
4. Name three types of transmission impairment.
	1. Attenuation - a loss of energy
	2. Distortion - signal changes its form or shape (mostly seen on composite signal)
	3. Noise
5. Distinguish between baseband transmission and broadband transmission.
	1. Baseband - Sends a digital signal over a channel without changing the digital signal to an analog signal. Needs a low-pass channel.
	2. Broadband - Change the digital signal to an analog signal, modulation allows it to use a bandpass channel (bandwidth doesn't start from zero)
6. Distinguish between a low-pass channel and a band-pass channel.
	1. A low-pass channel is a communication channel or a filter that allows lower-frequency components of a signal to pass through while attenuating higher-frequency components
	2. A band-pass channel is a communication channel or a filter that allows a specific range of frequencies
7. What does the Nyquist theorem have to do with communications?
	1. It defines maximum bitrate of a noiseless channel
8. What does the Shannon capacity have to do with communications?
	1. Theoretical maximum bit rate of a noisy channel.
9. Why do optical signals used in fiber optic cables have a very short wave length?
	1. Shorter wavelengths allow for higher data transmission rates
	2. Low Attenuation
10. Can we say whether a signal is periodic or nonperiodic by just looking at its frequency domain plot? How?
	1. Yes, periodic -> distinct peak, nonperiodic -> continuous (no distinct peak)
11. Is the frequency domain plot of a voice signal discrete or continuous?
	1. Continuous
12. Is the frequency domain plot of an alarm system discrete or continuous?
	1. Discrete
13. We send a voice signal from a microphone to a recorder. Is this baseband or broadband transmission?
	1. Baseband
14. We send a digital signal from one station on a LAN to another station. Is this baseband or broadband transmission?
	1. Baseband
15. We modulate several voice signals and send them through the air. Is this baseband or broadband transmission?
	1. Broadband

## Problems

1. What is the phase shift for the following?
	1. A sine wave with the maximum amplitude at time zero: 1/2pi
	2. A sine wave with maximum amplitude after 1/4 cycle: 0
	3. A sine wave with zero amplitude after 3/4 cycle and increasing: 1/2pi
2. What is the bandwidth of a signal that can be decomposed into five sine waves with frequencies at 0, 20, 50, 100, and 200 Hz? All peak amplitudes are the same. Draw the bandwidth.
	1. ![[Pasted image 20230817145508.png]]
3. A periodic composite signal with a bandwidth of 2000 Hz is composed of two sine waves. The first one has a frequency of 100 Hz with a maximum amplitude of 20 V; the second one has a maximum amplitude of 5 V. Draw the bandwidth.
	1. Bandwidth is 2000, 2 freqs 2000 and 100: max freq = 2100
	2. ![[Pasted image 20230817145533.png]]
4. Which signal has a wider bandwidth, a sine wave with a frequency of 100 Hz or a sine wave with a frequency of 200 Hz?
	1. Simple signal: bandwidth = 0
5. What is the bit rate for each of the following signals?
	1. A signal in which 1 bit lasts 0.001 s: 1/0.001
	2. A signal in which 1 bit lasts 2 ms: `1/2e-3`
	3. A signal in which 10 bits last 20 μs: `10/20e-6`
6. A device is sending out data at the rate of 1000 bps.
	1. How long does it take to send out 10 bits?: `1000 = 10/s`
	2. How long does it take to send out a single character (8 bits)?: `1000 = 8/s`
	3. How long does it take to send a file of 100,000 characters?: `100000*8/1000`
7. What is the bit rate for the signal ![[Pasted image 20230817150512.png]]
	1. 8/16e-9 = 500 Mbps
8. What is the bandwidth of the composite signal ![[Pasted image 20230817150804.png]]
	1. 180-155 or `5*5` = 25 Hz
9. A periodic composite signal contains frequencies from 10 to 30 KHz, each with an amplitude of 10 V. Draw the frequency spectrum.
	1. ![[Pasted image 20230817151041.png]]
10. A nonperiodic composite signal contains frequencies from 10 to 30 KHz. The peak amplitude is 10 V for the lowest and the highest signals and is 30 V for the 20-KHz signal. Assuming that the amplitudes change gradually from the minimum to the maximum, draw the frequency spectrum.
	1. ![[Pasted image 20230817151227.png]]
11. A TV channel has a bandwidth of 6 MHz. If we send a digital signal using one channel, what are the data rates if we use one harmonic, three harmonics, and five harmonics?
	1. one harmonic: `2 * 6e+6 / 1`
	2. three harmonics: `2 * 6e+6 / 3`
	3. five harmonics: `2 * 6e+6 / 5`
12. A signal travels from point A to point B. At point A, the signal power is 100 W. At point B, the power is 90 W. What is the attenuation in decibels?
	1. 100W A->B 90W: attenuation = dB = 10log10(90/100) = -0.457574906
13. The attenuation of a signal is −10 dB. What is the final signal power if it was originally 5 W?
	1. -10 = 10log10(Y/5): Y=0.5W
14. A signal has passed through three cascaded amplifiers, each with a 4 dB gain. What is the total gain? How much is the signal amplified?
	1. Total gain = 4+4+4 = 12 dB
	2. Amplified by 10^(12 dB / 10) = 15.849
15. If the bandwidth of the channel is 5 Kbps, how long does it take to send a frame of 100,000 bits out of this device?
	1. frame size / bandwidth = 1e5/5e+3 = 20 s
16. A signal has a wavelength of 1 μm in air. How far can the front of the wave travel during 1000 periods?
	1. `1000*1e-6` = 1mm
17. A line has a signal-to-noise ratio of 1000 and a bandwidth of 4000 KHz. What is the maximum data rate supported by this line?
	1. `4000 * log2(1+1000)` = 40 Kbps
18. We measure the performance of a telephone line (4 KHz of bandwidth). When the signal is 10 V, the noise is 5 mV. What is the maximum data rate supported by this telephone line?
	1. `4000 * log2(1+10/5e-3)` = 43866 bps
19. A file contains 2 million bytes. How long does it take to download this file using a 56-Kbps channel? 1-Mbps channel?
	1. 56 Kbps: `2e6*8/56e3`: 286 s
	2. 1 Mbps: `2e6*8/1e6`: 16 s
20. A computer monitor has a resolution of 1200 by 1000 pixels. If each pixel uses 1024 colors, how many bits are needed to send the complete contents of a screen?
	1. `1200*1000*log2(1024)`
21. A signal with 200 milliwatts power passes through 10 devices, each with an average noise of 2 microwatts. What is the SNR? What is the SNRdB?
	1. `10log10(200e-3/(10*2e-6))`
22. What is the theoretical capacity of a channel in each of the following cases?
	1. Bandwidth: 20 KHz SNR dB = 40; C = `20e3 * 40/3`
	2. Bandwidth: 200 KHz SNR dB = 4; C = `200e3 * 4/3`
	3. Bandwidth: 1 MHz SNR dB = 20; C = `1e6 * 20/3`
23. We need to upgrade a channel to a higher bandwidth. Answer the following questions:
	1. How is the rate improved if we double the bandwidth? 2x
	2. How is the rate improved if we double the SNR? +1
24. We have a channel with 4 KHz bandwidth. If we want to send data at 100 Kbps, what is the minimum SNRdB? What is the SNR?
	1. C = B × (SNRdB /3)
	2. `3*100e3/4e3` =75
	3. SNR = `10^(SNRdB/10)` = 10^7.5
25. What is the transmission time of a packet sent by a station if the length of the packet is 1 million bytes and the bandwidth of the channel is 200 Kbps?
	1. `1e6/200e3`
26. What is the length of a bit in a channel with a propagation speed of 2 × 10^8 m/s if the channel bandwidth is
	1. 1 Mbps? Bit length = `2e8 m/s * 1/(1 Mbps)`
	2. 10 Mbps?
	3. 100 Mbps?
27. How many bits can fit on a link with a 2 ms delay if the bandwidth of the link is
	1. 1 Mbps? Number of bits = bandwidth × delay = 1 Mbps × 2 ms = 2000 bit
	2. 10 Mbps?
	3. 100 Mbps?
