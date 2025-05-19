JewelVision: AI-Powered Jewelry Recognition System
![image](https://github.com/user-attachments/assets/d3787967-9f06-4253-a189-e1cce8ee03cc)


Overview:

JewelVision is an advanced AI-powered jewelry recognition system that leverages computer vision and deep learning to identify and find similar jewelry styles. Built with OpenAI's CLIP (Contrastive Language-Image Pre-training) and Facebook AI's FAISS (Facebook AI Similarity Search), JewelVision can analyze jewelry images and suggest visually similar items from a catalog.

Features:

1. AI-Powered Image Recognition: Uses CLIP to extract visual features from jewelry images
2. Fast Similarity Search: Employs FAISS for efficient nearest-neighbor searches
3. User-Friendly Interface: Clean, responsive UI built with Gradio
4: Multi-attribute Classification: Identifies jewelry type and metal used
5: Real-time Results: Provides instant visual matches with descriptions

How It Works
JewelVision operates through a multi-step process:

Feature Extraction: The system uses CLIP, a neural network trained on a variety of image-text pairs, to convert jewelry images into rich feature vectors.
Similarity Index: FAISS creates an efficient index of these feature vectors for quick similarity search.
Visual Search: When a query image is uploaded, JewelVision extracts its features and searches for the most similar items in the index.
Results Display: The system presents visually similar jewelry items along with metadata (jewelry type, metal used).

Technical Architecture:

Dependencies:

Python 3.7+
PyTorch
OpenAI CLIP
FAISS-CPU
Pandas
Pillow
Gradio
Matplotlib

Dataset Structure:

The system uses a dataset with the following structure:

Images/ - Propreitary Directory containing jewelry images
Labels.csv - CSV file with metadata (FILENAME, JEWELLERY_TYPE, METAL_USED, etc.)

Installation & Setup

1. Clone the Repository
bash
git clone https://github.com/yourusername/jewelvision.git
cd jewelvision
2. Install Dependencies
bash
pip install -r requirements.txt
pip install git+https://github.com/openai/CLIP.git
3. Prepare Your Data
Place your jewelry images in the Images/ directory and create a Labels.csv file with the following columns:

FILENAME
JEWELLERY_TYPE
METAL_USED
4. Run the Application
bash
python app.py
Usage
Start the application
Upload a jewelry image through the web interface
View similar jewelry items with their descriptions
Use the "Back to Search" button to upload a new image
Code Explanation
Feature Extraction with CLIP
python
def extract_features(image_paths):
    features = []
    for path in tqdm(image_paths):
        image = preprocess(Image.open(path).convert("RGB")).unsqueeze(0).to(device)
        with torch.no_grad():
            feature = model.encode_image(image).cpu().numpy()
        features.append(feature[0])
    return features
This function processes each image through CLIP's encoder to create feature vectors.

Creating the FAISS Index
python
features_np = np.array(image_features).astype("float32")
faiss.normalize_L2(features_np)
index = faiss.IndexFlatIP(features_np.shape[1])
index.add(features_np)
This code normalizes the feature vectors and adds them to a FAISS index for efficient similarity search.

Search Implementation
python
def run_search(input_image):
    # Process the input image
    img_t = preprocess(input_image.convert("RGB")).unsqueeze(0).to(device)
    with torch.no_grad():
        feats = model.encode_image(img_t).cpu().numpy().astype("float32")
    faiss.normalize_L2(feats)
    
    # Search for similar items
    D, I = index.search(feats, k=5)
    
    # Display results
    # ...
This function takes a query image, processes it through CLIP, and searches for similar items in the FAISS index.

Future Improvements
Add support for text-based jewelry search
Implement image preprocessing for better accuracy
Expand the dataset to cover more jewelry types
Add filtering options (by type, metal, etc.)
Deploy as a standalone web application or mobile app
License
This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgments
OpenAI CLIP for the vision-language model
Facebook AI FAISS for similarity search
Gradio for the web interface
Contact
Your Name - sreejitnair05@gmail.com
Linkedin: https://www.linkedin.com/in/sreejit-gopinath-nair-721a4a229/
Project Link: https://github.com/sreejitnair05/JewelVision
If you find this project useful, please consider giving it a star ⭐️

