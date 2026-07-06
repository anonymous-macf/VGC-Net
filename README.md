# VGC-Net

## 0. Abstract

In X-ray coronary angiography (XCA), accurate coronary artery segmentation is crucial for quantitative vascular analysis, stenosis assessment, and computer-aided diagnosis. However, XCA segmentation remains challenging due to weak vessel contrast caused by complex anatomical structures and segmentation instability caused by large diameter variations and blurred boundaries. To address these issues, this paper proposes a vascular evidence and geometric calibration network for XCA coronary artery segmentation named VGC-Net. First, we proposed a gray-scale vessel evidence decomposition (GVED) module, which utilizes complementary gray-scale structural cues to enhance weak coronary artery evidence at the input end, thereby reducing interference from ribs, catheters, and uneven backgrounds. Second, a radius-aware boundary calibration (RBC) module is designed to jointly model vessel regions, radius maps, and boundary maps, where geometry-supervised radius and boundary cues are fed back to calibrate fragmented distal branches and ambiguous vessel edges. Experiments on a self-built dataset (CS2026) and two public datasets (DCA1, XCAD) demonstrate that VGC-Net significantly improves segmentation performance. Compared to state-of-the-art methods, the VGC-Net model achieves improvements of at least 2.48\%, 1.8\%, and 2.06\% on Dice, respectively. 

## 1. Overview

<div align="center">
<img src="figures/vgcnet_framework.png" width="900" />
</div>

## 2. Main Environments

The environment installation process can be carried out as follows:

```bash
# Core Framework
Python: 3.9.23
torch==1.13.0+cu117 --extra-index-url https://download.pytorch.org/whl/cu117
torchvision==0.14.0+cu117 --extra-index-url https://download.pytorch.org/whl/cu117

# Data Processing & Augmentation
numpy==1.26.4
opencv-python==4.12.0
albumentations==2.0.12
Pillow==11.3.0

# Scientific & Tools
scikit-learn==1.0.2
scipy==1.13.1
matplotlib==3.9.4
tqdm==4.67.1
```

## 3. Datasets

Please organize the dataset into the following format:

```text
./data/
|-- images/
|   |-- 1.png
|   |-- 2.png
|   `-- ...
|-- masks/
|   |-- 1.png
|   |-- 2.png
|   `-- ...
|-- train.txt
|-- val.txt
`-- test/
    |-- images/
    |   |-- 1.png
    |   |-- 2.png
    |   `-- ...
    `-- masks/
        |-- 1.png
        |-- 2.png
        `-- ...
```


## 4. Train the VGC-Net

```bash
python main.py 

```

## 5. Test the VGC-Net

```bash
python evaluate.py 
```

The segmentation masks, visualization results, and metric file will be saved in
the results directory.


