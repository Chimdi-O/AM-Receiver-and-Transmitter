# AM-Receiver-and-Transmitter

# Introduction

This project is a basic AM transmitter and receiver which aims to be able to transmit signals across a room (2-3m). 

This project serves to introduce basic RF concepts to me  like mixers, filters and antennas. 

# Design

## Block Diagram    

<img width="802" height="392" alt="image" src="https://github.com/user-attachments/assets/07725a9a-d30b-4df5-9f9e-2146ac430ca8" />





<img width="1111" height="238" alt="image" src="https://github.com/user-attachments/assets/c4b61984-d923-4a2b-a8a6-f9e2a6d1ee28" />


## Circuit

### Transmitter

#### Oscillator - Colpitts Oscillator

**Description** 

The Colpitts Oscillator functions through tuned feedback. The circuit is a Common Emitter Amplifier with a LC tank as feedback.

All oscillators must fulfil the Barkhausen criterion which state for an oscillator to function it must have a loop gain of above 1 and a total phase shift of 0/360 degrees. 

The feedback network provides a phase shift of 180 degrees because of the centre tapped capacitors but it also provides an attenuation equal to the ratio between the capacitors. The CE amp provides another 180 phase shift bringing the total to 0 degrees but for the loop gain to be one the attenuation provided by the capacitors must be equal or smaller than the gain provided by the transistor. 

This circuit was chosen as when the basics of transistors are already understood its quite easy to get an output of a specific frequency and amplitude. Additionally the carrier wave frequency I want is 1Mhz which is very close to the bandwidth of the average Op Amp which rules out op amp oscillators.

**Circuit values**

<img width="520" height="356" alt="image" src="https://github.com/user-attachments/assets/e199d309-1ab4-47d7-ab7e-f45de9b13577" />


- Output Frequency - 1Mhz
- Output Amplitude - 1.5V
- Output impedance - 2kΩ

### **Modulator - Differential Amplifier Mixer** 

**Description** 

This modulator works inputting the modulating signal into the current source of the differential amplifier and inputting the carrier wave normally. The modulating signal then influences the tail current which then in turn changes the gain of the amplifier proportionally to itself effectively multiplying the two signals achieving AM modulation. 

The outputs are connected by a tank to improve linearity. 

This was chosen because its method of modulation is easy to understand and calculate compared to something like a square law modulator. Additionally I’m already familiar with differential pairs

**Circuit Values** 


<img width="356" height="378" alt="image" src="https://github.com/user-attachments/assets/216cbf03-ddc9-479e-b0da-f408f6c253c8" />

- Input Impedance - 20kΩ
- Output Impedance - 20kΩ
- Input Voltage Swing - 2V
- Output Voltage Swing - 500mV
- Resonant Frequency - 1Mhz

**Output Stage - Darlington pair**

**Description** 

Simple Darlington pair. 

**Circuit values** 

<img width="164" height="303" alt="image" src="https://github.com/user-attachments/assets/8db3e226-c17b-453d-a1d6-4c9ce6291bed" />


- Input Impedance - 1MΩ
- Output Impedance - 100Ω
- Input Voltage swing - 0.6V (Vb = 4.5V = VDC)
- Output Voltage swing - 1.6V

## Receiver

**Demodulator - Op Amp peak detector**

This was chosen for its simplicity. It allows the entire receiver to be done in almost in a single stage 

**Output Stage - Emitter follower** 

Volume is not a concern with this circuit so the voltage swing does not need to be rail to rail like a push pull stage could provide so a simpler emitter follower was chosen. 

# Roadmap 
- [ ] Design AM demodulator
- [ ] Build Transmitter and Reciever prototypes
- [ ] Design PCB
- [ ] Build PCB 
