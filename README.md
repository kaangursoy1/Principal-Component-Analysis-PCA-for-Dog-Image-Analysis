# Principal-Component-Analysis-PCA-for-Dog-Image-Analysis
# Overview
This project applies Principal Component Analysis (PCA) to a set of dog images from the Animal Faces Dataset. The dataset contains 5,239 RGB images of dogs, and the aim is to identify the most significant components in the image data, visualize the principal components, and reconstruct original images using varying numbers of components.

The project includes implementing PCA from scratch without using any library-specific PCA functions. Eigenvalue decomposition techniques such as numpy.linalg.eig or numpy.linalg.svd are utilized to compute eigenvalues and eigenvectors.

# Dataset
Dataset: The combined version of dog images from the Animal Faces Dataset.
Number of images: 5,239
Image size: All images are resized to 64x64 pixels with 3 RGB channels.
Methodology
# Preprocessing:

The images are resized to 64x64 pixels using bilinear interpolation (PIL.Image.open().resize((64,64), Image.BILINEAR)).
Each image is flattened into a 4096x3 matrix and stacked to create a 3D array (5239x4096x3).
The array is sliced into three matrices, Xi, representing each color channel (R, G, B).
PCA Implementation:

PCA is applied separately to each channel matrix (Xi).
The top 10 principal components are computed for each channel, and the proportion of variance explained (PVE) is reported.
The minimum number of components required to reach 70% PVE is determined for each channel.
Visualization of Principal Components:

The first 10 principal components for each color channel are reshaped to 64x64 matrices.

# Results
Variance Explained:

The project reports the PVE for each of the first 10 principal components across all color channels.
The minimum number of principal components required to achieve 70% PVE is identified.
Visualized Components:

The generated RGB images from the top 10 components reveal significant patterns and structures that are present in the dog images.
Reconstructed Images:

The reconstructed images demonstrate how the level of detail improves as more principal components are used.
Higher PVE values result in more accurate reconstructions, whereas using fewer components produces blurred images.
# Challenges & Solutions
Handling Negative Values in Image Data: Image data is converted to float32 to ensure accurate calculations, as PCA involves mean subtraction, which can result in negative values.
Eigenvalue Decomposition: Using both numpy.linalg.eig and numpy.linalg.svd helped accurately compute eigenvalues and eigenvectors while maintaining numerical stability.
Min-max normalization is applied to scale the values between 0 and 1.
The components are combined to generate 10 RGB images, providing a visual representation of the eigenvectors.
Reconstruction of Original Images:
# Results Interpretation
The first few principal components capture significant patterns in the image, like general shape and color gradients.
The reconstructed images improve with more components, highlighting how PCA can compress and retain crucial image details effectively.
# Future Enhancements
Extending the analysis to other animal faces in the dataset.
Applying more advanced dimensionality reduction techniques like t-SNE or autoencoders for deeper insights.
The reconstruction of the first image in the dataset is performed using the following number of components: 1, 50, 250, 500, 1000, 4096.
The reconstruction is achieved by projecting the image onto the selected principal components and transforming it back to the original space.
