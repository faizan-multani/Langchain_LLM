# World Wide Translator :
```
import streamlit as st
from openai import OpenAI
from dotenv import load_dotenv
import os

load_dotenv()

# Initialize OpenAI client
# client = OpenAI(api_key="OPEN_API_KEY")  # Replace with your API key
llm = OpenAI(api_key=os.getenv("OPEN_API_KEY"))

# Streamlit UI
st.set_page_config(page_title="World Translator", layout="centered")
st.title("World-Wide Translator")

# Language list (expandable)
languages = [
    "English", "Hindi", "Spanish", "French", "German", "Chinese", "Arabic", "Russian",
    "Japanese", "Korean", "Portuguese", "Italian", "Bengali", "Urdu", "Turkish", "Dutch"
]

# Language selection
source_lang = st.selectbox("Translate From", languages, index=0)
target_lang = st.selectbox("Translate To", languages, index=1)

# User input
user_input = st.text_area("Enter text to translate", height=100)

# Translation function
def translate_text(text, source, target):
    if source == target:
        return "Source and target languages are the same."

    prompt = (
        f"Translate the following text from {source} to {target}. "
        f"Return the translation written using English letters only (transliteration). "
        f"Do not use the native script of {target}.\n\n"
        f"Text: '{text}'"
    )

    try:
        response = llm.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a helpful language translator."},
                {"role": "user", "content": prompt}
            ],
            temperature=0.3,
            max_tokens=150
        )
        return response.choices[0].message.content.strip()
    except Exception as e:
        return f"Error: {e}"

# Translate button
if st.button("Translate"):
    if user_input.strip() == "":
        st.warning("Please enter some text.")
    else:
        with st.spinner("Translating..."):
            result = translate_text(user_input, source_lang, target_lang)
            # st.success("Translation:")
            st.write(f"Translation :{result}")
```