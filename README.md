# AI Image Generator with Custom .agi Format

A full-stack AI image generator that creates images using Stable Diffusion and packages them in a proprietary `.agi` format with embedded metadata for complete provenance tracking.

## Features

- **Stable Diffusion Integration**: Generate high-quality images from text prompts using Hugging Face API
- **Proprietary .agi Format**: Custom binary format that embeds generation metadata directly into image files
- **Complete Provenance Tracking**: Every generated image contains its full generation history including:
  - Original prompts
  - Timestamps
  - Model parameters
  - Generation settings
- **Magic Number Identification**: Uses `0x41474646` header for reliable file type detection
- **Lossless Metadata**: Base64 encoding ensures metadata integrity alongside PNG image data

## Why .agi Format?

The `.agi` format makes AI-generated images easily distinguishable from real images by giving them a unique identity. The embedded metadata allows for:
- Verification of image authenticity
- Complete generation history
- Easy validation and tracking
- Transparent AI content identification

## Tech Stack

- **Backend**: Python, Flask
- **Frontend**: JavaScript
- **AI Model**: Stable Diffusion (via Hugging Face API)
- **File Format**: Custom binary format with structured packaging (PNG + JSON metadata)

## How It Works

1. User submits a text prompt through the web interface
2. Backend sends request to Stable Diffusion via Hugging Face API
3. Generated image is packaged with metadata into `.agi` format
4. File structure: Magic number + PNG data + Base64-encoded JSON metadata
5. Users can extract and verify metadata from `.agi` files at any time

## Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/ai-image-generator.git
cd ai-image-generator

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
export HUGGINGFACE_API_KEY=your_api_key_here

# Run the application
python app.py
```

## Usage

1. Open your browser and navigate to `http://localhost:5000`
2. Enter your image prompt
3. Adjust generation parameters (optional)
4. Click generate
5. Download your image in `.agi` format with embedded metadata

## File Format Specification
```
[Magic Number: 4 bytes] 0x41474646
[PNG Image Data: variable length]
[Metadata Separator: 4 bytes]
[Base64 JSON Metadata: variable length]
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - feel free to use this project for your own purposes.

---

**Note**: This project demonstrates a novel approach to AI image provenance and transparency. The `.agi` format provides a foundation for tracking and verifying AI-generated content.
