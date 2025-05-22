Medieval Weapon Detection
This project uses the YOLO (You Only Look Once) model to detect melee weapons in images. The model is trained to identify objects such as swords and sticks, and the provided Jupyter notebook demonstrates how to run inference using a pre-trained model.
Table of Contents

Project Overview
Requirements
Installation
Usage
File Structure
Model Details
Contributing
License

Project Overview
The goal of this project is to detect melee weapons in images using a YOLO-based object detection model. The provided notebook (run.ipynb) loads a pre-trained model and performs inference on a specified image, saving the results with bounding boxes.
Requirements

Python 3.10+
PyTorch
Ultralytics YOLO
Jupyter Notebook

Installation

Clone the repository:
git clone https://github.com/CallMeGovos/WeaponDetection.git
cd WeaponDetection


Create a virtual environment and activate it:
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate


Install the required packages:
pip install torch ultralytics jupyter



Usage

Ensure you have a pre-trained model file (e.g., best.pt) in the specified path (e.g., G:\Project\Medival_detector\runs\detect\sword_yolo11s\weights\best.pt).
Update the source variable in run.ipynb with the path to your input image.
Run the Jupyter notebook:jupyter notebook run.ipynb


The model will process the input image, detect melee weapons, and save the results with bounding boxes in the runs/detect/predict* directory.

Example code snippet from run.ipynb:
model = YOLO(model_path)
results = model(source=source, conf=0.25, save=True)

File Structure
medieval-weapon-detection/
├── runs/
│   └── detect/
│       └── sword_yolo11s/
│           └── weights/
│               └── best.pt
├── notebooks/
│   └── run.ipynb
├── README.md


runs/detect/sword_yolo11s/weights/best.pt: Pre-trained YOLO model weights.
notebooks/run.ipynb: Jupyter notebook for running inference.
README.md: Project documentation.

Model Details

Model: YOLO (version: yolo11s)
Classes: Trained to detect melee weapons (e.g., sticks, swords)
Confidence Threshold: 0.25 (adjustable in run.ipynb)
Inference Speed: ~137.9ms per image (on 416x640 resolution)

Contributing
Contributions are welcome! Please follow these steps:

Fork the repository.
Create a new branch (git checkout -b feature-branch).
Commit your changes (git commit -m "Add feature").
Push to the branch (git push origin feature-branch).
Open a Pull Request.

License
This project is licensed under the MIT License. See the LICENSE file for details.
