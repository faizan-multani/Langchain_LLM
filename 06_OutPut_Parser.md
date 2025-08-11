# OutPut Parser :
- An Output Parser is a <mark>tool or method that takes the raw text output from an LLM and transforms it into structured data—like a Python dictionary, a list, JSON, or even a custom object.</mark>

- it is the translator between the AI’s response and your code.

##  Why Do We Need It ?
- LLMs often return <mark>**unstructured text** </mark>. But in most applications, especially in software or data workflows, we need the <mark>**output to be machine-readable and predictable**</mark>.

## Note :
### Without an output parser, you'd have to manually :

- <mark>**Parse strings** </mark>

- <mark>**Use regex** </mark>

- <mark>**Handle edge cases** </mark>

- <mark>**Deal with inconsistent formatting** </mark>

- Which is fragile and error-prone.

## What It Does (Examples) :
### 🔹 Raw LLM Output :
```
Name: Alice
Age: 30
Location: Paris
```

### Parsed/Output Parser (Structured) Output :
```
{
  "name": "Alice",
  "age": 30,
  "location": "Paris"
}
```

## Prompt Template + LLM +Output Parsers (Example) :
```
from langchain.chat_models import ChatOpenAI
from langchain.prompts.chat import ChatPromptTemplate
from langchain.schema import BaseOutputParser

chatllm=ChatOpenAI(openai_api_key=os.environ["OPEN_API_KEY"],temperature=0.6,model='gpt-3.5-turbo')

class Commaseperatedoutput(BaseOutputParser):
    def parse(self,text:str):
        return text.strip().split(",")


template="You are a helpful assistant. When the user given any input , you should generate 5 words synonyms in a comma seperated list"
human_template="{text}"
chatprompt=ChatPromptTemplate.from_messages([
    ("system",template),
    ("human",human_template)

])

chain=chatprompt|chatllm|Commaseperatedoutput()
chain.invoke({"text":"intelligent"})

```