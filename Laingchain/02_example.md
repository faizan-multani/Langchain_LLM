# basic example of langchain :
```
from langchain.chat_models import ChatOpenAI
import os

os.environ["OPEN_API_KEY"] = "your api key here"

llm = ChatOpenAI(openai_api_key=os.environ["OPEN_API_KEY"], temperature=0.7)

response = llm.invoke("Write a paragraph on programming language?")
print(response.content)

# output:
 A programming language is a formal language used to instruct computers to perform specific tasks. It consists of a set of rules and symbols that are used to write code, which is then translated into machine-readable instructions by a compiler or interpreter. Programming languages vary in complexity and purpose, with some designed for general-purpose programming while others are specialized for specific tasks or platforms. Common programming languages include Java, Python, C++, and JavaScript. Learning a programming language is essential for anyone looking to develop software, websites, or applications, as it allows them to communicate with computers and create functional and efficient programs. #
```