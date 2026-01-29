# Context-Aware CCTV Surveillance System

AI-powered CCTV monitor using Qwen2-VL vision language model to detect suspicious activities.

## Features
- Analyzes 3-second video clips with multi-frame context
- Detects: robbery, assault, weapons, accidents, fire/smoke, vandalism, forced entry
- Mentions useful events: people entering, stray animals, deliveries
- Generates detailed logs with timestamps

## Requirements
- Windows 10/11
- NVIDIA GPU with 6GB+ VRAM (RTX 3060 or better)
- Python 3.11 (64-bit)

## Quick Setup

### 1. Install Python 3.11
Download from [python.org](https://www.python.org/downloads/) - **check "Add to PATH"**

### 2. Clone this repository
```powershell
git clone https://github.com/AyanMalaviya/cctv-surveillance.git
cd cctv-surveillance

### 3. Create virtual environment
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1

### 4. Install dependencies
python -m pip install -U pip
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
pip install -r requirements.txt

### 5. Download the VLM model (one-time, ~4.4GB)
$env:HF_HUB_DISABLE_XET="1"
pip install -U "huggingface_hub[cli]"
hf auth login
hf download Qwen/Qwen3-VL-2B-Instruct --local-dir "hf_models\Qwen3-VL-2B-Instruct"

### 6. configuration
VIDEO_PATH = r"path\to\your\video.mp4"        # or RTSP URL
MODEL_ID = r"hf_models\Qwen3-VL-2B-Instruct"
CLIP_DURATION_SEC = 3.0                       # analyze every N seconds
