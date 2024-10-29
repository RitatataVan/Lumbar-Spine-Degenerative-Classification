# RSNA 2024 Lumbar Spine Degenerative Classification

![LLM](https://github.com/user-attachments/assets/be8f32cc-da26-4866-9d14-caf121cc2192)

## Objective
The aim is to build a model to aid in the detection and classification of degenerative spine conditions using lumbar spine MR images.
The challenge focused on the classification of five lumbar spine degenerative conditions: Left Neural Foraminal Narrowing, Right Neural Foraminal Narrowing, Left Subarticular Stenosis, Right Subarticular Stenosis, and Spinal Canal Stenosis. It provided severity scores (Normal/Mild, Moderate, or Severe) for each of the five conditions across the intervertebral disc levels L1/L2, L2/L3, L3/L4, L4/L5, and L5/S1.

## Methods
Utilized YOLOv8 to recognize and classify lumbar spine degenerative symptoms
1.	Data Processing: Based on the provided MRI images and the precise coordinate information of the lumbar vertebrae, I constructed target detection data. Appropriate bounding boxes were set on images of various scales to maximize the retention of severe degenerative features.
2.	Modeling 1: I divided the case images into three major categories for model training:
- Spinal Canal Stenosis (15 classes)
-	Subarticular Stenosis (30 classes)
-	Neural Foraminal Narrowing (30 classes)
During training, I applied data augmentation techniques to enhance the images.
3.	Modeling 2: This approach is similar to Modeling 1 but differs in label masking. Since some case images have multiple labels and YOLOv8 does not support multi-label multi-classification, I removed non-severe degeneration categories (i.e., Normal_Mild and Moderate) from images with multiple labels during the data processing stage. 
4.	Inference: For each of the three categories of images in each case, I used the corresponding models for inference. In each image series, I obtained probabilities for all types and selected the maximum probability for each category as the probability for that category in a single case. The obtained probabilities were then normalized to produce the final classification prediction results.

