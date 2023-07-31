# Direct Memory Access Structure

![[Pasted image 20230719152855.png]]

- Used for high-speed I/O devices able to transmit information at close to memory speeds
- Transfers blocks of data from buffer storage directly to main memory **without CPU intervention**
- Only one interrupt is generated per block, rather than the one interrupt per byte

## DMA Example

if a computer wants to send data from system memory to a printer, it issues a DMA transfer request to the printer's DMA controller
