# Speaker Diarization & Transcription

This project implements speaker diarization and now includes a Command-Line Interface (CLI) for fast transcriptions using [insanely-fast-whisper](https://github.com/your-repo-link). The diarization module partitions an audio stream into segments based on speaker identity, while the CLI enables rapid transcription.

## Features

- **Speaker Diarization:**  
  Partitioning audio into segments based on speaker identity using audio preprocessing, feature extraction, and clustering.
- **Noise Reduction**:
Integrated noise reduction techniques are applied during audio preprocessing to enhance the clarity of the features extracted from the audio.
## Prerequisites

Before running the project, ensure you have the following installed:

- **Python 3.x**  
### Required Python Packages

Install the required packages using pip:

```bash
pip install numpy scipy matplotlib librosa scikit-learn moviepy
```

*For the CLI transcription feature, follow the installation instructions below.*

## Installation and Setup

### CLI Installation

To use the CLI for fast transcriptions, install insanely-fast-whisper using [pipx](https://pypi.org/project/pipx/):

1. **Install pipx (if not already installed):**

   ```bash
   pip install pipx
   ```

   or on macOS using Homebrew:

   ```bash
   brew install pipx
   ```

2. **Install insanely-fast-whisper via pipx:**

   ```bash
   pipx install insanely-fast-whisper
   ```

   ⚠️ **Note:**  
   If you have Python 3.11.XX installed, pipx may misinterpret the version and install an old version of insanely-fast-whisper (version 0.0.8) that won't work with the current BetterTransformers. In that case, install the latest version by running:

   ```bash
   pipx install insanely-fast-whisper --force --pip-args="--ignore-requires-python"
   ```

   If you're installing with pip directly, you can pass the argument like so:

   ```bash
   pip install insanely-fast-whisper --ignore-requires-python
   ```

## Troubleshooting

### Torch CUDA Error on Windows

If you encounter the following error:

```
AssertionError: Torch not compiled with CUDA enabled
```

on Windows, you can resolve it by manually installing the correct version of torch in your virtual environment. Run the following command:

```bash
python -m pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
```

This command installs torch with CUDA support. Thanks to [@pto2k](https://github.com/pto2k) for the debugging help.

