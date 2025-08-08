# **Camouflaged Object Detection & Instance Segmentation on MHCD Dataset**

<p align="center">
  <img src="assets/demo_result.jpg" width="800"/>
</p>

---

## **About the Project**

This repository presents my undergraduate research at the **Computer Vision Lab (CVLab)**, **Iran University of Science and Technology (IUST)**, focusing on **Camouflaged Object Detection (COD)** and **Camouflaged Instance Segmentation (CIS)**.

Camouflaged objects, blending into their surroundings, challenge both human perception and computer vision systems. Inspired by recent advances in deep learning and informed by recent literature, I applied and evaluated **YOLOv8** models for both detection and segmentation on a **custom-cleaned MHCD dataset** that I built from scratch.

---

## **Key Contributions**

* **Dataset Curation & Cleaning**

  * Processed the **Military Camouflage HD (MHCD2022)** dataset into a **noise-free, class-balanced version**.
  * Fixed mislabeled samples, removed duplicates, standardized image resolutions.
  * Created consistent **training / validation splits** and uploaded to <a href="https://universe.roboflow.com/forground/cod-mhcd-camouflaged-object-detection-dataset-curated-czv10">
    <img src="https://app.roboflow.com/images/download-dataset-badge.svg"></img>
</a>) for reproducible annotation management.

* **Dual-Task Implementation**

  * **Object Detection** (Bounding Boxes) using YOLOv8n/s/m/l/x variants.
  * **Instance Segmentation** (Masks) using YOLOv8n/s/m/l/x-Seg variants.

* **Experimental Depth**

  * 20+ experiments, varying image size, patience, optimizer, and validation selection strategies.
  * Thorough logging of all hyperparameters, metrics, and model versions.

* **Reproducibility & Transparency**

  * Public dataset, weight files, and Google Colab notebooks for each run.
  * Full training history in structured format for future analysis.

---

## **Dataset Overview**

**Classes:**

* Person
* Tank
* Aeroplane
* Military Vehicle
* Warship

**Folder Structure:**

```
data/
  ├── images/train
  ├── images/val
  ├── labels/train
  └── labels/val
```

**Download:**

* [Clean MHCD Dataset (ZIP)]([link-to-dataset](https://drive.google.com/file/d/1b60qEyZOV3oc1DWZf20CfyWnr_pRASIz/view?usp=sharing))
* Original MHCD2022: `Military-Camouflage-MHCD2022.zip`

---

## **Object Detection Results (Bounding Boxes)**

| Dataset               | Model   | Precision | Recall    | mAP50     | mAP50-95  | Weights                                        |
| --------------------- | ------- | --------- | --------- | --------- | --------- | ---------------------------------------------- |
| Old MHCD              | YOLOv8l | 67.2%     | 40.6%     | 45.5%     | 24.2%     | [Download](weights/detect_20240812_133435.zip) |
| Old MHCD              | YOLOv8x | 61.2%     | 42.9%     | 48.9%     | 27.3%     | [Download](weights/detect_20240812_004026.zip) |
| Clean MHCD (No Valid) | YOLOv8l | **68.1%** | **51.3%** | **59.7%** | **37.7%** | [Download](weights/detect_20240908_020947.zip) |
| Clean MHCD (Valid)    | YOLOv8m | 70.8%     | 44.7%     | 51.8%     | 31.9%     | [Download](weights/detect_20240910_220054.zip) |
| Clean MHCD (Valid)    | YOLOv8s | 66.7%     | 48.3%     | 54.7%     | 32.3%     | [Download](weights/detect_20240912_201230.zip) |

---

## **Instance Segmentation Results (Masks)**

| Dataset    | Model       | Box P     | Box R     | Box mAP50 | Box mAP50-95 | Mask P    | Mask R    | Mask mAP50 | Mask mAP50-95 | Weights                                                                                      |
| ---------- | ----------- | --------- | --------- | --------- | ------------ | --------- | --------- | ---------- | ------------- | -------------------------------------------------------------------------------------------- |
| Clean MHCD | YOLOv8n-Seg | **68.7%** | **56.2%** | **61.1%** | **37.2%**    | **68.6%** | 54.3%     | **59.8%**  | **33.8%**     | [Download](https://drive.google.com/uc?id=1xY586IhHUWY0Y4Kd2pF782FAJiy6STU4&export=download) |
| Clean MHCD | YOLOv8m-Seg | 61.4%     | 55.8%     | 55.6%     | 32.7%        | 60.5%     | 52%       | 51.2%      | 28.1%         | [Download](https://drive.google.com/uc?id=14O_hI32kLAKjobbKTd3mGQ3EvTL_yglu&export=download) |
| Clean MHCD | YOLOv8s-Seg | 57.1%     | 46.6%     | 49.1%     | 29.7%        | 55.6%     | 45.2%     | 47.4%      | 26%           | [Download](https://drive.google.com/uc?id=1smmcUl7qHCknSCD8jl7MqJiOpUCGewOH&export=download) |
| Clean MHCD | YOLOv8l-Seg | 53.6%     | 51.4%     | 51.4%     | 32%          | 51.5%     | 49.9%     | 48.7%      | 27.6%         | [Download](https://drive.google.com/uc?id=1IDknTmrWKuuTG-hQd07TKOz6hqUWiIZr&export=download) |
| Clean MHCD | YOLOv8x-Seg | 55.2%     | **56.8%** | 53.9%     | 34.4%        | 53.8%     | **54.2%** | 51.5%      | 31.1%         | [Download](https://drive.google.com/uc?id=1u_ZYhg0cWLJOPjh_1bItOyqlYy5W8K1g&export=download) |

---

## **Example Outputs**

<p align="center">
  <img src="assets/detection_example.jpg" width="400"/>
  <img src="assets/segmentation_example.jpg" width="400"/>
</p>

---

## **Training & Evaluation**

* All models trained on **Google Colab Pro**
* Mixed precision training for efficiency
* Early stopping patience: 10–15 epochs depending on run
* Logged metrics: Precision, Recall, mAP50, mAP50-95 for both train, valid, and test sets

Training scripts and configs are available in:

* [`colabs/`](colabs/) → Colab notebooks for each run
* [`weights/`](weights/) → trained weights in `.pt` format

---

## **References**

1. **Yong Liang, et al.** *A systematic review of image-level camouflaged object detection with deep learning*. Neurocomputing, 2024.
2. **Thanh Nguyen Le, et al.** *Camouflaged Instance Segmentation: Dataset and Benchmark Suite (CAMO++)*, ICCV 2021.

---

## **Contact**

**Amir Hossein Eslami**

* Email: [amirhosseineslami@example.com](mailto:amirhossein.eslami.ac@gmail.com)
* GitHub: [amirhosseineslami](https://github.com/amirhosseineslami)
* LinkedIn: [amir-hossein-eslami](https://linkedin.com/in/amir-hossein-eslami)

