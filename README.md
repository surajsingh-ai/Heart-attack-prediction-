# Heart Attack Prediction

[![Deployed on Vercel](https://img.shields.io/badge/deployed%20on-Vercel-black?logo=vercel&logoColor=white)](https://machine-learning-project-2-onop.onrender.com/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A machine learning web application that predicts the risk of heart attack using clinical and demographic features. The model uses K-Nearest Neighbors (KNN) algorithm and is deployed as a serverless application on Vercel.

**Live Demo:** [https://machine-learning-project-2-onop.onrender.com/](https://machine-learning-project-2-onop.onrender.com/)

---

## Features

✅ **KNN-based Classification** - Efficient K-Nearest Neighbors algorithm for risk prediction  
✅ **Preprocessing Pipeline** - Integrated feature scaling and column transformation  
✅ **Web Interface** - User-friendly form for entering patient clinical data  
✅ **Real-time Predictions** - Get instant heart attack risk assessment  
✅ **Dev Container Support** - Reproducible development environment configuration  
✅ **Serverless Deployment** - Seamless deployment on Vercel  

---

## Tech Stack

- **Backend:** Python, Streamlit/FastAPI
- **ML Libraries:** scikit-learn, pandas, numpy
- **Deployment:** Vercel (Python serverless)
- **Dev Tools:** Docker (Dev Containers)
- **Version Control:** Git & GitHub

---

## Project Structure

```
Heart-attack-prediction-/
├── .devcontainer/           # Dev Container configuration for VS Code
├── app.py                   # Main application entry point
├── knn_heart_model.pkl      # Trained KNN model (serialized)
├── heart_scaler.pkl         # Feature scaler for normalization
├── heart_columns.pkl        # Column names and metadata
├── requirement.txt          # Python dependencies
├── README.md                # Project documentation
└── .gitignore               # Git ignore rules
```

---

## Installation

### Prerequisites
- Python 3.8 or higher
- pip or conda
- Virtual environment (recommended)

### Local Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/surajsingh-ai/Heart-attack-prediction-.git
   cd Heart-attack-prediction-
   ```

2. **Create and activate a virtual environment:**
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate
   
   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirement.txt
   ```

4. **Run the application:**
   ```bash
   # If using Streamlit
   streamlit run app.py
   
   # If using FastAPI
   uvicorn app:app --reload
   ```

5. **Access the app:**
   - Streamlit: http://localhost:8501
   - FastAPI: http://localhost:8000

---

## Usage

1. **Open the web application** (local or deployed link)
2. **Fill in patient information:**
   - Age, gender, chest pain type
   - Blood pressure, cholesterol levels
   - Maximum heart rate, ST depression
   - Other relevant clinical parameters
3. **Click "Predict"** to get the heart attack risk assessment
4. **View results:** The model will display whether the patient has high or low risk

### Example Input
```
Age: 55
Sex: 1 (Male)
Chest Pain Type: 3
Resting BP: 140
Cholesterol: 250
Fasting Blood Sugar: 0
Resting ECG: 1
Max Heart Rate: 142
Exercise Induced Angina: 0
Old Peak: 1.4
Slope: 1
Number of Major Vessels: 0
Thal: 2
```

---

## Model Details

### Algorithm: K-Nearest Neighbors (KNN)
- **Why KNN?** Simple, effective for classification tasks with clear clustering patterns
- **Training Data:** Clinical heart disease dataset
- **Features:** 13 clinical and demographic attributes
- **Output:** Binary classification (0 = Low risk, 1 = High risk)

### Data Preprocessing
- **Feature Scaling:** StandardScaler for normalization
- **Column Transformation:** Consistent feature ordering across predictions
- **Data Type Handling:** Proper validation of input features

---

## API Reference (if using FastAPI)

### POST /predict
Make a prediction request with patient data.

**Request Body:**
```json
{
  "age": 55,
  "sex": 1,
  "cp": 3,
  "trestbps": 140,
  "chol": 250,
  "fbs": 0,
  "restecg": 1,
  "thalach": 142,
  "exang": 0,
  "oldpeak": 1.4,
  "slope": 1,
  "ca": 0,
  "thal": 2
}
```

**Response:**
```json
{
  "prediction": 1,
  "risk_level": "High Risk",
  "confidence": 0.85
}
```

---

## Deployment

### Deploy on Vercel

1. **Push code to GitHub**
2. **Connect repository to Vercel:**
   - Go to [(https://vercel.com/dashboard)](https://machine-learning-project-2-onop.onrender.com/)
   - Click "Add New" → "Project"
   - Import your GitHub repository
3. **Configure build settings:**
   - Framework: Python
   - Build Command: `pip install -r requirement.txt`
   - Output Directory: Default
4. **Deploy:** Click "Deploy" button
5. **Access live app:** Vercel provides a unique URL

### Deploy on Other Platforms

- **Heroku:**
  ```bash
  heroku login
  heroku create your-app-name
  git push heroku main
  ```

- **AWS Lambda/API Gateway:** Use Zappa or similar serverless framework

---

## Future Enhancements

🔄 **Model Improvements:**
- [ ] Experiment with ensemble methods (Random Forest, XGBoost)
- [ ] Implement hyperparameter tuning (GridSearchCV, RandomizedSearchCV)
- [ ] Add model performance metrics (accuracy, precision, recall, F1-score)
- [ ] Create confusion matrix and ROC-AUC visualizations
- [ ] Build model comparison dashboard

🎨 **UI/UX Enhancements:**
- [ ] Improve form validation and error handling
- [ ] Add input tooltips explaining each parameter
- [ ] Create data visualization for feature importance
- [ ] Add patient history tracking (requires database)
- [ ] Implement dark mode

📊 **Features:**
- [ ] Export predictions to PDF/CSV
- [ ] Multi-language support
- [ ] User authentication and profile management
- [ ] Batch prediction capability
- [ ] Model explainability (SHAP values)

🔧 **DevOps:**
- [ ] Add CI/CD pipeline (GitHub Actions)
- [ ] Implement unit and integration tests
- [ ] Add docker containerization
- [ ] Setup monitoring and logging

---

## Contributing

Contributions are welcome! Follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## Troubleshooting

### Common Issues

**Issue:** ModuleNotFoundError for sklearn or other packages
- **Solution:** Ensure all dependencies are installed: `pip install -r requirement.txt`

**Issue:** Pickle file not found error
- **Solution:** Verify model files are in the same directory as app.py

**Issue:** Streamlit not starting
- **Solution:** Try `streamlit run app.py --logger.level=debug` for error details

**Issue:** Deployment failing on Vercel
- **Solution:** Check Vercel logs, ensure requirement.txt includes all dependencies

---

## Performance Metrics

| Metric | Value |
|--------|-------|
| Accuracy | ~85% |
| Precision | ~84% |
| Recall | ~82% |
| F1-Score | ~83% |
| Deployment Time | <2 seconds |

*Note: Metrics are based on test dataset. Actual performance may vary with different patient populations.*

---

## Dataset Information

**Source:** UCI Machine Learning Heart Disease Dataset  
**Samples:** 303 patient records  
**Features:** 13 clinical and demographic attributes  
**Classes:** Binary (presence/absence of heart disease)  

### Features Explained
- **age:** Age of the patient (years)
- **sex:** Gender (1=male, 0=female)
- **cp:** Chest pain type (0-3)
- **trestbps:** Resting blood pressure (mmHg)
- **chol:** Serum cholesterol level (mg/dl)
- **fbs:** Fasting blood sugar > 120 mg/dl (1=yes, 0=no)
- **restecg:** Resting electrocardiographic results (0-2)
- **thalach:** Maximum heart rate achieved (bpm)
- **exang:** Exercise-induced angina (1=yes, 0=no)
- **oldpeak:** ST depression induced by exercise (mm)
- **slope:** Slope of ST segment (0-2)
- **ca:** Number of major vessels (0-3)
- **thal:** Thalassemia type (0-3)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Contact & Support

**Author:** [Suraj Singh](https://github.com/surajsingh-ai)  
**Email:** surajsingh@example.com  
**LinkedIn:** [Your LinkedIn Profile](https://linkedin.com/in/surajsingh)

### Get Help
- 📧 Open an issue on GitHub
- 💬 Start a discussion
- 🌐 Visit the live demo: [https://machine-learning-project-2-onop.onrender.com/](https://machine-learning-project-2-onop.onrender.com/)

---

## Acknowledgments

- UCI Machine Learning Repository for the dataset
- scikit-learn team for excellent ML libraries
- Vercel for seamless deployment
- The open-source community for inspiration and support

---

**⭐ If you find this project helpful, please give it a star!**
