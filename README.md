# Microplastic Detection with YOLO

Detects microplastic particles in images, for the camera on my Autonomous Underwater Vehicle. The model is meant to run on the AUV's Raspberry Pi 4.

The notebook (written for Kaggle) does the following:

1. **Downloads every open microplastic dataset** listed from Roboflow Universe.
2. **Unifies class names** by keyword, either as one `microplastic` class or by shape (fiber, fragment, pellet, film). Non-plastic classes (dirt, sand, organic) are kept as negative images so the model learns what not to detect.
3. **Removes duplicates across datasets** with perceptual hashing plus pixel correlation, so augmented copies of one image can't land in both train and test.
4. Splits per source and **adds underwater-style training copies**.
5. **Trains YOLO** and evaluates it on a held-out test set, overall, per class, per source dataset, and at the Pi's input size.
6. **Exports to ONNX and NCNN** for the Raspberry Pi 4.
7. Optional **generalisation check:** retrains without one whole dataset and tests on it, which gives a more realistic preview of performance with a new camera.

## Run

1. Open `microplastic_detection.ipynb` on Kaggle with a GPU.
2. Add your Roboflow key as a Kaggle secret named `ROBOFLOW_API_KEY`. Never paste the key into the notebook.
3. Run all cells.

> **Status:** pipeline complete; test-set results will be added after the full training run.

**Author:** Tejas Jadhav, B.Tech Mechatronics, Symbiosis Skills and Professional University, Pune
