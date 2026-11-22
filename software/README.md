# Software

Perception and control code for the Leaf Compost Collector, written by **Lynn Ong**.

Copied from [lynnlo/leaf-detector](https://github.com/lynnlo/leaf-detector) at commit `848fb54` (Nov 8, 2026). Check the original repository for later updates.

## Scripts

| Script | What it does |
|---|---|
| `pickup.py` | Full autonomy: detect a leaf, drive to it, run the rake roller |
| `capture.py` | Detect-and-steer loop for the drivetrain only |
| `teleop.py` | Drive from a browser (WASD, arrow keys, or on-screen joystick) with a deadman stop |
| `webstream.py` | Live camera feed with detection boxes, viewable in a browser on port 8000 |
| `drive.py` | L298N motor driver class and interactive motor test |
| `leaf_detector.py` | Detector: hosted Roboflow workflow, or a local YOLO model through ONNX Runtime |
| `train_and_export.py` | Train YOLO11n on the leaf dataset and export it for the Pi |
| `export_for_pi.py` | Convert trained weights to ONNX or NCNN for the Pi |
| `stream.py`, `webvideo.py` | Camera streaming helpers |
| `pinout.html` | Raspberry Pi GPIO wiring reference |
| `runs/leaf/results.csv` | Training metrics per epoch |

Motors only move when `--drive` is passed.

## Run on the Raspberry Pi

```bash
sudo apt update
sudo apt install -y python3-opencv python3-picamera2 python3-gpiozero python3-numpy
cd software
python3 -m venv --system-site-packages ~/leafvenv && source ~/leafvenv/bin/activate
pip install -r requirements-pi.txt

export ROBOFLOW_API_KEY=your_key_here   # for the hosted detector
python pickup.py            # dry run: prints commands, motors stay still
python pickup.py --drive    # drive and sweep
```

To use a local model instead of the hosted one, train and export it on a GPU machine with `requirements-train.txt` and `train_and_export.py`, copy `models/leaf.onnx` to the Pi, and run `python pickup.py --backend onnx`.
