# IRISBIO-KEY

This repository contains MATLAB implementations for preprocessing, segmenting, normalizing, feature extraction, and secure key generation from UBIRIS.v2 iris images. The system has been designed for biometric cryptographic applications, where discriminant iris features are transformed into a protected key.

1. Repository Overview

The workflow is organized into three major stages:

Iris Preprocessing & Segmentation
File: main_UBIRISv2.m

Iris Normalization (Rubber Sheet Model)
File: normalize8.m

Feature Extraction and Key Generation
File: test_ubiris1.m

Each step is described in detail below.

2. File Descriptions
➤ 2.1 main_UBIRISv2.m

This script performs preprocessing and segmentation of UBIRIS.v2 iris images.

Operations performed:

The input image is read and converted into a suitable format.

Reflection removal and noise suppression are applied.

Iris and pupil boundaries are detected using edge maps and circular boundary estimation.

Eyelids and eyelashes are optionally masked.

A clean segmented iris region is generated for the normalization stage.

This file acts as the starting point for the entire pipeline.

➤ 2.2 normalize8.m

This script performs iris normalization using Daugman’s Rubber Sheet Model.

Operations performed:

The circular iris region is transformed into a fixed-dimension rectangular strip.

Polar coordinates are remapped to Cartesian space.

Variations in iris size, dilation, and imaging distance are reduced.

A normalized iris template is generated for stable feature extraction.

The output of this script is a rectangular unwrapped iris image.

➤ 2.3 test_ubiris1.m

This script performs discriminative feature extraction and biometric key generation.

Operations performed:

Ensemble iris features are extracted using multiple complementary filters or statistical measures.

Discriminant features are generated to enhance separability between subjects.

Feature quantization and binarization are applied.

A secure key is generated from the processed feature vector.

Optional post-processing (e.g., error correction or hashing) is supported depending on implementation.

This file produces the final cryptographic key output.

3. Workflow Pipeline
UBIRIS.v2 Image
      │
      ▼
main_UBIRISv2.m  
(Iris Preprocessing & Segmentation)
      │
      ▼
normalize8.m  
(Iris Normalization – Rubber Sheet)
      │
      ▼
test_ubiris1.m  
(Feature Extraction → Discriminant Mapping → Key Generation)
      │
      ▼
Final Iris-Based Cryptographic Key

4. Requirements
Software

MATLAB R2017a or later

Image Processing Toolbox

Dataset

UBIRIS.v2 iris image dataset (not included)

5. Usage Instructions

Place your UBIRIS.v2 images in the input/ folder.

Run the preprocessing and segmentation script:

main_UBIRISv2


The segmented iris region will be saved in a temporary workspace variable or output directory.

Normalize the segmented region:

normalize8


Extract features and generate the cryptographic key:

test_ubiris1


The final biometric key will be saved or displayed depending on your code configuration.

6. Folder Structure (Suggested)
├── main_UBIRISv2.m
├── normalize8.m
├── test_ubiris1.m
├── input/
│   └── sample_iris_images/
├── output/
│   ├── segmented/
│   ├── normalized/
│   └── keys/
└── README.md
