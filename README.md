 Title :  A Novel Hybrid Approach for Secure Image Encryption: Leveraging Chaotic Maps and Deep Convolutional Neural Networks

 Abstract: Due to the proliferation of smart devices and high-speed internet, the volume of digital images has surged in recent years, necessitating robust encryption techniques to ensure their integrity. This paper introduces a novel hybrid encryption approach that integrates chaotic maps with deep convolutional neural networks (CNNs) for secure image encryption. The proposed method processes 8,000 color images of varying sizes, resizing them to 128 × 128 pixels for consistent  encryption and decryption. Highly secure keys generated by chaotic maps are used to encrypt and decrypt
the images. A CNN model is then trained on the original, encrypted, and decrypted images, achieving a remarkable accuracy of 98.56% after 100 epochs. Statistical analysis reveals excellent security metrics, with NPCR at 99.65%, UACI at 33.267%, and entropy at 7.989206. The results demonstrate that the proposed approach effectively enhances image security without loss of information. The model is implemented and analyzed using Google Colab, showcasing its potential for safeguarding sensitive image data in various applications.

##  Project Instrcution
 

## 1. **Mounting Google Drive**
- **Code**: `drive.mount('/content/drive')`
- **Purpose**: Mounts Google Drive to access datasets and save results directly in the specified Drive folders.

---

## 2. **Paths Setup**
- **Variables**: `image_folder_path`, `encrypted_folder_path`, `decrypted_folder_path`, `image_folder_path1`.
- **Purpose**: Define paths for the source, encrypted, decrypted, and resized image folders.
  - `image_folder_path`: Path to original images.
  - `encrypted_folder_path`: Folder to save encrypted images.
  - `decrypted_folder_path`: Folder to save decrypted images.
  - `image_folder_path1`: Folder to save resized original images.

---

## 3. **Loading and Resizing Images**
- **Function**: `load_images_from_folder`
- **Purpose**: Loads a specified number of images from a folder, resizes them to a given size, and returns them as NumPy arrays along with their filenames.
- **Key Parameters**:
  - `size`: Target size for resizing the images (default: 128x128).
  - `limit`: Maximum number of images to load (default: 2000).

---

## 4. **Logistic Map**
- **Function**: `logistic`
- **Purpose**: Implements the chaotic logistic map function for generating pseudorandom sequences.
- **Key Parameter**:
  - `mu`: Logistic map parameter (default: 3.57999099).

---

## 5. **Image Encryption**
- **Function**: `encrypt_image`
- **Purpose**: Encrypts an image using chaotic logistic mapping and bitwise XOR operations.
- **Key Steps**:
  1. Flattens each color channel.
  2. Generates a sequence using the logistic map.
  3. Applies XOR operations for encryption.
- **Output**: Encrypted image as a NumPy array.

---

## 6. **Image Decryption**
- **Function**: `decrypt_image`
- **Purpose**: Decrypts an encrypted image back to its original form using the reverse of the encryption process.
- **Key Steps**:
  1. Uses the logistic map sequence.
  2. Applies XOR operations in reverse order.
- **Output**: Decrypted image as a NumPy array.

---

## 7. **Processing Images**
- **Purpose**: Loops through loaded images, performs encryption, decryption, and saves the results.
- **Key Steps**:
  1. Encrypts the image and saves it to `encrypted_folder_path`.
  2. Decrypts the encrypted image and saves it to `decrypted_folder_path`.
  3. Saves the resized original image to `image_folder_path1`.

---

## 8. **Displaying Images**
- **Code**: Matplotlib is used to display the first 4 encrypted images.
- **Purpose**: Visualizes encrypted images for quick verification.

---

## 9. **Normalization**
- **Code**: `images = images.astype('float32') / 256.0`
- **Purpose**: Normalizes image pixel values to the range [0, 1] for compatibility with the neural network.

---

## 10. **Dataset Splitting**
- **Purpose**: Splits the dataset into training (80%) and validation (20%) sets.
- **Key Variables**:
  - `train_images`: Training images.
  - `val_images`: Validation images.

---

## 11. **Autoencoder Model**
- **Purpose**: Defines a convolutional autoencoder for reconstructing input images.
- **Architecture**:
  - **Encoder**:
    - Two convolutional layers with ReLU activation.
    - Two max-pooling layers for dimensionality reduction.
  - **Decoder**:
    - Two transposed convolutional layers for upsampling.
    - A final convolutional layer with a sigmoid activation to output reconstructed images.

---

## 12. **Model Compilation**
- **Optimizer**: Adam optimizer with a custom learning rate of 0.01.
- **Loss Function**: Mean squared error (MSE).
- **Metric**: Accuracy.

---

## 13. **Model Training**
- **Purpose**: Trains the autoencoder on normalized training images.
- **Key Parameters**:
  - `epochs`: Number of training iterations.
  - `batch_size`: Number of samples per gradient update (default: 64).
  - `validation_data`: Used for validating the model after each epoch.

---

## 14. **Histograms for Analysis**
- **Function**: `plot_histograms`
- **Purpose**: Plots histograms for the original, encrypted, and decrypted images to analyze pixel value distributions.
- **Key Steps**:
  1. Separate histograms for red, green, and blue channels.
  2. Shows changes in pixel distributions due to encryption and decryption.

---

## 15. **Encryption and Decryption Validation**
- **Purpose**: Ensures the encryption and decryption processes are functioning as expected by:
  - Verifying decrypted images match original ones.
  - Displaying histograms to observe pixel value differences.

---

### Suggested Structure for README:
1. **Introduction**
2. **Dataset Description**
3. **Dependencies and Setup**
4. **Code Explanation**
   - Mounting Google Drive
   - Paths Setup
   - Loading and Resizing Images
   - Logistic Map
   - Image Encryption and Decryption
   - Processing Images
   - Visualization
   - Normalization and Dataset Splitting
   - Autoencoder Model
   - Model Compilation and Training
   - Histogram Analysis
5. **Results**
6. **Future Improvements**
7. **Acknowledgements**

Let me know if you'd like a draft for the README!
