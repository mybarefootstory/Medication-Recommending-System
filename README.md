# **Personalized Medical Recommendation System with Machine Learning**

Welcome to the **Personalized Medical Recommendation System**, a powerful platform designed to help users manage their health by leveraging advanced machine learning algorithms. This system accurately predicts potential diseases based on user-input symptoms and offers tailored recommendations for medications, prescriptions, and even workout routines, all while ensuring user privacy and data security.

## **Key Features**

- **User-Friendly Interface**: Our intuitive, easy-to-navigate interface enables users to input symptoms and receive health recommendations seamlessly.
- **Advanced Machine Learning Models**: Utilizing state-of-the-art algorithms like **Support Vector Machines (SVM)**, our system provides accurate disease predictions by analyzing symptoms data.
- **Personalized Recommendations**: Beyond disease prediction, users receive recommendations for the top 5 medications, along with details on prescriptions, dietary suggestions, and custom workout plans.
- **Flask Web Application**: The entire system is powered by a **Flask** web app, allowing for easy access across devices, ensuring a hassle-free healthcare experience.
- **Data Security and Privacy**: Your health data is handled with the utmost confidentiality, in compliance with strict data security standards. User information is never shared or misused.
- **Continuous Model Improvement**: Our machine learning models continuously evolve through data updates, improving accuracy and relevance over time.

## **System Workflow**

1. **Symptom Input**: Users enter their symptoms into the system via the web app.
2. **Model Prediction**: The system processes the input using a pre-trained **SVM model** to predict the most likely disease.
3. **Personalized Output**: Based on the predicted disease, the system provides:
   - A brief description of the disease.
   - Top 5 medication suggestions.
   - Recommended precautions and dietary guidelines.
   - Suggested workout routines to assist in recovery.

## **Machine Learning Models**

We employed several machine learning models to compare performance and selected the best-performing one. The models evaluated include:

- **Support Vector Classifier (SVC)**
- **Random Forest Classifier**
- **Gradient Boosting Classifier**
- **K-Nearest Neighbors (KNN)**
- **Multinomial Naive Bayes**

The **SVM model** provided the highest accuracy for disease prediction, and the model was serialized using pickle for future use in the Flask app.

## **Dataset**

We use a dataset containing various diseases, symptoms, medications, precautions, diets, and workouts:

- **Symptom Data**: `symptoms_df.csv`
- **Precaution Data**: `precautions_df.csv`
- **Workout Data**: `workout_df.csv`
- **Description Data**: `description.csv`
- **Medication Data**: `medications.csv`
- **Diet Data**: `diets.csv`

## **How It Works**

1. **Input Symptoms**: The user provides a list of symptoms (e.g., "fever, cough, headache").
2. **Prediction**: The system maps these symptoms to an input vector using a pre-defined symptom dictionary and runs it through the **SVM model**.
3. **Disease Identification**: Based on the model’s output, the most likely disease is identified.
4. **Helper Functions**: The system retrieves additional information such as disease description, medication, workout, and precautions using custom helper functions.

## **Flask Integration**

The Flask app serves as the front end, handling routes such as:

- `/` for the home page.
- `/predict` to process the symptoms input and display predictions.
- `/about`, `/contact`, and more for additional informational pages.

The application renders predictions, recommendations, and health guidelines via HTML templates.

## **Code Example**

```python
@app.route('/predict', methods=['POST', 'GET'])
def predict():
    if request.method == 'POST':
        symptoms = request.form.get('symptoms')
        user_symptoms = [s.strip() for s in symptoms.split(',')]
        predicted_disease = get_predicted_value(user_symptoms)
        desc, pre, med, die, wrkout = helper(predicted_disease)
        return render_template('index.html', predicted_disease=predicted_disease, dis_des=desc, dis_pre=pre, dis_med=med, dis_diet=die, dis_wrkout=wrkout)
```
## **How to Run the Project**

### **Clone the repository**:

```bash
git clone https://github.com/yourusername/Personalized-Medical-Recommendation-System.git
```

## Install required dependencies:
```bash
pip install -r requirements.txt
```

## Future Improvements
Integration of More Data: We plan to expand the dataset with additional diseases and symptoms for better predictions.
Model Optimization: Future updates will explore model hyperparameter tuning to further improve accuracy.
Mobile Support: We aim to develop a mobile app version for even easier access to personalized health recommendations.

## Credits
This project is inspired by the work from the Medicine Recommendation System - Personalized Medical Recommendation System with Machine Learning by Noor Saeed. Their contribution laid the foundation for building and enhancing this project.
