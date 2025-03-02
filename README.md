# **semantic segmentation** using a **U-Net architecture with a ResNet50 backbone**  

Semantic segmentation using a U-Net architecture with a ResNet50 backbone on the **oxford_iiit_pet dataset**.

---

## **Preprocessing the Data**

1. **Resize images and masks** to 128x128 pixels.
2. **Normalize the image** scale pixel values to [0,1].
3. **Adjust the mask values**:
   - The dataset labels are **1, 2, 3**  we subtract 1 so they become **0, 1, 2**.
4. **Data Augmentation** (Optional):
   - Flips the image & mask horizontally.

---

## **Prepare the Training & Test Datasets**

1. **Apply preprocess() to training & test sets**.
2. **Batch the data** into groups of **32 images**.
3. **Shuffle & Cache Training Data**.

---

## **Visualization**

**Displays three images per example**:
   - **Original Image**
   - **True Segmentation Mask**
   - **Predicted Mask from the Model**

---

## **Build the U-Net Model with ResNet50 Backbone**

- Uses ResNet50 backbone encoder.
- Removes classification layers to keep only feature extraction layers.
- Extracts four feature maps from different layers of ResNet50.
- These feature maps will be used for skip connections in the decoder.
- Creates an encoder model using ResNet50.
- Freezes weights so only the decoder (U-Net part) is trained.

---

## **Decoder (Upsampling)**

1. Takes the last feature map from the encoder.
2. Iterates through skip connections:
3. Upsamples to match the original 128x128 input size.
4. final layer uses a softmax activation.

---

## **Compile & Train the Model**

- Trains for **15 epochs**.

---

## **Display Predictions**

- Displays predictions alongside true segmentation masks.

