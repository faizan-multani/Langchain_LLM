m# Prompt_Template :
- In LangChain, a PromptTemplate is a way to <mark>**dynamically construct prompts**</mark> that you send to an LLM (like GPT-4). It helps you separate static parts of your prompt from the dynamic variables you want to insert later.

## Why Use PromptTemplate ?
### Imagine you want to ask the LLM something like:

- "Translate the following sentence to French: **'Hello, how are you?'**"

### You don't want to <mark>**hardcode every sentence**</mark>. Instead, you make a template and fill in the sentence dynamically.

```
from langchain.prompts import PromptTemplate

prompt_template = PromptTemplate(input_variables=['country'], template="what is  the capital of {country}") 

prompt_template.format(country="india")

from langchain.chains import LLMChain
chain = LLMChain(llm=llm,prompt=prompt_template)
print(chain.invoke("india"))

# output:
{'country': 'india', 'text': 'The capital of India is New Delhi.'}
```

##  Why It’s Powerful :
- You can reuse prompts across different tasks or pipelines.

- Makes your code modular and readable.

- Helps in managing chains where prompts are built step-by-step.

## Example For PromptTemplate :
- <mark>required import statements</mark>
```
from langchain.chat_models import ChatOpenAI
from langchain.prompts import PromptTemplate
from langchain.chains import LLMChain
import os

llm = ChatOpenAI(openai_api_key=os.environ["OPEN_API_KEY"], temperature=0)

prompt = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?"
)

chain = LLMChain(llm=llm, prompt=prompt)

response = chain.run(product="artificial intelligence toys")
print(response)

```