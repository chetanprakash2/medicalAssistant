
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

%%writefile app.py
# (app code)

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

