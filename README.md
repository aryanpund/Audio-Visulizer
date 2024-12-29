# Real-Time Audio Visualization with SPL and Frequency Bands

## Overview
This script provides a real-time audio visualization tool using Python. It captures audio input, processes it, and displays three components:
1. **Sound Pressure Level (SPL)**: Displays the current and maximum SPL values in decibels (dB).
2. **Frequency Spectrum**: Visualizes the frequency components of the audio signal.
3. **Frequency Bands**: Separates and visualizes the magnitude of Bass, Mid, and Treble frequency bands.

The visualization is rendered using Matplotlib, and audio input is handled using PyAudio.

---

## Requirements
To run the script, ensure you have the following Python packages installed:

- `numpy`
- `pyaudio`
- `matplotlib`

You can install these packages using pip:
```bash
pip install numpy pyaudio matplotlib
```

---

## Features
1. **SPL Visualization**:
   - Displays the current SPL value as a bar with a color that changes based on intensity.
   - Tracks and displays the maximum SPL value recorded during the session.

2. **Frequency Spectrum**:
   - Uses FFT (Fast Fourier Transform) to compute and display the magnitude of audio frequencies up to 2 kHz.
   - Includes real-time smoothing for better visualization.

3. **Frequency Bands**:
   - Divides the audio spectrum into three bands:
     - Bass (20 Hz - 250 Hz)
     - Mid (250 Hz - 4 kHz)
     - Treble (4 kHz - 20 kHz)
   - Displays the average magnitude of each band in dB.

---

## How It Works
1. **Audio Input**:
   - The script uses PyAudio to capture audio input in real-time from the default input device (e.g., microphone).
   - Audio data is processed in chunks of 512 samples at a sampling rate of 44.1 kHz.

2. **Signal Processing**:
   - SPL is calculated from the Root Mean Square (RMS) of the audio signal.
   - FFT is applied to extract frequency components.
   - A smoothing function is applied to the FFT output for visual clarity.

3. **Visualization**:
   - Matplotlib plots three subplots:
     - SPL bar indicator.
     - Frequency spectrum.
     - Frequency band magnitudes.

---

## Usage
To run the script:
1. Save the code to a file, e.g., `audio_visualizer.py`.
2. Run the script in a terminal or IDE:
   ```bash
   python audio_visualizer.py
   ```
3. The visualization window will open and start displaying real-time audio data.
4. Press `Ctrl+C` to stop the visualization and terminate the script.

---

## Code Details
### Main Functions
1. **`calculate_spl(inputdata)`**:
   - Calculates the Sound Pressure Level (SPL) in decibels from the audio input.

2. **`get_color(spldb)`**:
   - Maps SPL values to a range of colors for visualization.

3. **`smooth_signal(magfft, windowsize=10)`**:
   - Smooths the FFT output using a moving average filter.

4. **`visualisation()`**:
   - Main loop for capturing audio, processing data, and updating the visualization.

### Key Components
- **PyAudio**:
   - Handles real-time audio capture.
   - Configured to use 16-bit audio with a single channel (mono).

- **Matplotlib**:
   - Used for rendering the visualizations.
   - Subplots handle different components (SPL, FFT, and frequency bands).

---

## Notes
- Ensure your microphone or audio input device is working properly.
- High CPU usage may occur due to real-time processing and rendering.
- Adjust the `chunk` size, `rate`, or `plt.pause()` duration if you experience performance issues.

---

## License
This script is open-source and can be freely used and modified for personal or educational purposes.

---

## Troubleshooting
1. **Audio Input Not Detected**:
   - Verify that your microphone is enabled and set as the default input device.

2. **High CPU Usage**:
   - Reduce the `chunk` size or increase the `plt.pause()` interval.

3. **Module Not Found Errors**:
   - Ensure all dependencies are installed correctly using pip.

---

## Example
The visualization:


