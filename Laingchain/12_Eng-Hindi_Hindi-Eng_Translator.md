# English-Hindi | Hindi-English Translator :
```
import streamlit as st
from openai import OpenAI
from dotenv import load_dotenv
import os

load_dotenv()

# Initialize OpenAI client
llm = OpenAI(api_key=os.getenv("OPEN_API_KEY"))

# Streamlit page setup
st.set_page_config(page_title="Translator", layout="centered")
st.title("English ↔ Hindi Translator")

# Language selection
language_options = ["English to Hindi", "Hindi to English"]
selected_option = st.selectbox("Choose Translation Direction", language_options)

# User input
user_input = st.text_area("Enter a word or sentence", height=100)

# Translation function
def translate_text(text, direction):
    if direction == "English to Hindi":
        prompt = f"Translate the following English sentence to Hindi:\n\n'{text}'\n\nHindi:"
    else:
        prompt = f"Translate the following Hindi sentence to English:\n\n'{text}'\n\nEnglish:"

    try:
        response = llm.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a helpful translator."},
                {"role": "user", "content": prompt}
            ],
            temperature=0.3,
            max_tokens=100
        )
        translation = response.choices[0].message.content.strip()
        return translation
    except Exception as e:
        return f"Error: {e}"

# Translate button
if st.button("Translate"):
    if user_input.strip() == "":
        st.warning("Please enter some text.")
    else:
        with st.spinner("Translating..."):
            result = translate_text(user_input, selected_option)
            st.write(f"Translation : {result}")


```