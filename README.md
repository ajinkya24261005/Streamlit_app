# NeuroStress - EEG Stress Detection System (Streamlit App)

A comprehensive EEG-based stress detection and classification system using the SAM-40 dataset with the novel MSA-CBL (Multi-Scale Attention CNN-BiLSTM) architecture.

## Features

- **Home**: Overview of the system with key metrics and quick navigation
- **Dataset & Setup**: SAM-40 dataset statistics and configuration
- **Model Training**: Simulated training with configurable hyperparameters and real-time visualization
- **Results & Metrics**: Confusion matrices, ROC curves, and classification reports
- **Implementation**: Interactive demonstration of all 4 research objectives
- **Research Paper**: Literature survey, research gaps, novel method, and stress analysis
- **Stress Detection**: Upload EEG spectrogram images for stress classification
- **Test Files**: Sample EEG images for testing
- **Help Guide**: Step-by-step instructions and FAQ

---

## Quick Start

```bash
cd streamlit_app
pip install -r requirements.txt
streamlit run app.py
```

Open `http://localhost:8501` in your browser.

---

## Running in Different IDEs/Editors

### PyCharm (Professional or Community)

#### Step 1: Open Project
1. Launch PyCharm
2. File → Open → Select `streamlit_app` folder
3. Right-click the folder → Mark Directory as → Sources Root

#### Step 2: Configure Python Interpreter
1. File → Settings (Windows/Linux) or PyCharm → Preferences (macOS)
2. Project → Python Interpreter
3. Click gear icon → Add Interpreter
4. Choose "New Environment" or "Existing Interpreter"
5. Select Python 3.8+ interpreter
6. Click OK

#### Step 3: Install Dependencies
1. Open Terminal (View → Tool Windows → Terminal)
2. Run:
   ```bash
   pip install -r requirements.txt
   ```

#### Step 4: Create Run Configuration
1. Run → Edit Configurations
2. Click "+" → Python
3. Configure:
   - **Name**: Streamlit App
   - **Script path**: Leave empty
   - **Module name**: `streamlit`
   - **Parameters**: `run app.py`
   - **Working directory**: `/path/to/streamlit_app`
4. Click Apply → OK

#### Step 5: Run the Application
- Click the green Run button (▶) or press Shift+F10
- Or open Terminal and run: `streamlit run app.py`

---

### Spyder

#### Step 1: Open Project
1. Launch Spyder
2. Projects → New Project → Existing directory
3. Select `streamlit_app` folder
4. Click Create

#### Step 2: Configure Python Interpreter
1. Tools → Preferences → Python interpreter
2. Select interpreter with required packages installed
3. Click Apply → OK

#### Step 3: Install Dependencies
Open IPython Console (bottom-right) and run:
```python
!pip install -r requirements.txt
```

#### Step 4: Run the Application

**Method 1: Using IPython Console**
```python
import os
os.chdir('/path/to/streamlit_app')  # Change to your path
!streamlit run app.py
```

**Method 2: Using External Terminal**
1. Open your system terminal (cmd, PowerShell, or Terminal)
2. Navigate to the project:
   ```bash
   cd /path/to/streamlit_app
   ```
3. Run:
   ```bash
   streamlit run app.py
   ```

**Method 3: Create Custom Run Script**
Create a file `run_app.py` in the project folder:
```python
"""
Run this file to start the Streamlit app.
Execute in IPython console: %run run_app.py
"""
import subprocess
import os

os.chdir(os.path.dirname(os.path.abspath(__file__)))
subprocess.run(['streamlit', 'run', 'app.py'])
```
Then run in IPython: `%run run_app.py`

#### Step 5: Access the App
- The app opens automatically in your browser
- Keep the IPython console running
- URL: `http://localhost:8501`

---

### Visual Studio Code

#### Step 1: Open Folder
1. Launch VS Code
2. File → Open Folder
3. Select `streamlit_app` folder

#### Step 2: Select Python Interpreter
1. Press Ctrl+Shift+P (Cmd+Shift+P on macOS)
2. Type "Python: Select Interpreter"
3. Choose Python 3.8+ interpreter

