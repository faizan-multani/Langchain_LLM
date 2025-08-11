## Q&A Chat Bot :
```
from langchain.chat_models import ChatOpenAI
from dotenv import load_dotenv
import os
import streamlit as st
from langchain.schema import HumanMessage

# take environment variables from .env
load_dotenv()

# initialize our strealit app
st.set_page_config(page_title="Q&A chat bot")
st.header("LangChain Chat App")

# Initialize the Chat LLM once
llm = ChatOpenAI(openai_api_key=os.getenv("OPEN_API_KEY"),model_name="gpt-3.5-turbo",temperature=0.5)

input = st.text_input("Enter your question:", key="input")
submit = st.button("Get your response")

# if Get button is clicked
if submit and input:
    with st.spinner("Thinking..."):
        # Use Chat format with HumanMessage
        response = llm([HumanMessage(content=input)])
        # st.subheader("The response is:")
        st.write(response.content)

```

## streamlit :
- Streamlit is an open-source Python library that makes it easy to build interactive web applications — especially for data science, machine learning, and AI projects — using just Python.

- No need to learn HTML, CSS, or JavaScript. If you can write a Python script, you can create a working app with Streamlit.

## installation :
```
pip install streamlit
```
## verify :
```
streamlit --version
```
## run :
```
streamlit run file_name.py
```