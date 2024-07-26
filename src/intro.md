# Project Intro

The process of this project can breaks into 2 parts:

## Data Process
1. Data Collection: Data was scripted from OpenAlex, resulting in numerous paper PDFs and JSON files.
2. Data Preprocessing: The large JSON files from OpenAlex were converted into a manageable database using DuckDB, with PDFs managed in detail within the database.
3. Image Extraction and Filtering: Images and their captions were extracted from the PDFs. Each image file was labeled accordingly.
4. Image Labeling: A Zero-Shot Image Classifier was applied for image labeling. While the model performs well on small samples, its performance on large datasets is still being optimized.

## Data Visualization
1. Dimensionality Reduction: Based on classified images and their scores, t-SNE and UMAP were applied for dimensionality reduction, obtaining x and y labels for each image. Additionally, a custom algorithm was developed to generate x and y coordinates based on image labels and scores.
2. Efficient Image Loading: Loading 15,000 images on a webpage is a resource-intensive task. To increase efficiency, image montages were created for loading previews. The 15,000 images were converted into 4 montages, each containing 64x64 images. Initially, the 4 montages are loaded, and the 15,000 images are then rendered in pieces by index.
3. 3D Visualization: The project utilizes Three.js and D3.js for web-based 3D visualization. Detailed implementation can be found in the project documentation.