# SABCA - Simulated Annealing-Based Cipher Analysis

**SABCA** (Simulated Annealing-Based Cipher Analysis) is a Python library for encrypting, decrypting, and cracking substitution ciphers. It implements a **novel automated cracking method** proposed by us, combining **quadgram statistical analysis**, **linguistic syntax modeling**, and **optimization-based simulated annealing**. SABCA provides both CLI and GUI interfaces for flexible and interactive use.

## 🌟 Features

- **Automated Cipher Cracking**:
  Utilize our SABCA algorithm to efficiently break substitution ciphers.
- **Encryption/Decryption**:
  Encrypt plaintext or decrypt ciphertext using substitution keys.
- **Real-Time Visualization**:
  GUI includes live charts for fitness score and cracking progress.
- **Flexible Interaction**:
  Offers both GUI and CLI options for diverse user needs.
- **Educational and Practical**:
  Combines linguistics, probability, and optimization for cryptanalysis.

## 📦 Installation

### Prerequisites
- Python 3.8 or higher
- Libraries: `nltk`, `matplotlib`, `tkinter`

### Installation Steps
1. Clone the repository:

2. Install dependencies:

3. Run the program:
- **GUI mode**:
  ```
  python main.py
  ```
- **CLI mode**:
  ```
  python cli.py
  ```
## 🎮 How to Use

### GUI Mode
1. Launch the GUI:
2. Use the tabs for encryption, decryption, or cracking.
3. Visualize cracking progress with real-time charts.

### CLI Mode
1. Start the CLI version:
2. Select an option from the menu:
- **Encrypt**: Input plaintext and receive ciphertext with the key.
- **Decrypt**: Input ciphertext and a key to decrypt it.
- **Crack**: Automatically decrypt ciphertext without a key.
## 🔍 Mathematical Principles

1. **Quadgram Statistical Analysis**:
   - Text plausibility is evaluated using the frequencies of four-character sequences (quadgrams).
   - From the Brown Corpus, the probability of a quadgram is computed as:
     \[
     P(\text{quadgram}) = \log_{10}\left(\frac{\text{frequency of quadgram}}{\text{total quadgrams}}\right)
     \]
   - The fitness score of a decrypted text is the sum of log probabilities of all its quadgrams:
     \[
     \text{Fitness} = \sum_{i=1}^{n} P(\text{quadgram}_i)
     \]

2. **Simulated Annealing Optimization**:
   - Substitution keys are refined iteratively:
     - **Initial State**: Starts with a random substitution key.
     - **Key Mutation**: Two random key mappings are swapped.
     - **Acceptance Criterion**: Accepts mutations based on fitness improvement (\( \Delta \text{fitness} \)):
       \[
       P(\text{accept}) = 
       \begin{cases} 
       1, & \Delta \text{fitness} > 0 \\ 
       \exp\left(\frac{\Delta \text{fitness}}{T}\right), & \Delta \text{fitness} \leq 0 
       \end{cases}
       \]
       where \( T \) is the temperature parameter.

3. **Cooling Schedule**:
   - Temperature \( T \) decreases exponentially over iterations:
     \[
     T = T_0 \cdot \alpha^k
     \]
     Here, \( T_0 \) is the initial temperature, \( \alpha \) is the cooling rate, and \( k \) is the iteration count.

4. **Convergence**:
   - The algorithm balances exploration and exploitation to maximize fitness, yielding the most probable decryption.
