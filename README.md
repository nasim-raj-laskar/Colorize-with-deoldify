# Colourizer-v2

A deep learning project for colorizing black and white images using DeOldify, designed to run in Google Colab.

## Overview

This project leverages the DeOldify neural network to automatically add realistic colors to grayscale images. DeOldify is a state-of-the-art deep learning model that uses GANs (Generative Adversarial Networks) to produce high-quality colorized images.

## Features

- Automatic colorization of black and white images
- Uses pre-trained DeOldify artistic model
- Flask web interface with CORS support
- Optimized for Google Colab environment

## Requirements

- Python 3.7+
- PyTorch 2.0.1
- TorchVision 0.15.2
- NumPy 1.24.4
- Flask
- Flask-CORS
- pyngrok

## Installation & Setup

### Google Colab (Recommended)

1. Open the `main.ipynb` notebook in Google Colab
2. Run the dependency installation cells to:
   - Clone the DeOldify repository
   - Install required packages
   - Download the pre-trained ColorizeArtistic model

### Local Setup

```bash
# Clone DeOldify
git clone https://github.com/jantic/DeOldify.git
cd DeOldify

# Install dependencies
pip install -r requirements-colab.txt
pip install flask flask-cors pyngrok
pip install torch==2.0.1 torchvision==0.15.2
pip install numpy==1.24.4

# Download pre-trained model
mkdir models
wget https://data.deepai.org/deoldify/ColorizeArtistic_gen.pth -O ./models/ColorizeArtistic_gen.pth
```

## Usage

1. **Initialize the colorizer:**
   ```python
   from deoldify import device
   from deoldify.device_id import DeviceId
   device.set(device=DeviceId.GPU0)
   from deoldify.visualize import get_image_colorizer
   colorizer = get_image_colorizer(artistic=True)
   ```

2. **Colorize an image:**
   ```python
   result_path = colorizer.colorize_image(
       source_path='path/to/your/image.jpg',
       render_factor=35  # Adjust for quality vs speed
   )
   ```

## Model Information

- **Model**: ColorizeArtistic_gen.pth
- **Type**: Artistic colorization model
- **Framework**: FastAI/PyTorch
- **Input**: Grayscale images
- **Output**: RGB colorized images

## File Structure

```
Colourizer-v2/
├── main.ipynb          # Main Jupyter notebook
└── README.md          # This file
```

## Notes

- The project is optimized for GPU acceleration (CUDA)
- Compatible with Google Colab's environment
- Includes compatibility fixes for newer PyTorch versions
- Web interface support through Flask integration

## Troubleshooting

- If you encounter torch loading issues, the notebook includes a fix for the `weights_only` parameter
- Ensure proper GPU setup for optimal performance
- Use appropriate render_factor values (10-40) to balance quality and processing time

## Credits

This project is based on [DeOldify](https://github.com/jantic/DeOldify) by Jason Antic.

## License

Please refer to the original DeOldify license for usage terms.