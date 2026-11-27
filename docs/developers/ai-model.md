<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# How the AI was made

How Printer Buddy's failure-detection models were built, what they can't do yet, and the data and software they're built on. Using the AI is on [AI failure detection](../using/ai.md).

## The first model: `basic-v1`

- MobileNetV3-Large, 224 x 224 input, ONNX, runs on a CPU (about 7 ms per image on a PC; a Pi 4 is slower but fine for a check every few seconds)
- Trained on 31,934 images, tested on 2,907 held-out images
- Default alert threshold **0.6**

Test results (alert labels, per frame, before the "hold for several checks" rule):

| Threshold | Failures caught | Correct when it alarms | False alarms on frames without an alert problem |
|---|---|---|---|
| 0.5 | 92.2% | 95.7% | 4.0% |
| **0.6** | **91.5%** | **96.2%** | **3.5%** |
| 0.7 | 90.6% | 96.5% | 3.2% |
| 0.8 | 89.3% | 97.0% | 2.6% |

Newer model releases list their own test scores in the release notes under **Model check**. All models: [releases tagged `ai-`](https://github.com/printer-buddy/printer-buddy/releases?q=ai-&expanded=true).

## Limits

- The test images come from the **same kinds of sources** as the training images. On your own
  printers, cameras and lighting it **will do worse** than the table above. Tell us about misses and false alarms.
- **first_layer** looks perfect in testing but most of its images come from one dataset, so it may be
  recognising that camera rather than the defect. Don't trust it yet.
- **failure** is a vague label from datasets that only said "fail"; it scores poorly on its own.
  Real failures are usually caught by spaghetti or warping anyway.
- Clean "OK" prints are only about 11% of the data, so false alarms are the main thing we're working on.

## How it was made

1. Twelve public datasets were downloaded, their labels mapped onto ours, and duplicates removed
   (4,766 copies) to make one dataset: 34,841 images.
2. Every image was resized (max 640 px) and given image-level labels. Box sets: any box = that label.
   Folder sets: the folder name is the label. Images with no problem are "OK".
3. A MobileNetV3-Large (starting from ImageNet weights) was trained for 30 epochs in Google Colab;
   the best epoch (24) was kept and exported to ONNX.

## Credits

### Datasets

Thank you to everyone who published these. We **resized, relabelled and merged** the images;
nothing here is endorsed by the original authors.

| Dataset | Author | License | Images used |
|---|---|---|---|
| [3D printing defects](https://universe.roboflow.com/hnnm/3d-printing-defects-eavhn) | hnnm (Roboflow) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | 16,133 |
| [3D printing error](https://universe.roboflow.com/cameteam/3d-printing-error-cv8ue) | cameteam (Roboflow) | MIT | 4,274 |
| [3DPrintFail](https://universe.roboflow.com/minedorothy/3dprintfail) | minedorothy (Roboflow) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | 4,347 |
| [3D print fail detection](https://universe.roboflow.com/detection-y0hrz/3d-print-fail-detection) | detection-y0hrz (Roboflow) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | 2,058 |
| [3Dprint3](https://universe.roboflow.com/edison-jyxbh/3dprint3) | edison-jyxbh (Roboflow) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | 1,372 |
| [3d-ho5at](https://universe.roboflow.com/automatisierung-projekt-aajut/3d-ho5at) | automatisierung-projekt-aajut (Roboflow) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | 3,493 |
| [FDM defects](https://universe.roboflow.com/defects-of-3d-printing/fdm-sw9eb) | defects-of-3d-printing (Roboflow) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | 3,888 |
| [3dprinting](https://universe.roboflow.com/additive-manufacturing-qa/3dprinting) | additive-manufacturing-qa (Roboflow) | Public Domain | 692 |
| [3D printing errors](https://www.kaggle.com/datasets/mikulhe/3d-printing-errors) | mikulhe (Kaggle) | see dataset page | 388 |
| [3D printing success/failure (finetuned)](https://www.kaggle.com/datasets/bshaurya/3d-printing-success-failure-dataset-finetuned) | bshaurya (Kaggle) | see dataset page | 327 |
| [Defect 3D printing](https://www.kaggle.com/datasets/muhammadmeftahmafazy/defect-3d-printing) | muhammadmeftahmafazy (Kaggle) | see dataset page | 635 |
| [3D printing errors](https://www.kaggle.com/datasets/nimbus200/3d-printing-errors) | nimbus200 (Kaggle) | see dataset page | 2,000 (of 17,883) |

"Images used" is before duplicates were removed. Several sets share images, so the final dataset is smaller.

### Added for the next model (`basic-v2`)

| Dataset | Author | License |
|---|---|---|
| [3D FDM faults detection](https://universe.roboflow.com/wangdada/3d_fdm_faults_detection-krkkr) | wangdada (Roboflow) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) |
| [3Dprinting](https://universe.roboflow.com/hnnm/3dprinting-32nsa) | hnnm (Roboflow) | Public Domain |
| [KS1 full dataset](https://github.com/mann1x/anycubic/releases/tag/datasets%2Fks1-full) | mann1x (Anycubic Kobra S1 camera, from BigEdge-FDM-Models) | none stated - credited here; ask the author before a model trained on it is released |

Plus photos shared by Printer Buddy users through **Help improve the AI**.

### Ideas

- [PrintGuard](https://github.com/oliverbravery/PrintGuard) by Oliver Bravery (GPL-2.0) - showed that
  a small, fast model on a Pi works, and the "hold for a while before acting" alert idea. Its list of
  datasets pointed us to several of the sets above. **No PrintGuard code or model is used.**

### Software

- [PyTorch / torchvision](https://github.com/pytorch/vision) (BSD-3-Clause) - MobileNetV3 and training
- MobileNetV3 starting weights trained on [ImageNet](https://www.image-net.org/) (ImageNet's terms are for research use; check them before any commercial use)
- [ONNX](https://github.com/onnx/onnx) and [ONNX Runtime](https://github.com/microsoft/onnxruntime) (Apache-2.0 / MIT) - running the model
- [Roboflow](https://roboflow.com) and [Kaggle](https://www.kaggle.com) - dataset hosting
