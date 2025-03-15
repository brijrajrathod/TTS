# 🐸 Coqui TTS - Advanced Text-to-Speech Toolkit
<div align="center">
<img src="https://raw.githubusercontent.com/coqui-ai/TTS/main/images/coqui-log-green-TTS.png" height="56"/>

**A comprehensive library for advanced Text-to-Speech generation**

[![Discord](https://img.shields.io/discord/1037326658807533628?color=%239B59B6&label=chat%20on%20discord)](https://discord.gg/5eXr5seRrv)
[![License](<https://img.shields.io/badge/License-MPL%202.0-brightgreen.svg>)](https://opensource.org/licenses/MPL-2.0)
[![PyPI version](https://badge.fury.io/py/TTS.svg)](https://badge.fury.io/py/TTS)
[![Downloads](https://pepy.tech/badge/tts)](https://pepy.tech/project/tts)
[![DOI](https://zenodo.org/badge/265612440.svg)](https://zenodo.org/badge/latestdoi/265612440)
</div>

## 📑 Table of Contents
- [Latest Updates](#-latest-updates)
- [Quick Start](#-quick-start)
- [Features](#-features)
- [Installation](#-installation)
- [Basic Usage](#-basic-usage)
- [Available Models](#-available-models)
- [Advanced Usage](#-advanced-usage)
- [Performance Optimization](#-performance-optimization)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [Community & Support](#-community--support)
- [Security](#-security)
- [Citation](#-citation)

## 🔥 Latest Updates
- 📣 ⓍTTSv2 released with 16 languages and improved performance
- 📣 ⓍTTS fine-tuning code available
- 📣 ⓍTTS now supports streaming with <200ms latency
- 📣 Support for ~1100 Fairseq models
- 📣 Integration with 🐶Bark and 🐢Tortoise
[View all updates](https://github.com/coqui-ai/TTS/releases)

## 🚀 Quick Start

```bash
# Install TTS
pip install TTS

# Quick text-to-speech generation
python -c "from TTS.api import TTS; tts = TTS('tts_models/multilingual/multi-dataset/xtts_v2'); tts.tts_to_file(text='Hello, this is a test!', file_path='output.wav')"
```

## ✨ Features
- 🌟 High-performance Deep Learning models
- 🌍 Support for 1100+ languages
- 🎯 Production-ready performance
- 🔧 Easy-to-use API
- 📚 Comprehensive documentation
- 🛠️ Flexible training pipeline

## 💻 Installation

### Requirements
- Python >= 3.9, < 3.12
- Operating Systems: Ubuntu 18.04+ (Primary), Windows, macOS
- GPU (Optional but recommended for training)

### Basic Installation
```bash
pip install TTS
```

### Development Installation
```bash
git clone https://github.com/coqui-ai/TTS
pip install -e .[all,dev,notebooks]
```

### Docker Installation
```bash
docker run --rm -it -p 5002:5002 ghcr.io/coqui-ai/tts-cpu
```

[Detailed Installation Guide](https://tts.readthedocs.io/en/latest/installation.html)

## 📖 Basic Usage

### Simple Text-to-Speech
```python
from TTS.api import TTS

# Initialize TTS
tts = TTS("tts_models/en/ljspeech/tacotron2-DDC")

# Generate speech
tts.tts_to_file("Hello world!", file_path="output.wav")
```

### Multi-lingual Voice Cloning
```python
tts = TTS("tts_models/multilingual/multi-dataset/xtts_v2")
tts.tts_to_file(
    text="Hello world!",
    speaker_wav="path/to/speaker.wav",
    language="en",
    file_path="output.wav"
)
```

## 🎯 Available Models

### Text-to-Speech Models
| Model | Languages | Speed | Quality | GPU Memory |
|-------|-----------|-------|---------|------------|
| ⓍTTS v2 | 16 | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 4GB+ |
| YourTTS | 13 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 2GB+ |
| Tacotron 2 | Any | ⭐⭐ | ⭐⭐⭐ | 1GB+ |
| FastSpeech 2 | Any | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | 1GB+ |

[Complete Model List](https://tts.readthedocs.io/en/latest/models.html)

## 🚄 Performance Optimization

### Hardware Requirements
- Training: NVIDIA GPU with 8GB+ VRAM recommended
- Inference: CPU or GPU (2GB+ VRAM)
- RAM: 8GB minimum, 16GB recommended

### Optimization Tips
- Use batch processing for multiple inputs
- Enable GPU acceleration when available
- Implement caching for repeated phrases
- Use quantized models for faster inference

## 🌐 Deployment

### Production Setup
1. Load models during initialization
2. Implement proper error handling
3. Set up monitoring and logging
4. Use appropriate scaling strategies

### Docker Deployment
```bash
docker run -d --gpus all -p 5002:5002 ghcr.io/coqui-ai/tts-gpu
```

## 🛠 Contributing

### Development Setup
1. Fork the repository
2. Set up development environment
3. Run tests: `pytest tests/`
4. Submit PR with detailed description

[Contributing Guidelines](CONTRIBUTING.md)

## 🤝 Community & Support

### Get Help
- [Discord Community](https://discord.gg/5eXr5seRrv)
- [GitHub Discussions](https://github.com/coqui-ai/TTS/discussions)
- [Documentation](https://tts.readthedocs.io/)

### Commercial Support
- [Contact Coqui](https://coqui.ai/contact)

## 🔒 Security

### Best Practices
- Keep models and dependencies updated
- Use environment variables for sensitive data
- Implement proper API authentication
- Monitor for unusual usage patterns

[Security Policy](SECURITY.md)

## 📚 Citation

```bibtex
@misc{coqui-ai-tts,
  author = {Eren Gölge and others},
  title = {🐸TTS - a deep learning toolkit for Text-to-Speech},
  year = {2021},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/coqui-ai/TTS}},
}
```

## 📊 Performance Benchmarks

<p align="center"><img src="https://raw.githubusercontent.com/coqui-ai/TTS/main/images/TTS-performance.png" width="800" /></p>

## 🌍 Language Support
- 16 primary languages with ⓍTTS v2
- 1100+ languages via Fairseq models
- Support for custom language training

[Language Documentation](https://tts.readthedocs.io/en/latest/languages.html)

## 📁 Directory Structure
```
|- notebooks/       # Jupyter Notebooks for examples
|- TTS/
    |- bin/        # Training scripts
    |- tts/        # Core TTS models
    |- vocoder/    # Vocoder models
    |- utils/      # Utilities
```

For more detailed information, visit our [Documentation](https://tts.readthedocs.io/).
