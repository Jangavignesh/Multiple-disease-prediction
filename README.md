# 🏥 Multiple Disease Prediction System

A web app built with **Streamlit** that uses trained machine learning models to predict the likelihood of three diseases from user-entered medical parameters:

- **Diabetes**
- **Heart Disease**
- **Parkinson's Disease**

> ⚠️ **Disclaimer:** This project is for educational purposes only. It is not a medical device and must not be used for real diagnosis or treatment decisions. Always consult a qualified healthcare professional.

---

## ✨ Features

- Sidebar navigation between the three prediction pages (via `streamlit-option-menu`)
- Clean multi-column input forms for each disease
- Instant prediction on button click, shown as a result message
- Pre-trained models loaded from `.sav` (pickle) files, so no retraining at runtime

---

## 🧠 Prediction Modules

### 1. Diabetes Prediction
Takes 8 inputs (PIMA-style dataset features):

| Feature | Description |
|---|---|
| Pregnancies | Number of pregnancies |
| Glucose | Glucose level |
| BloodPressure | Blood pressure value |
| SkinThickness | Skin thickness value |
| Insulin | Insulin level |
| BMI | Body mass index |
| DiabetesPedigreeFunction | Diabetes pedigree function value |
| Age | Age of the person |

### 2. Heart Disease Prediction
Takes 13 inputs (UCI Heart Disease-style features):

`age`, `sex`, `cp` (chest pain type), `trestbps` (resting BP), `chol` (serum cholesterol), `fbs` (fasting blood sugar > 120 mg/dl), `restecg`, `thalach` (max heart rate), `exang` (exercise-induced angina), `oldpeak` (ST depression), `slope`, `ca` (major vessels), `thal`

### 3. Parkinson's Disease Prediction
Takes 22 voice-measurement features, including:

`MDVP:Fo(Hz)`, `MDVP:Fhi(Hz)`, `MDVP:Flo(Hz)`, Jitter variants, Shimmer variants, `NHR`, `HNR`, `RPDE`, `DFA`, `spread1`, `spread2`, `D2`, `PPE`

---

## 🛠️ Tech Stack

- **Language:** Python 3
- **Frontend/UI:** Streamlit, streamlit-option-menu
- **ML:** scikit-learn (models serialized with `pickle`)

---

## 📁 Project Structure

```
Multiple_disease_prediction/
├── multiple disease prediction.py      # Main Streamlit app
├── streamlit run command.txt           # Command to launch the app
├── models/                             # Trained models (.sav)
│   ├── Trained_diabeties_model.sav
│   ├── Trained_heart_model.sav
│   └── trained_model_parkinsons.sav
├── datasets/                           # Datasets used for training
├── colab_nbs/                          # Colab notebooks for model training
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/Jangavignesh/<your-repo-name>.git
cd <your-repo-name>
```

### 2. (Optional) Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install streamlit streamlit-option-menu scikit-learn numpy pandas
```

### 4. Update model paths
The script currently loads models using absolute Windows paths. Change them to relative paths so the app runs on any machine:

```python
import os
BASE_DIR = os.path.dirname(os.path.abspath(__file__))

diabetes_model = pickle.load(open(os.path.join(BASE_DIR, 'models', 'Trained_diabeties_model.sav'), 'rb'))
heart_model = pickle.load(open(os.path.join(BASE_DIR, 'models', 'Trained_heart_model.sav'), 'rb'))
parkinson_model = pickle.load(open(os.path.join(BASE_DIR, 'models', 'trained_model_parkinsons.sav'), 'rb'))
```

### 5. Run the app
```bash
streamlit run "multiple disease prediction.py"
```
The app opens at `http://localhost:8501`.

---

## 💡 Usage

1. Pick a disease from the sidebar menu.
2. Enter the required values in the input fields.
3. Click the **Test Result** button.
4. The prediction appears below the form.

---

## 🔮 Future Improvements

- Input validation and friendly error messages (e.g. for empty or non-numeric fields)
- Show prediction probability/confidence, not just a binary result
- Model performance metrics and dataset details inside the app
- Dropdowns with labelled options for categorical inputs (sex, chest pain type, etc.)
- Deploy on Streamlit Community Cloud

---

## 📊 Datasets

Models were trained in the Colab notebooks (`colab_nbs/`) on publicly available datasets (copies in `datasets/`):
- PIMA Indians Diabetes Dataset
- UCI Heart Disease Dataset
- UCI Parkinson's Disease Dataset

---

## 👤 Author

**Janga Vignesh**
- GitHub: [Jangavignesh](https://github.com/Jangavignesh)
- LinkedIn: [janga-vignesh](https://www.linkedin.com/in/janga-vignesh-9aa265281/)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
