
🧠 AI Symptom Checker with Remedies

A simple and interactive Streamlit web application that uses a fine-tuned BERT model to predict diseases based on user-described symptoms and suggests basic remedies. Powered by Transformers and Ngrok for easy sharing.

🚀 Features

Predicts likely disease based on symptoms using a BERT-based text classification model.

Displays predicted disease, confidence score, and helpful home remedies.

Runs on Streamlit and can be shared online using Ngrok.

Includes a pre-defined mapping for common diseases like flu, COVID-19, dengue, etc.



---

🛠 Installation

1. Clone this repo or copy the app.py script.

2. Install dependencies:

pip install streamlit transformers pyngrok --quiet


---

🧪 Running the App

1. Write the app code to a Python file :

!pip install streamlit transformers pyngrok --quiet

%%writefile app.py
import streamlit as st
from transformers import pipeline

classifier = pipeline("text-classification", model="shanover/symps_disease_bert_v3_c41")

label_info = {
    "LABEL_0": {"disease": "Common Cold", "remedy": "Rest, drink fluids, and take OTC cold medications."},
    "LABEL_1": {"disease": "Flu", "remedy": "Rest, stay hydrated, and use fever reducers like paracetamol."},
    "LABEL_2": {"disease": "COVID-19", "remedy": "Self-isolate, wear a mask, rest, and consult a doctor if needed."},
    "LABEL_3": {"disease": "Migraine", "remedy": "Avoid triggers, rest in a quiet dark room, and take prescribed meds."},
    "LABEL_4": {"disease": "Food Poisoning", "remedy": "Drink ORS, eat light meals, and rest. Avoid spicy foods."},
    "LABEL_5": {"disease": "Malaria", "remedy": "Consult a doctor, take antimalarial medication, and rest."},
    "LABEL_6": {"disease": "Dengue", "remedy": "Drink plenty of fluids, avoid NSAIDs, and monitor platelet count."},
    "LABEL_7": {"disease": "Typhoid", "remedy": "Antibiotics (prescribed), eat soft food, and maintain hygiene."},
    "LABEL_8": {"disease": "Pneumonia", "remedy": "Consult a doctor for antibiotics and rest properly."},
    "LABEL_9": {"disease": "Sinusitis", "remedy": "Steam inhalation, stay hydrated, and use nasal sprays."},
    "LABEL_29": {"disease": "Acid Reflux", "remedy": "Avoid spicy food, eat smaller meals, and use antacids."},
}

st.title("🧠 AI Symptom Checker with Remedies")

user_input = st.text_area("Describe your symptoms:", placeholder="e.g. I have fever, body pain and dry cough")

if st.button("Predict Disease"):
    if user_input.strip() == "":
        st.warning("Please enter some symptoms.")
    else:
        result = classifier(user_input)
        label = result[0]['label']
        confidence = round(result[0]['score'] * 100, 2)

        info = label_info.get(label, {"disease": "Unknown", "remedy": "No remedy available."})
        disease = info['disease']
        remedy = info['remedy']

        st.success(f"*Predicted Disease:* {disease}")
        st.info(f"*Confidence:* {confidence}%")
        st.write(f"*Suggested Remedy:* {remedy}")


from pyngrok import ngrok, conf

# Set your authtoken
conf.get_default().auth_token = "<YOUR_AUTHTOKEN>"

# Start tunnel
public_url = ngrok.connect(8501)
print(f"The app is live at: {public_url}")

2. Start the Streamlit app:

streamlit run app.py

3. Ngrok Tunnel (for sharing your app online):

from pyngrok import ngrok, conf

conf.get_default().auth_token = "<YOUR_AUTHTOKEN>"
public_url = ngrok.connect(8501)
print(f"🌍 Your app is live at: {public_url}")

Replace <YOUR_AUTHTOKEN> with your actual Ngrok Authtoken.


---

🧠 Model Info

The app uses the Hugging Face model: shanover/symps_disease_bert_v3_c41

This model is fine-tuned for text classification on symptom-based disease prediction tasks.


---

🏥 Supported Diseases & Remedies


---

🧠 How It Works

1. User enters symptoms in plain text.


2. Text is passed to a BERT-based classifier model.


3. Model outputs a predicted label and confidence score.


4. The app maps the label to a known disease and displays a remedy.




---

📌 Notes

The app is for informational purposes only and does not replace professional medical advice.

Model predictions are based on limited training data and may not cover all diseases.

Always consult a qualified healthcare provider for serious or persistent symptoms.



---

🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first.


---

📄 License

This project is licensed under the MIT License.

