Initial Approach to Train GAN Model

1. Introduction

This document outlines the methodology used to train and test Generative Adversarial Networks (GANs) for anomaly detection in retinal images. The GAN models are trained separately for left and right eye images to enhance their ability to detect abnormalities.

2. Data Preprocessing

2.1 Dataset Overview

The dataset consists of retinal images categorized into left and right eye images. These images are resized and normalized before being fed into the GAN models.

2.2 Preprocessing Steps

Load images from predefined directories.

Resize images to 256x256 pixels.

Normalize pixel values to [-1,1] for stable GAN training.

Separate left and right images based on filenames.

Store processed images in processed/left/ and processed/right/ directories.

3. GAN Training

3.1 Model Architecture

The GAN architecture consists of:

Generator: A deep convolutional network that synthesizes realistic retinal images.

Discriminator: A convolutional neural network that differentiates real images from generated ones.

3.2 Training Strategy

Train two separate GANs: one for left eye images, another for right eye images.

Use the Wasserstein GAN with Gradient Penalty (WGAN-GP) for stable training.

Apply Adam optimizer with learning rate 0.0002 and beta values (0.5, 0.9).

Train for 1000 epochs with batch size 16.

Save model checkpoints at regular intervals.

4. Anomaly Detection

4.1 Testing Approach

Load pre-trained GAN models for left and right eyes.

Pass test images through the corresponding GAN.

Measure reconstruction loss using L1 loss and Structural Similarity Index (SSIM).

Generate heatmaps to highlight potential anomalies.

4.2 Evaluation Metrics

Reconstruction Error: Higher error indicates potential abnormalities.

SSIM Score: Lower SSIM suggests structural deviations from normal images.

Visual Inspection: Heatmaps assist in locating abnormal regions.

5. Deployment

A Streamlit web application is used to facilitate real-time anomaly detection.

5.1 Features

Upload an image (left or right eye).

Automatically route the image to the corresponding GAN.

Display results with reconstruction loss, SSIM score, and heatmaps.

6. Conclusion

This methodology ensures a systematic approach to GAN-based anomaly detection in retinal images. The separation of left and right eye models improves specificity, while reconstruction loss and SSIM provide quantitative evaluation of anomalies.

