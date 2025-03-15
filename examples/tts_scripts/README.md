# TTS Example Scripts

This directory contains example scripts demonstrating how to use the TTS (Text-to-Speech) system.

## Available Scripts

1. `simple_tts.py` - The simplest way to use TTS with minimal setup
2. `quick_tts.py` - Command-line interface for quick text-to-speech conversion
3. `interactive_tts.py` - Interactive script with speaker selection and multi-line text input
4. `example_tts.py` - Basic example showing TTS functionality

## Usage

### Simple TTS
```bash
python simple_tts.py
```
This will convert the default text to speech using speaker p335.

### Quick TTS
```bash
python quick_tts.py "Your text goes here"
```
Converts command-line text to speech immediately.

### Interactive TTS
```bash
python interactive_tts.py
```
Provides an interactive interface where you can:
1. Choose from available speakers
2. Enter multi-line text
3. Generate speech with custom output filenames

## Output
All scripts generate WAV files that can be played with any media player.
- `simple_tts.py` generates `speech_[speaker_id].wav`
- `quick_tts.py` generates `speech_output.wav`
- `interactive_tts.py` generates `speech_output_[number].wav`

## Requirements
- Python 3.9+
- TTS library
- espeak-ng (required for phonemization)

## Installation

### 1. Python Environment Setup
```bash
# Create a virtual environment
python -m venv venv

# Activate virtual environment
# On Windows
venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate

# Upgrade pip
python -m pip install --upgrade pip
```

### 2. Install Dependencies
```bash
# Install TTS library
pip install TTS

# Install system dependencies
# For macOS
brew install espeak-ng

# For Ubuntu/Debian
sudo apt-get install espeak-ng
```

## Examples

### Basic Text-to-Speech
```python
from TTS.api import TTS

# Initialize TTS
tts = TTS(model_name="tts_models/en/vctk/vits")

# Simple conversion
tts.tts_to_file(text="Hello, world!", file_path="output.wav", speaker="p335")
```

### Multi-line Text
```python
text = """
This is a multi-line text example.
It will be converted to speech with proper pauses.
You can use it for longer content like articles or books.
"""
```

### Different Speakers
```python
# List available speakers
tts = TTS(model_name="tts_models/en/vctk/vits")
print("Available speakers:", tts.speakers)

# Try different speakers
tts.tts_to_file(text="Same text, different voice.", file_path="speaker1.wav", speaker="p227")
tts.tts_to_file(text="Same text, different voice.", file_path="speaker2.wav", speaker="p228")
```

## Configuration

### Model Options
- Model Name: `tts_models/en/vctk/vits`
- Sample Rate: 22050 Hz
- Speaker IDs: p225-p376 available
- Language: English

### Audio Settings
```python
# Available audio settings
settings = {
    "sample_rate": 22050,      # Audio sample rate
    "output_format": "wav",    # Output format (wav, mp3)
    "speed": 1.0,             # Speech speed (0.5-2.0)
}
```

### Performance Tips
1. **Memory Usage**
   - Batch processing for multiple files
   - Clear cache between large generations
   - Monitor system resources

2. **Speed Optimization**
   - Use CPU for small tasks
   - Enable GPU for batch processing
   - Cache model for repeated use

## Development

### Setting up Development Environment
```bash
# Clone the repository
git clone <repository-url>
cd TTS

# Create development environment
python -m venv venv
source venv/bin/activate  # or `venv\Scripts\activate` on Windows

# Install development dependencies
pip install -r requirements.dev.txt
```

### Running Tests
```bash
# Run all tests
python -m pytest tests/

# Run specific test file
python -m pytest tests/test_specific.py
```

### Contributing
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests
5. Submit pull request

## Supported Languages
The current model (`tts_models/en/vctk/vits`) supports English with multiple speakers.
Each speaker has a unique voice characteristic. The available speakers can be viewed
when running the interactive script.

## Troubleshooting

### Common Issues

1. **No audio output file generated**
   - Check if you have write permissions in the current directory
   - Ensure enough disk space is available
   - Verify that the text input is not empty

2. **espeak-ng not found**
   - Make sure espeak-ng is installed correctly
   - For macOS: `brew install espeak-ng`
   - For Ubuntu/Debian: `sudo apt-get install espeak-ng`
   - Add espeak-ng to your system PATH if needed

3. **Speaker not found error**
   - Use the interactive script to see available speaker IDs
   - Default speaker is "p335"
   - Make sure to use exact speaker ID (case sensitive)

4. **Model download issues**
   - Check your internet connection
   - Ensure you have enough disk space
   - Try removing the downloaded model and let it re-download

5. **Memory errors**
   - Try with shorter text inputs
   - Close other memory-intensive applications
   - Check if your system meets minimum requirements

### Advanced Usage

1. **Custom Output Location**
   - All scripts support custom output paths
   - Use absolute paths for reliable file saving
   - Ensure write permissions in target directory

2. **Voice Customization**
   - Try different speakers for variety
   - Use interactive mode to preview voices
   - Experiment with different text formats

### Getting Help
If you encounter issues not covered here:
1. Check the error message for specific details
2. Verify your Python environment and dependencies
3. Try running the example scripts with simple inputs first
4. Check the TTS library documentation for advanced issues 