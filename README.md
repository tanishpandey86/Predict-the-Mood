# 🎭 Predict the Mood

A machine learning-powered application that analyzes text input and predicts the emotional mood of the user. The project combines NLP-based feature extraction with multiple trained classifiers to deliver accurate mood detection through an interactive interface.

---

## ✨ Features

- **Multi-Model Mood Prediction** — Uses four trained classifiers (Logistic Regression, Naive Bayes, Decision Tree, KNN) to predict mood from text input
- **TF-IDF Text Vectorization** — Converts raw text into meaningful numerical features using a pre-trained TF-IDF model
- **Pre-trained Model Support** — All models are serialized as `.pkl` files for instant inference without retraining
- **Interactive Deployment Interface** — Powered by `deploy.py` for a clean, real-time user experience
- **Comparative Model Evaluation** — Easily compare predictions across different classifiers
- **Lightweight & Modular** — Clean project structure makes it easy to swap models or extend functionality
- **Fast Inference Pipeline** — End-to-end prediction in milliseconds from text input to mood output

---

## 🧰 Prerequisites

Before getting started, make sure you have the following installed:

| Requirement | Version |
|---|---|
| Python | 3.8 or higher |
| pip | Latest recommended |
| Git | Any recent version |
| Streamlit (for UI) | Included in `requirements.txt` |

> 💡 A virtual environment is **strongly recommended** to avoid dependency conflicts.

---

## ⚙️ Installation & Setup

**1. Clone the repository**

```bash
git clone https://github.com/tanishpandey86/Predict-the-Mood.git
cd Predict-the-Mood
```

**2. Create a virtual environment**

```bash
python -m venv venv
```

**3. Activate the virtual environment**

```bash
# On macOS/Linux
source venv/bin/activate

# On Windows
venv\Scripts\activate
```

**4. Install dependencies**

```bash
pip install -r requirements.txt
```

**5. Run the application**

```bash
streamlit run deploy.py
```

> The app will open in your browser at `http://localhost:8501`

---

## 🛠️ Technologies Used

| Category | Technology |
|---|---|
| **Language** | Python 3.8+ |
| **NLP / Vectorization** | Scikit-learn (TF-IDF Vectorizer) |
| **Machine Learning** | Scikit-learn (LR, NB, DT, KNN) |
| **Model Serialization** | Pickle (`.pkl`) |
| **Web Interface** | Streamlit |
| **Data Handling** | Pandas, NumPy |
| **Version Control** | Git & GitHub |

---

## 🔄 Data Flow Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER INPUT                               │
│              (Text entered via Streamlit UI)                    │
└─────────────────────────┬───────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                   TEXT PREPROCESSING                            │
│     Lowercasing → Punctuation Removal → Stop Word Filtering     │
└─────────────────────────┬───────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│               TF-IDF VECTORIZATION (tfidf_model.pkl)            │
│       Converts cleaned text into a numerical feature vector     │
└─────────────────────────┬───────────────────────────────────────┘
                          │
            ┌─────────────┼─────────────┐─────────────┐
            ▼             ▼             ▼              ▼
    ┌──────────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐
    │  Logistic    │ │  Naive   │ │ Decision │ │     KNN      │
    │  Regression  │ │  Bayes   │ │   Tree   │ │   Classifier │
    │ (lr_model)   │ │(nb_model)│ │(dt_model)│ │ (knn_model)  │
    └──────┬───────┘ └────┬─────┘ └────┬─────┘ └──────┬───────┘
            └─────────────┴─────────────┴──────────────┘
                                    │
                                    ▼
            ┌───────────────────────────────────────────┐
            │          MOOD PREDICTION OUTPUT           │
            │   (e.g., Happy 😄 / Sad 😢 / Angry 😠)   │
            └───────────────────────────────────────────┘
                                    │
                                    ▼
            ┌───────────────────────────────────────────┐
            │         STREAMLIT UI DISPLAY              │
            │   Renders predicted mood to the user      │
            └───────────────────────────────────────────┘
```

### Step-by-Step Flow

1. **User Input** — The user enters a text string (sentence, phrase, or paragraph) into the Streamlit interface.
2. **Text Preprocessing** — The raw input is cleaned: lowercased, stripped of punctuation and noise.
3. **TF-IDF Vectorization** — The pre-trained `tfidf_model.pkl` transforms the cleaned text into a sparse feature vector representing word importance.
4. **Parallel Model Inference** — The feature vector is passed to all four pre-trained classifiers simultaneously:
   - `lr_model.pkl` → Logistic Regression
   - `nb_model.pkl` → Naive Bayes
   - `dt_model.pkl` → Decision Tree
   - `knn_model.pkl` → K-Nearest Neighbors
5. **Mood Prediction** — Each model outputs a predicted mood label based on learned patterns from the training data.
6. **Result Display** — The predicted mood(s) are displayed back to the user via the Streamlit interface.

---

## 📂 Project Structure

```
Predict-the-Mood/
│
├── deploy.py            # Main Streamlit app — entry point for the UI
├── tfidf_model.pkl      # Pre-trained TF-IDF vectorizer
├── lr_model.pkl         # Trained Logistic Regression model
├── nb_model.pkl         # Trained Naive Bayes model
├── dt_model.pkl         # Trained Decision Tree model
├── knn_model.pkl        # Trained K-Nearest Neighbors model
├── youtube.png          # UI asset / logo
├── requirements.txt     # Python dependencies
└── README.md            # Project documentation
```

---

## 🚀 Future Improvements

- Add deep learning models (LSTM / BERT) for richer text understanding
- Real-time mood prediction from live audio or video input
- Multi-language support for global accessibility
- Dashboard with mood trend analytics over time
- REST API endpoint (FastAPI) for third-party integration
- Cloud deployment (Heroku / AWS / Streamlit Cloud)
- Explainability layer using SHAP or LIME

---

## 🤝 Contributing

Contributions are welcome! To get started:

1. Fork the repository
2. Create a new feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m "Add: your feature description"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Tanish Pandey**  
[GitHub](https://github.com/tanishpandey86)

---

> ⭐ If you found this project helpful, give it a star on GitHub!
