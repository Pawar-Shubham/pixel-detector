Pixel Coordinate Prediction using Deep Learning

Problem Statement

  The objective is to design a supervised regression model capable of predicting the exact (x, y) coordinates of a single bright pixel in a 50×50 grayscale image.
  
  Each image contains:
  
  One pixel with intensity value 255
  
  All other pixels set to 0
  
  The task is to accurately estimate the spatial position of that pixel using a neural network model.

Approach

  Data Generation
  
  Since the images follow a fixed structure, a synthetic dataset is generated programmatically.
  
  For each sample:
  
  A 50×50 zero matrix is created.
  
  A random coordinate (x, y) is selected.
  
  The pixel at that coordinate is assigned intensity 255.
  
  To improve training stability:
  
  The coordinate labels are normalized to the range [0, 1] by dividing by 49.
  
  This ensures consistent gradient behavior and bounded outputs.
  
  Random seeds are fixed to ensure reproducibility of results.

Model Architecture

  A Convolutional Neural Network (CNN) is used to learn the spatial mapping.

Architecture:
  
  Input: (50, 50, 1)
  → Conv2D (8 filters, 3×3, ReLU, same padding)
  → MaxPooling2D (2×2)
  → Conv2D (16 filters, 3×3, ReLU, same padding)
  → MaxPooling2D (2×2)
  → Flatten
  → Dense (64, ReLU)
  → Dense (2 outputs for x and y coordinates)

Rationale:

  Convolution layers extract spatial patterns.
  
  Pooling reduces dimensionality and computation.
  
  Fully connected layers learn the regression mapping.
  
  Final layer outputs two continuous values representing coordinates.

Training Strategy

  Optimizer: Adam
  
  Loss Function: Mean Squared Error (MSE)
  
  Evaluation Metric: Mean Absolute Error (MAE)
  
  Additional techniques:
  
  Early stopping to prevent unnecessary training
  
  Learning rate reduction on plateau
  
  Model checkpointing to save the best model

Evaluation

  Model performance is evaluated using:
  
  Mean Squared Error (MSE)
  
  Mean Absolute Error (MAE)
  
  R² Score

  Pearson Correlation Coefficient
  
  Mean Euclidean Pixel Distance

The results demonstrate:

  Very low prediction error
  
  Strong correlation between predicted and true coordinates
  
  Sub-pixel level average localization error

Conclusion

  The CNN successfully learns to localize a single bright pixel in a sparse image through supervised regression.
  
  The approach emphasizes:
  
  Clean data normalization
  
  Lightweight and efficient architecture
  
  Proper evaluation metrics
  
  Reproducibility
  
  Clear visualization of results

The model demonstrates accurate and stable coordinate prediction across the dataset.
