# MATLAB Simulation Code for "Capacity of a Binary Channel with a Time-Bounded Adversary"

This MATLAB script simulates the performance of a 5G NR LDPC-coded communication system under adversarial interference. It evaluates how different adversarial strategies, such as bit-flipping attacks, impact system performance using Bit Error Rate (BER) and Block Error Rate (BLER) metrics across a range of Signal-to-Noise Ratio (SNR) levels.

## Features

- **Modulation:** 64-QAM  
- **Coding Rate:** Fixed at 1/3  
- **Base Graph:** Implements 5G NR LDPC Base Graph 1 (BG1)  
- **Adversarial Models:**  
  - No Adversary: Standard communication without interference  
  - Minimax Adversary: Worst-case bit-flipping strategy  
  - Fixed Flipping: Targeted bit flipping at fixed positions  
- **Decoding Options:**  
  - Thresholded Log-Likelihood Ratio (LLR) clipping for improved decoding robustness  
- **Performance Metrics:**  
  - BER and BLER, calculated over varying SNR levels and adversarial strategies  

## Requirements

### Software

MATLAB is required to run this simulation.

### Toolboxes

- **Communications Toolbox** for QAM modulation/demodulation and LDPC encoding/decoding.

## Usage Instructions

### Run the Script

Execute the script in MATLAB. The simulation will process all specified SNR levels and methods.

### Outputs

- **MAT File:** Results are saved in a `.mat` file named `BG1_results_1.mat`, which includes:
  - `BERavg`: Average BER for each method and SNR  
  - `BLERavg`: Average BLER for each method and SNR  
  - `SNRdB`: SNR values used in the simulation  
  - `methStr`: Descriptions of each method  

- **Figures:**
  - **Figure 1:** BER vs. SNR for all methods  
  - **Figure 2:** BLER vs. SNR for all methods  

## Key Parameters

| Parameter     | Description                                  | Value         |
|---------------|----------------------------------------------|---------------|
| `bitsPerSym`  | Bits per symbol (modulation order)           | `6` (64-QAM)  |
| `coderate`    | Coding rate                                  | `1/3`         |
| `BG`          | 5G NR LDPC Base Graph                        | `1` or `2`    |
| `K`           | Information block size (bits)                | `8448` or `3840`|
| `N`           | Encoded block size (bits)                    | `25344`       |
| `maxNumIter`  | Maximum number of decoding iterations        | `50`          |
| `flipProb`    | Probability of bit flipping by the adversary | `0.01`        |
| `numTrials`   | Number of trials for each SNR and method     | `10000`        |
| `SNRdB`       | Range of SNR values (dB)                     | `0:0.1:20`    |

## Notes

- The simulation uses fixed modulation (64-QAM) and coding rate (1/3) as specified.  
- Adversarial strategies can be modified by changing the `advType` and `llrClip` arrays in the script.  
- Adjust `numTrials` and `SNRdB` to balance simulation accuracy and execution time.  
- Ensure the MATLAB **Communications Toolbox** is installed for proper functionality.  

## Citation

M. Ying, F. B. Sarpkaya, S. Bakirtas, E. Erkip, T. S. Rappaport, and S. Rangan, "Capacity of a binary channel with a time-bounded adversary," in *2024 58th Asilomar Conference on Signals, Systems, and Computers*, Pacific Grove, CA, USA, Oct. 2024, pp. 1–5.
