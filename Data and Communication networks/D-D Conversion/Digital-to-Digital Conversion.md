> The conversion involves three techniques: line coding, block coding, and scrambling.
## Line Coding

* Line coding converts a sequence of bits to a digital signal. 
* At the sender, digital data are encoded into a digital signal; at the receiver, the digital data are recreated by decoding the digital signal.

![[Pasted image 20240820190648.png]]

### Line Coding Schemes

1. Unipolar scheme - NRZ
2. Polar schemes - NRZ (NRZ-L, NRZ-I), RZ, Bi-phase (Manchester and Differential Manchester)
3. Bipolar - AMI, pseudo-ternary
4. Multilevel
5. Multi-transition

![[Pasted image 20240820233639.png]]
![[Pasted image 20240820233702.png]]
![[Pasted image 20240820233716.png]]
![[Pasted image 20240820233738.png]]

#### AMI - Alternate Mark Inversion

> AMI is commonly used for long-distance communication, but it has a synchronization problem when a long sequence of 0's present in the data. It can be solved by scrambling techniques.

Mark means 1, => telegraphy term, So, Alternate 1 inversion.

![[Pasted image 20240820234053.png]]

![[Pasted image 20240820235211.png]]

## Block Coding (mB/nB coding)

* block coding changes a block of m bits into a block of n bits, where n is larger than m
* need redundancy to ensure synchronization and to provide some kind of inherent error detecting.

## Scrambling

1. B8ZS 
2. HDB3

> B8ZS substitutes eight consecutive zeros with 000VBOVB.

![[Pasted image 20240821000444.png]]

>HDB3 substitutes four consecutive zeros with 000V or BOOV depending on the number of nonzero pulses after the last substitution.

![[Pasted image 20240821000841.png]]
