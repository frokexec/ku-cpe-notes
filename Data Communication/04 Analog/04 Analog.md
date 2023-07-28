# 04 Analog

Table of Contents

1. [Analog Conversion](#Analog%20Conversion)
	1. [Digital - Analog - Digital Conversion](#Digital%20-%20Analog%20-%20Digital%20Conversion)
2. [Carrier Signals](#Carrier%20Signals)
3. [Pure sine](#Pure%20sine)
4. [Digital to Analog Conversion](#Digital%20to%20Analog%20Conversion)
	1. [Data Rate VS Signal Rate](#Data%20Rate%20VS%20Signal%20Rate)
		1. [r in analog transmission](#r%20in%20analog%20transmission)
	2. [Bandwidth and Carrier Signal](#Bandwidth%20and%20Carrier%20Signal)
	3. [Amplitude Shift Keying](#Amplitude%20Shift%20Keying)
		1. [ASK Implementation](#ASK%20Implementation)
	4. [Frequency Shift Keying](#Frequency%20Shift%20Keying)
	5. [FSK implementation](#FSK%20implementation)
		1. [Multilevel FSK](#Multilevel%20FSK)
	6. [Phase Shift Keying](#Phase%20Shift%20Keying)
	7. [BPSK Implementation](#BPSK%20Implementation)
	8. [QPSK Implementation *](#QPSK%20Implementation%20*)
	9. [Constellation Diagram](#Constellation%20Diagram)
5. [Analog to Analog Conversion](#Analog%20to%20Analog%20Conversion)
	1. [Amplitude Modulation](#Amplitude%20Modulation)
		1. [AM band allocation](#AM%20band%20allocation)
	2. [Frequency Modulation](#Frequency%20Modulation)
		1. [FM band allocation](#FM%20band%20allocation)
	3. [Phase Modulation](#Phase%20Modulation)
6. [kw](#kw)

## Analog Conversion

- D-A - **Digital data** to **bandpass analog signal**
- A-A - **Low-pass analog signal** to **bandpass analog signal**

### Digital - Analog - Digital Conversion

- Uses **modem**

![[Pasted image 20230725092020.png]]

## Carrier Signals

aka Carrier Frequency
a high-frequency signal acting as a base for information signal

- pure wave of constant freq
- sine wave

![[Pasted image 20230725092011.png]]

## Pure sine

- Bandwidth = 0
- 1 discrete peak in freq domain

## Digital to Analog Conversion

- Sine wave is characterized by amplitude, freq, and phase
- Three mechanisms
	- Amplitude Shift Keying
		- สะบัด amp ให้มี bandwidth
	- Frequency Shift Keying
		- สะบัด freq ให้มี bandwidth
	- Phase Shift Keying
		- สะบัด freq ให้มี bandwidth
- All to Quadrature Amplitude Modulation

![[Pasted image 20230725092725.png]]

### Data Rate VS Signal Rate

![[Pasted image 20230725093327.png]]

- N: data rate (bps)
- r: number of data elements
- S: symbol per sec (baud)

#### r in analog transmission

![[Pasted image 20230725093903.png]]

- L: number of different signal elems

![[Pasted image 20230725093756.png]]
r = N * (1/r) = 8000/1000 = 8 data elems

### Bandwidth and Carrier Signal

- Bandwidth
	- … except for FSK
- Carrier Signal
	- ….

### Amplitude Shift Keying

สะบัดที่ Amplitude

- อ่อนต่อ noise
- OOK: On off keying
- Binary ASK

![[Pasted image 20230725094546.png]]

![[Pasted image 20230725094143.png]]

![[Pasted image 20230725094514.png]]

#### ASK Implementation

- Unipolar line coding

![[Pasted image 20230725095044.png]]
![[Pasted image 20230725095130.png]]

### Frequency Shift Keying

- 1 frequency ขี่ 1 bit
- อ่อนต่อ noise

### FSK implementation

- Unipolar line coding

![[Pasted image 20230725095413.png]]
![[Pasted image 20230725095421.png]]

#### Multilevel FSK

![[Pasted image 20230725095602.png]]

### Phase Shift Keying

- Less affected by noise (compared to ASK)
- outperforms FSK as it doesn't require **two carrier signals**
- requires more advanced hardware

![[Pasted image 20230725100413.png]]
![[Pasted image 20230725100420.png]]

### BPSK Implementation

- Bipolar line coding

![[Pasted image 20230725100625.png]]
![[Pasted image 20230725101027.png]]

### QPSK Implementation *

![[Pasted image 20230725101037.png]]
![[Pasted image 20230725101046.png]]

### Constellation Diagram

- Constellation (กลุ่มดาว)
- บอก Amplitude and Phase

![[Pasted image 20230725103849.png]]
[Visualization](https://www.cpe.ku.ac.th/~cpj/204325/tools/phasor/)

## Analog to Analog Conversion

### Amplitude Modulation

![[Pasted image 20230725112254.png]]
![[Pasted image 20230725112307.png]]

#### AM band allocation

![[Pasted image 20230725112441.png]]

### Frequency Modulation

![[Pasted image 20230725112509.png]]
![[Pasted image 20230725112524.png]]

#### FM band allocation

![[Pasted image 20230725112545.png]]

### Phase Modulation

- Similar to FM
![[Pasted image 20230725112631.png]]
![[Pasted image 20230725112638.png]]

## kw

- Baud rate
