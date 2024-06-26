# Image Captioner

## Implementation Flow

### Create descriptions Dictionary

1. Create a dictionary named `descriptions` where each key is the name of an image (without the .jpg extension) and the value is a list of 5 captions corresponding to that image.

### Cleaning Captions

2. Write all captions along with their image names into a new file named `descriptions.txt` and save it on disk.

### Create Vocabulary

3. Generate a vocabulary containing all unique words across all 40,000 image captions in the dataset.

### Image Features Extraction using Transfer Learning (ResNet-50)

4. Preprocess each image and extract its features using the ResNet-50 model. Store these encoded features.

### Preprocessing

5. Treat captions as target variables (Y) for prediction.
6. Encode each word into a fixed-sized vector.

### Training Components

7. **Photo Feature Extractor Model:**
   - Extracts image features using ResNet-50 and processes them through a Dense layer to produce a 256-element representation.

8. **Sequence Processor Model:**
   - Takes caption sequences as input, processes them through an Embedding layer and LSTM layer to produce a 256-element vector.

9. **Decoder Model:**
   - Concatenates outputs from both models, uses dropout for regularization, and predicts the next word using a Dense layer with softmax activation.