#### Step 3: Install Recommended Extensions
1. Python (Microsoft)
2. Pylance
3. Streamlit (optional, for syntax highlighting)

#### Step 4: Install Dependencies
1. Open Terminal (Ctrl+` or View → Terminal)
2. Run:
   ```bash
   pip install -r requirements.txt
   ```

#### Step 5: Run the Application

**Method 1: Using Integrated Terminal**
```bash
streamlit run app.py
```

**Method 2: Create Launch Configuration**
1. Create folder `.vscode` in project root
2. Create file `.vscode/launch.json`:
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Streamlit App",
            "type": "python",
            "request": "launch",
            "module": "streamlit",
            "args": ["run", "app.py"],
            "cwd": "${workspaceFolder}",
            "console": "integratedTerminal"
        }
    ]
}
```
3. Press F5 to run

**Method 3: Create Tasks**
Create `.vscode/tasks.json`:
```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Run Streamlit",
            "type": "shell",
            "command": "streamlit run app.py",
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```
Press Ctrl+Shift+B to run.

---

### Jupyter Notebook / JupyterLab

#### Method 1: Magic Command
In a notebook cell:
```python
!cd /path/to/streamlit_app && streamlit run app.py
```

#### Method 2: Using ngrok for Remote Access
```python
# Install dependencies
!pip install streamlit pyngrok

# Start Streamlit in background
!nohup streamlit run app.py &

# Create public tunnel
from pyngrok import ngrok
public_url = ngrok.connect(8501)
print(f"Access app at: {public_url}")
```

#### Method 3: subprocess
```python
import subprocess
import webbrowser

# Start Streamlit
process = subprocess.Popen(['streamlit', 'run', 'app.py'])

# Open browser
webbrowser.open('http://localhost:8501')
```

---

### Command Line (Any Terminal)

```bash
# Navigate to project
cd /path/to/streamlit_app

# Create virtual environment (recommended)
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the app
streamlit run app.py

# Run on specific port
streamlit run app.py --server.port 8502

# Run accessible from network
streamlit run app.py --server.address 0.0.0.0 --server.port 8501
```

---

## Project Structure

```
streamlit_app/
├── app.py                 # Main Streamlit application
├── eeg_processing.py      # EEG processing module (all 4 objectives)
│                          # - EEGDataCleaner: Signal cleaning
│                          # - FeatureExtractor: Feature extraction
│                          # - CNNModel, BiLSTMModel, MSACBLModel: Deep learning
│                          # - ModelValidator: Validation metrics
├── config.py              # Configuration settings
├── data_loader.py         # Data loading utilities
├── model.py               # Model definitions
├── utils.py               # Helper functions
├── requirements.txt       # Python dependencies
├── README.md              # This documentation
├── assets/                # Image assets
│   ├── normal_eeg.png     # Sample normal EEG
│   ├── stressed_eeg.png   # Sample stressed EEG
│   └── ...
└── data/                  # EEG data files
    └── raw/               # Raw .mat files
```

---

## Mathematical Reference

### eeg_processing.py - Complete Documentation

The `eeg_processing.py` module contains comprehensive mathematical documentation:

#### 1. Signal Processing (Objective 1)

**Butterworth Bandpass Filter:**
```
|H(jω)|² = 1 / [1 + (ω/ωc)^(2n)]

Parameters: n=4, f_low=0.5 Hz, f_high=45 Hz
```

**Notch Filter (50/60 Hz removal):**
```
H(s) = (s² + ω₀²) / (s² + (ω₀/Q)·s + ω₀²)

Parameters: Q=30, f₀=50 or 60 Hz
```

**Artifact Detection (Z-score):**
```
z_i = (x_i - μ) / σ
artifact if |z_i| > 4
```

#### 2. Feature Extraction (Objective 2)

**Time Domain Features (11 total):**
```
Mean:       μ = (1/N) Σ xᵢ
Std:        σ = √[(1/N) Σ(xᵢ-μ)²]
Skewness:   γ₁ = E[(X-μ)³] / σ³
Kurtosis:   γ₂ = E[(X-μ)⁴] / σ⁴ - 3
Hjorth Activity:   var(x)
Hjorth Mobility:   √[var(x')/var(x)]
Hjorth Complexity: Mobility(x')/Mobility(x)
```

**Frequency Domain Features (15 total):**
```
PSD (Welch):  Pxx(f) = (1/K) Σₖ |FFT(xₖ·w)|²
Band Power:   P_band = ∫ Pxx(f) df

Bands: δ(0.5-4Hz), θ(4-8Hz), α(8-13Hz), β(13-30Hz), γ(30-45Hz)
```

**Wavelet Features (24 total):**
```
DWT: x(t) = Σⱼ Σₖ cⱼ,ₖ · ψⱼ,ₖ(t)

Wavelet: db4 (Daubechies-4)
Levels: 5 decomposition levels
Features: Energy, Entropy, Mean, Std per level
```

#### 3. Deep Learning (Objective 3)

**LSTM Equations:**
```
Forget gate:  fₜ = σ(Wf·[hₜ₋₁, xₜ] + bf)
Input gate:   iₜ = σ(Wi·[hₜ₋₁, xₜ] + bi)
Cell update:  Cₜ = fₜ⊙Cₜ₋₁ + iₜ⊙tanh(Wc·[hₜ₋₁, xₜ] + bc)
Output gate:  oₜ = σ(Wo·[hₜ₋₁, xₜ] + bo)
Hidden:       hₜ = oₜ ⊙ tanh(Cₜ)
```

**Self-Attention:**
```
Attention(Q,K,V) = softmax(QK^T/√dₖ) · V
```

**SE-Attention:**
```
z = GlobalAvgPool(F)
s = σ(W₂ · ReLU(W₁ · z))
F' = F ⊙ s
```

#### 4. Validation Metrics (Objective 4)

```
Accuracy:    (TP + TN) / Total
Precision:   TP / (TP + FP)
Recall:      TP / (TP + FN)
F1-Score:    2·Precision·Recall / (Precision + Recall)
Specificity: TN / (TN + FP)
MCC:         (TP·TN - FP·FN) / √[(TP+FP)(TP+FN)(TN+FP)(TN+FN)]
```

**Stress Biomarkers:**
```
Beta/Alpha Ratio = P_β / P_α
  > 2.0 → Stressed state
  < 1.0 → Relaxed state

Stress Index = (P_β + P_γ) / (P_α + P_θ)
```

---

## Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| `ModuleNotFoundError` | `pip install -r requirements.txt` |
| `streamlit: command not found` | `pip install streamlit` |
| Port 8501 in use | `streamlit run app.py --server.port 8502` |
| Can't access from network | Use `--server.address 0.0.0.0` |
| scipy import error | `pip install scipy numpy` |
| PyWavelets not available | `pip install PyWavelets` |

### Finding Process Using Port
```bash
# Linux/macOS
lsof -i :8501

# Windows
netstat -ano | findstr :8501
```

### Firewall Configuration
```bash
# Linux (Ubuntu)
sudo ufw allow 8501

# Windows
# Open Windows Firewall → Advanced Settings → Inbound Rules
# Add new rule for port 8501 (TCP)
```

---

## Docker Deployment

### Build and Run
```bash
cd streamlit_app
docker build -t neurostress-streamlit .
docker run -p 8501:8501 neurostress-streamlit
```

### Docker Compose
```yaml
version: '3.8'
services:
  neurostress:
    build: .
    ports:
      - "8501:8501"
    environment:
      - STREAMLIT_SERVER_ADDRESS=0.0.0.0
    restart: unless-stopped
```

---

## License

MIT License

## Citation

```bibtex
@article{neurostress2024,
  title={MSA-CBL: Multi-Scale Attention CNN-BiLSTM for EEG Stress Detection},
  author={NeuroStress Research Team},
  year={2024}
}
```

## Contact

For issues or questions, please open an issue in the repository.
