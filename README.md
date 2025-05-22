# Medieval Weapon Detection

This project uses the YOLO (You Only Look Once) model to detect melee weapons in images. The model is trained to identify objects such as swords and sticks, and the provided Jupyter notebook demonstrates how to run inference using a pre-trained model.

## Table of Contents
- [Project Overview](#project-overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [File Structure](#file-structure)
- [Model Details](#model-details)
- [Notes](#notes)
- [Contributing](#contributing)
- [License](#license)

## Project Overview
The goal of this project is to detect melee weapons in images using a YOLO-based object detection model. The provided notebook (`run.ipynb`) loads a pre-trained model and performs inference on a specified image, saving the results with bounding boxes.

## Requirements
- Python 3.10+
- PyTorch
- Ultralytics YOLO
- Jupyter Notebook

## Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/CallMeGovos/WeaponDetection.git
   cd WeaponDetection
   ```

2. **Create a virtual environment and activate it**:
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: env\Scripts\activate
   ```

3. **Install the required packages**:
   ```bash
   pip install torch ultralytics jupyter
   ```

## Training the Model
The model was trained using the following command:
```bash
yolo task=detect mode=train model=yolo11s.pt data=data/weapon2.v2i.yolov12/data.yaml epochs=50 batch=16 name=sword_yolo11n
```
- Model: Pre-trained YOLO11s (yolo11s.pt)
- Dataset: Custom dataset specified in data/weapon2.v2i.yolov12/data.yaml
- Epochs: 50
- Batch Size: 16
- Output: Trained model saved as best.pt in runs/detect/sword_yolo11n/weights/
To train your own model, prepare a dataset in YOLO format and run the above command with your dataset configuration.

## Usage
1. **Ensure you have a pre-trained model file (e.g., `best.pt`) in the specified path (e.g., `G:\Project\Medival_detector\runs\detect\sword_yolo11s\weights\best.pt`)**.
2. **Update the `source` variable in `run.ipynb` with the path to your input image**.
3. **Run the Jupyter notebook**:
   ```bash
   jupyter notebook run.ipynb
   ```
4. **The model will process the input image, detect melee weapons, and save the results with bounding boxes in the `runs/detect/predict*` directory**.

Example code snippet from `run.ipynb`:
```python
model = YOLO(model_path)
results = model(source=source, conf=0.25, save=True)
```

## File Structure
```
medieval-weapon-detection/
├── runs/detect/sword_yolo11s/weights/best.pt
├── notebooks/run.ipynb
├── README.md
├── LICENSE
```

- `runs/detect/sword_yolo11s/weights/best.pt`: Pre-trained YOLO model weights.
- `notebooks/run.ipynb`: Jupyter notebook for running inference.
- `README.md`: Project documentation.
- `LICENSE`: MIT License file.

## Model Details
- **Model**: YOLO (version: yolo11s)
- **Classes**: Trained to detect melee weapons (e.g., sticks, swords)
- **Confidence Threshold**: 0.25 (adjustable in `run.ipynb`)
- **Inference Speed**: ~137.9ms per image (on 416x640 resolution)

## Notes
- The pre-trained model (`best.pt`) and dataset are not included in this repository due to licensing restrictions.
- This project uses the Ultralytics YOLO framework, which is licensed under AGPL-3.0. Ensure compliance with its license terms when using the model.

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.