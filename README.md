1| # 🕵️‍♂️ Deepfake Image Detector
2| 
3| A deep learning-powered application that detects deepfake images using Convolutional Neural Networks (CNN). Built with TensorFlow/Keras and deployed via Streamlit for an interactive web interface.
4| 
5| ## 🎯 Project Overview
6| 
7| This project implements a binary image classifier to distinguish between real and AI-generated (deepfake) images. Using a custom CNN architecture, the model analyzes facial images and provides real[...]
8| 
9| ## ✨ Features
10| 
11| - **CNN-Based Detection**: Custom 3-layer convolutional neural network architecture
12| - **Real-Time Predictions**: Instant analysis with confidence scores
13| - **Interactive Web Interface**: User-friendly Streamlit dashboard
14| - **Image Preprocessing**: Automatic resizing and normalization (128x128 pixels)
15| - **Performance Metrics**: Processing time tracking for each inference
16| - **Visual Feedback**: Clear prediction results with probability percentages
17| 
18| ## 📁 Project Structure
19| 
20| ```
21| deepfake-detector-Model/
22| ├── V1/
23| │   ├── MODELdeepfakedetector.h5      # Trained CNN model (~38 MB)
24| │   ├── deepfake_app.py                # Streamlit web application
24| │   ├── deepfake_detector_create_model_file.py  # Model training script
25| │   └── research paper.pdf             # Reference research paper
26| └── README.md
27| ```
28| 
29| ## 🏗️ Model Architecture
30| 
31| ### CNN Architecture
32| 
33| ```python
34| Sequential([
35|     Conv2D(32, (3, 3), activation='relu', input_shape=(128, 128, 3)),
36|     MaxPooling2D((2, 2)),
37|     Conv2D(64, (3, 3), activation='relu'),
38|     MaxPooling2D((2, 2)),
39|     Conv2D(128, (3, 3), activation='relu'),
40|     MaxPooling2D((2, 2)),
41|     Flatten(),
42|     Dense(128, activation='relu'),
43|     Dropout(0.5),
44|     Dense(1, activation='sigmoid')  # Binary classification
45| ])
46| ```
47| 
48| ### Model Specifications
49| 
50| | Parameter | Value |
51| |-----------|-------|
52| | Input Size | 128 x 128 x 3 (RGB) |
53| | Optimizer | Adam (lr=0.001) |
|54| | Loss Function | Binary Crossentropy |
|55| | Activation (Output) | Sigmoid |
|56| | Dropout Rate | 0.5 |
|57| | Model Size | ~38 MB |
58| 
59| ## 🚀 Getting Started
60| 
61| ### Prerequisites
62| 
63| ```bash
64| pip install numpy tensorflow matplotlib seaborn scikit-learn streamlit pillow
65| ```
66| 
67| ### Installation
68| 
69| 1. Clone the repository:
70| ```bash
71| git clone https://github.com/yourusername/deepfake-detector-Model.git
72| cd deepfake-detector-Model
73| ```
74| 
75| 2. Install dependencies:
76| ```bash
77| pip install -r requirements.txt
78| ```
79| 
80| ### Running the Application
81| 
82| #### Streamlit Web App
83| 
84| ```bash
85| cd V1
86| python -m streamlit run deepfake_app.py
87| ```
88| 
89| The app will open in your default browser at `http://localhost:8501`
90| 
91| #### Training a New Model
92| 
|93| To train a new model from scratch:
94| 
95| ```bash
96| cd V1
97| python deepfake_detector_create_model_file.py
98| ```
99| 
100| **Note**: You'll need to update the dataset paths in the script to point to your data directories:
101| - Set `fake_dir` to your fake images folder
102| - Set `real_dir` to your real images folder
103| 
104| ## 📊 Usage
105| 
106| ### Web Interface
107| 
108| 1. **Launch the app** using the Streamlit command
109| 2. **Upload an image** (JPG, JPEG, or PNG format)
110| 3. **View results** including:
111|    - Prediction: Real or Fake
112|    - Confidence probability
112|    - Processing time
113| 
114| ### Prediction Process
115| 
116| ```python
117| # Image preprocessing
118| - Resize to 128x128 pixels
119| - Normalize pixel values (0-1 range)
120| - Convert RGBA to RGB if needed
121| - Predict using trained model
122| ```
123| 
124| ## 🔬 Model Training Details
125| 
126| ### Data Preprocessing
127| 
128| - **Image Size**: 128x128 pixels
129| - **Normalization**: Pixel values divided by 255.0
130| - **Train/Test Split**: 80/20 ratio
131| - **Random State**: 42 (for reproducibility)
132| 
133| ### Training Configuration
134| 
135| - **Epochs**: Configurable (default: 2 for quick testing)
136| - **Validation**: Real-time validation on test set
137| - **Metrics**: Accuracy and Binary Crossentropy Loss
138| 
139| ### Evaluation Metrics
140| 
141| The model tracks:
142| - Training accuracy and validation accuracy
143| - Confusion matrix visualization
144| - Classification report (Precision, Recall, F1-Score)
145| - Loss curves over epochs
146| 
147| ## 🎨 Web Interface Features
148| 
149| The Streamlit app provides:
150| 
151| - **📤 File Upload**: Drag-and-drop or browse for images
152| - **🖼️ Image Preview**: View uploaded image before prediction
153| - **📊 Metrics Dashboard**: Three-column layout showing:
154|   - Prediction result (Real/Fake)
155|   - Confidence percentage
156|   - Processing time in seconds
157| - **🎨 Professional UI**: Clean, intuitive interface design
158| 
159| ## 🛠️ Technologies Used
159| 
160| - **TensorFlow/Keras**: Deep learning framework
161| - **Streamlit**: Web application framework
162| - **NumPy**: Numerical computations
163| - **Pillow (PIL)**: Image processing
164| - **Matplotlib**: Visualization (training)
165| - **Seaborn**: Statistical visualization
166| - **Scikit-learn**: Model evaluation metrics
167| 
168| ## 📈 Model Performance
169| 
170| The model provides:
171| - **Binary Classification**: Fake (0) vs Real (1)
172| - **Threshold**: 0.5 for classification
173| - **Confidence Scores**: Percentage-based probability
174| - **Fast Inference**: Typically < 1 second per image
175| 
176| ## 🔧 Customization
177| 
178| ### Modifying the Model
179| 
180| Edit `deepfake_detector_create_model_file.py` to:
181| - Add more convolutional layers
182| - Adjust filter sizes and counts
183| - Change dropout rates
184| - Experiment with different optimizers
185| - Increase training epochs
186| 
187| ### Updating the App
188| 
189| Modify `deepfake_app.py` to:
190| - Change the UI layout
191| - Add more visualization features
192| - Implement batch processing
193| - Add result export functionality
194| 
195| ## 📝 Dataset Requirements
196| 
197| For training, organize your dataset as:
198| 
199| ```
200| Data/
201| ├── Fake/
202| │   ├── fake_image_001.jpg
203| │   ├── fake_image_002.jpg
204| │   └── ...
205| └── Real/
206|     ├── real_image_001.jpg
207|     ├── real_image_002.jpg
208|     └── ...
209| ```
210| 
211| ## 🔍 How It Works
212| 
213| 1. **Upload Image**: User uploads a facial image
214| 2. **Preprocessing**: Image is resized to 128x128 and normalized
215| 3. **CNN Analysis**: Model processes through convolutional layers to extract features
214| 4. **Classification**: Sigmoid activation produces probability score
215| 5. **Result**: Prediction (Fake/Real) with confidence percentage
216| 
217| ## 📚 Research
218| 
219| This project is based on deepfake detection research. See `research paper.pdf` for more details on the underlying concepts and methodologies.
220| 
221| ## ⚠️ Limitations
222| 
223| - Model is trained on specific datasets and may not generalize to all deepfake types
224| - Performance depends on image quality and resolution
225| - Best results with frontal facial images
226| - May require retraining for new deepfake generation techniques
227| 
228| ## 🚀 Future Enhancements
229| 
230| - [ ] Add support for video deepfake detection
231| - [ ] Implement ensemble model architecture
232| - [ ] Create REST API for programmatic access
233| - [ ] Add multi-face detection in single image
234| - [ ] Implement GAN-based augmentation for training
235| - [ ] Deploy to cloud (AWS/GCP/Azure)
236| - [ ] Add explainability features (Grad-CAM visualization)
237| - [ ] Create Docker container for easy deployment
238| 
239| ## 📄 License
240| This project is available for educational and research purposes.
241| 
242| ## 🙏 Acknowledgments
243| 
244| - TensorFlow team for the excellent deep learning framework
245| - Streamlit for the interactive web framework
246| - Research community for deepfake detection methodologies
247| 
248| ## ⭐ Show Your Support
249| 
250| Give a ⭐️ if this project helped you!
251| 
252| ---
253| 
254| **Disclaimer**: This tool is for educational and research purposes. Always verify critical information through multiple sources. Deepfake detection is an evolving field, and no detector is 100% accurate.
255| 
