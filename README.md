
# MATLAB Simulation Code for Paper "Capacity of a Binary Channel with a Time-Bounded Adversary"

## Overview
This .mlx file simulates the performance of Low-Density Parity-Check (LDPC) decoding in 5G New Radio (NR) systems under adversarial interference. It evaluates the system using different modulation and coding schemes (MCS) and adversarial strategies while considering realistic parameters from 5G standards. Performance metrics such as Bit Error Rate (BER) and Block Error Rate (BLER) are calculated over varying Signal-to-Noise Ratio (SNR) levels.

---

## Features
- **Modulation Types:** Supports 64-QAM and 256-QAM.
- **MCS Types:** Three options for coding rates:
  - `conservative`: Low code rate for robust decoding.
  - `moderate`: Balanced code rate for average performance.
  - `aggressive`: High code rate for high data throughput.
- **Base Graphs:** Implements 5G NR LDPC Base Graphs 1 (BG1) and 2 (BG2).
- **Adversarial Models:**
  - `no adv`: No adversarial interference.
  - `minimax`: Worst-case adversary.
  - `fix flip`: Targeted bit flipping.
- **Decoding Options:**
  - Thresholded Log-Likelihood Ratio (LLR) clipping for improved robustness.
  - Early termination for efficient decoding.
- **Performance Metrics:**
  - BER and BLER calculated across multiple SNR levels and adversarial strategies.

---

## Requirements
### **Software**
- MATLAB 

### **Toolboxes**
- Communications Toolbox (for QAM modulation/demodulation and LDPC encoding/decoding).
- Parallel Computing Toolbox (optional, for parallel execution).

---

## Usage Instructions

1. **Set Simulation Parameters:**
   - Modify `modulation` to `'64QAM'` or `'256QAM'`.
   - Choose `mcsType` as `'conservative'`, `'moderate'`, or `'aggressive'` based on desired coding rate.
   - Adjust other simulation parameters, including `numTrials`, `flipProb`, and `maxNumIter`.

2. **Run the Script:**
   - Execute the script in MATLAB. Intermediate results (BER, BLER) will be displayed for each method and SNR level.

3. **Outputs:**
   - BER and BLER for all SNR levels and adversarial strategies are stored in arrays.
   - Results are saved in a `.mat` file named based on modulation, MCS, and Base Graph (e.g., `256QAM_moderate_BG1_results.mat`).
   - Graphs:
     - BER vs. SNR (`Figure 1`).
     - BLER vs. SNR (`Figure 2`).

4. **Adjust Simulation Details:**
   - Modify the number of decoding iterations (`maxNumIter`) or the SNR range (`SNRdB`) as needed.
   - Add or remove adversarial strategies by editing the `advType` array.

---

## Key Parameters
| Parameter           | Description                                         | Values                             |
|---------------------|-----------------------------------------------------|------------------------------------|
| `modulation`        | Modulation type                                    | `'64QAM'`, `'256QAM'`             |
| `mcsType`           | Modulation and coding scheme type                  | `'conservative'`, `'moderate'`, `'aggressive'` |
| `BG`                | 5G NR LDPC Base Graph                              | `1`, `2`                          |
| `K`                 | Information block size (bits)                      | Based on MCS and Base Graph       |
| `N`                 | Encoded block size (bits)                          | Calculated from `K` and coderate  |
| `maxNumIter`        | Maximum number of decoding iterations              | `64`                              |
| `flipProb`          | Probability of bit flipping by the adversary       | `0.01`                            |
| `numTrials`         | Number of trials for each SNR and method           | `10000`                            |
| `SNRdB`             | Range of SNR values (dB)                           | `(0:0.1:20)`                      |

MCS and Base Graph setting please refer to:
- 3GPP Technical Specification TS 38.212: *Multiplexing and channel coding*.
- 3GPP Technical Specification TS 38.214: *Physical layer procedures for data*.

---

## Outputs
1. **MAT File:** Contains BER, BLER, SNR values, method descriptions, and LDPC parameters.
   - Example: `256QAM_moderate_BG1_results.mat`.
2. **Figures:**
   - **Figure 1:** BER vs. SNR for all methods.
   - **Figure 2:** BLER vs. SNR for all methods.

---

## Example Configuration
```matlab
modulation = '256QAM';
mcsType = 'moderate';
maxNumIter = 64;
flipProb = 0.01;
numTrials = 10000;
SNRdB = (0:0.1:20)';
```

---

## Notes
- Ensure the lifting size and encoded block length (`N`) meet 5G NR standards.
- Verify that adversarial strategies comply with defined constraints (e.g., flip probability).

---

## Citation

M. Ying, F. B. Sarpkaya, S. Bakirtas, E. Erkip, T. S. Rappaport, and S. Rangan, "Capacity of a binary channel with a time-bounded adversary," in *2024 58th Asilomar Conference on Signals, Systems, and Computers*, Pacific Grove, CA, USA, Oct. 2024, pp. 1–5.




---

Feel free to reach out for clarifications or modifications to this script.
