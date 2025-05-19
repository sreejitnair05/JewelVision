JewelVision - AI-Powered Jewelry Image Search

Overview
--------
JewelVision is a web application that allows users to upload an image of a piece of jewelry and find similar styles using AI-powered image search.  The application uses the CLIP model to extract image features and FAISS for efficient similarity search.

![image](https://github.com/user-attachments/assets/d6855e7b-784f-44c4-a481-4054dd3aab42)


Key Features
------------
* Image Upload: Users can upload an image of jewelry to find similar items.
* AI-Powered Search:  Uses the CLIP model to understand the visual content of the image.
* Similarity Search:  Employs FAISS for fast and efficient similarity search in a database of jewelry images.
* Results Display:  Displays the uploaded image along with similar jewelry images, including details like filename, jewelry type, and metal used.
* Responsive UI:  A clean and responsive user interface built with Gradio.

Technical Details
-----------------
* Python: The application is written in Python inside Google Colab.
* Libraries:
    * CLIP:  Used for extracting image features.
    * FAISS:  Used for similarity search.
    * Gradio:  Used for creating the web interface.
    * Pandas:  Used for data manipulation.
    * PIL (Pillow): Used for image processing.
    * PyTorch: Used as a backend for CLIP.
* Image Processing:  Uploaded images are preprocessed before feature extraction.
* Feature Extraction:  CLIP's image encoding capabilities are used to convert images into feature vectors.
* Similarity Indexing:  FAISS is used to create an index of image features for fast similarity search.
* User Interface:  Gradio provides an interactive interface for uploading images and viewing results.

Setup and Installation
----------------------
1.  **Mount Google Drive:** The notebook assumes that the dataset is located in a Google Drive folder named `JeweleryRecognition`, so the same needs to be uploaded there.  The first code cell mounts the user's Google Drive.
2.  **Define Paths:** The notebook defines the base directory, image directory, and CSV file path.
3.  **Install Dependencies:** The notebook installs the necessary Python packages, including `ftfy`, `regex`, `tqdm`, `CLIP`, and `faiss-cpu`.
4.  **Load Data:** The notebook loads the jewelry image data from the CSV file and constructs the filepaths.
5.  **Extract Image Features:** The CLIP model extracts feature vectors from the images.
6.  **Build FAISS Index:** A FAISS index is created from the image features.
7.  **Define Search Function:** The `run_search` function takes an uploaded image, extracts its features, searches the FAISS index for similar images, and displays the results.
8.  **Define Gradio Interface:** The Gradio library is used to create the web interface, including the image upload component, results display, and back button.
9.  **Run the Application:** The Gradio interface is launched, making the application accessible through a web browser.

How to Use
----------
1.  **Upload Image:** Upload an image of a piece of jewelry using the file upload component.
2.  **View Results:** The application will display the uploaded image along with similar jewelry images.  Information about the similar images (filename, jewelry type, metal used) will also be shown.
3.  **Back to Search:** Click the "⬅️ Back to Search" button to upload a new image and perform another search.

Notes
-----
* The application assumes that the images and labels are organized in a specific directory structure within Google Drive.
* The CLIP model used is `ViT-B/32`.
* The similarity threshold is set to 0.25.  Images with a similarity score below this threshold are not displayed.
* The application includes a check to verify that the uploaded image is actually jewelry.

Future Improvements
-------------------
* **Expanded Dataset:** Increase the size and diversity of the jewelry image dataset to improve the accuracy and robustness of the search results.
* **Refined Similarity Metrics:** Experiment with different similarity metrics and ranking algorithms to provide more relevant search results.
* **Jewelry Type Classification:** Add a feature to automatically classify the type of jewelry (e.g., ring, necklace, earring) in the uploaded image.
* **Metal and Gemstone Detection:** Implement functionality to identify the types of metal and gemstones present in the jewelry.
* **Performance Optimization:** Optimize the application for faster search and response times.
* **Mobile Responsiveness:** Enhance the mobile responsiveness of the user interface.

Contact
-------
* LinkedIn: https://www.linkedin.com/in/sreejit-gopinath-nair-721a4a229/
* Email:   sreejitnair05@gmail.com

Repository
----------
* GitHub:  https://github.com/sreejitnair05/JewelVision

Support
-------
If you found this project helpful, please consider giving it a star on GitHub! ⭐
 
