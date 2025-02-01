# JK-Lakshmi_codetrio
MINED HACKATHON 2025


# Wagon Damage Detection, Depth Estimation, and Clinker Volume Calculation

## Overview
This project utilizes computer vision and deep learning techniques to analyze rail wagon images, detect damages, estimate depth, classify severity, and compute clinker volume. The system processes images and video frames, labels wagons, estimates depth differences, calculates material volume, and generates a detailed PDF report.

## Features
- Detects and labels wagons in an image.
- Classifies damage size into "Small Damage" or "Big Damage."
- Generates a detailed PDF report with labeled images and damage statistics.
- Uses MiDaS for monocular depth estimation to calculate clinker volume.
- Computes the difference between empty and filled wagon depth maps for weight estimation.
- Utilizes OpenCV for image processing and FPDF for report generation.

## Prerequisites
Before running the scripts, ensure you have the following dependencies installed:

bash
pip install torch torchvision opencv-python numpy matplotlib fpdf


## Usage

1. Place the input images and video frames in the specified directory.
2. Update the image_path, video_path, and output_path variables in the scripts.
3. Run the Python scripts:

bash
python wagon_damage_detection.py
python depth_estimation.py


4. The scripts will process the inputs and generate:
   - A labeled image with bounding boxes around detected wagons and damage classification.
   - A wagon_damage_report.pdf in the output directory.
   - Precomputed depth maps for empty and filled wagons.
   - Volume and weight estimation based on clinker density.

## File Structure

|-- wagon_damage_detection.py  # Damage detection script
|-- depth_estimation.py        # Depth estimation and volume calculation
|-- input/                     # Folder containing input images and videos
|-- output/                    # Folder to save labeled images, reports, and depth maps
|-- empty_wagon_depth.npy      # Precomputed depth map for an empty wagon
|-- filled_wagon_depth.npy     # Precomputed depth map for a filled wagon
|-- README.md                   # Project documentation


## Output Example
After running the scripts, the output folder will contain:
- frame_10175_labeled.jpg (Labeled wagon image)
- wagon_damage_report.pdf (PDF report with analysis)
- empty_wagon_depth.npy and filled_wagon_depth.npy (Depth maps for volume estimation)

## How It Works
1. The system loads the MiDaS depth estimation model.
2. It processes input video frames by resizing and normalizing them.
3. Depth maps are computed for empty and filled wagons.
4. The difference in depth is used to calculate the volume of the stored clinker.
5. The computed volume is converted into mass based on clinker density.
6. Results are visualized using matplotlib.

## Notes
- The damage detection model should be trained separately and loaded into the script.
- The threshold values for damage classification and clinker density can be adjusted based on specific use cases.
- The script assumes a known wagon length, width, and height.
- If CUDA is available, the script will automatically utilize GPU acceleration.

## License
This project is open-source and can be modified as needed.
