# 🩺 MedChat AI

A conversational medical assistant that provides basic suggestions based on symptoms entered in *English* and *Hinglish*. It's built using LLMs (OpenAI API), vector search (FAISS), and LangChain, all wrapped in a Streamlit interface.

The goal: to help users get preliminary medical insights without needing an immediate doctor visit, especially for common symptoms.

---

## 🔧 Stack

- *Frontend*: Streamlit
- *LLM*: OpenAI (GPT-3.5/4)
- *Vector DB*: FAISS
- *LangChain*: for prompt orchestration
- *Language*: Python

---

## 📦 Setup

```bash
git clone https://github.com/chetanprakash2/medchat-ai.git
cd medchat-ai
pip install -r requirements.txt
streamlit run app.py
