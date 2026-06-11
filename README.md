# Costas Loop Based BPSK Carrier Recovery in MATLAB/Simulink

## Overview

This project implements a **Costas Loop** for **carrier recovery and coherent BPSK demodulation** using **MATLAB Simulink**. The model demonstrates how a feedback control system can synchronize a locally generated carrier with the received signal, enabling accurate demodulation.

The implementation includes the complete Costas Loop architecture consisting of:

* BPSK Transmitter
* Local Carrier Generator (NCO)
* In-phase (I) and Quadrature (Q) Multipliers
* Low Pass Filters (LPF)
* PI Loop Filter
* Closed-loop carrier synchronization

---

# Theory

A Costas Loop is a specialized Phase Locked Loop (PLL) widely used in digital communication systems for carrier recovery. It generates two orthogonal local carriers (cosine and sine), multiplies them with the received signal, filters the resulting components, and produces a phase error signal.

This error signal is processed by a PI controller, which continuously adjusts the local oscillator until the phase difference approaches zero. Once locked, the receiver can coherently demodulate the transmitted BPSK data.

---

# Block Diagram

```
                +----------------------+
                | Local Carrier        |
                | Generator (NCO)      |
                +----------+-----------+
                           |
                    Cosine & Sine
                           |
                           v
                 +--------------------+
Received Signal->| Internal Products  |
                 |   (I & Q Mixers)   |
                 +--------------------+
                           |
                           v
                 +--------------------+
                 | Low Pass Filters   |
                 +--------------------+
                           |
                           v
                 +--------------------+
                 | PI Loop Filter     |
                 +--------------------+
                           |
                           |
                           +----------------------+
                                                  |
                                                  |
                                      Feedback to NCO
```

---

# Features

* MATLAB Simulink implementation
* Costas Loop based carrier recovery
* BPSK coherent demodulation
* I/Q signal generation
* Low-pass filtering
* PI loop filtering
* Closed-loop synchronization
* Time-domain and frequency-domain analysis

---

# Simulation Results

## 1. Complete Costas Loop Architecture

The Simulink model consists of the transmitter, local carrier generator, internal products, LPF, and PI loop filter connected through a feedback loop.

---

## 2. I-Q Product After Lock

After the Costas Loop achieves lock, the I-Q product remains nearly zero with only very small residual fluctuations. This indicates successful carrier synchronization and stable loop operation.

---

## 3. PI Loop Filter Output

The PI controller generates the control signal for the local oscillator. During acquisition, oscillatory behavior is observed as the loop searches for the correct phase. Once synchronization is achieved, the control signal stabilizes.

---

## 4. FFT Analysis

The FFT of the loop filter output demonstrates effective suppression of the carrier frequency while preserving the low-frequency phase error component required for loop control.

---

# Project Files

```
├── CostasLoop.slx
├── Costasloop.png
├── FilterOutput.png
├── LoopLock.png
├── FFTloopfilter.png
└── README.md
```

---

# Software Used

* MATLAB
* Simulink

---

# Applications

* Digital Communication Systems
* BPSK Receivers
* Software Defined Radio (SDR)
* Satellite Communication
* Wireless Communication
* Carrier Recovery Systems

---

# Future Work

* BER vs SNR analysis
* Performance under AWGN channel
* Extension to QPSK Costas Loop
* FPGA implementation
* Adaptive loop filter design

---

# References

1. John G. Proakis – *Digital Communications*
2. Simon Haykin – *Communication Systems*
3. https://john-gentile.com/kb/dsp/PI_filter.html

---

## Author

This project was developed as an academic implementation of a **Costas Loop based BPSK carrier recovery system** using MATLAB/Simulink for studying synchronization techniques in digital communication systems.
