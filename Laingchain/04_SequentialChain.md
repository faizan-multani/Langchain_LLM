# SequesntialChains : 
-  a SequentialChain is a type of multi-step pipeline where multiple LLM tasks (or chains) are executed one after another in a fixed order, <mark>**with the output of one chain becoming the input of the next chain.**</mark>

## Example :
### chain 1 input :
- Generate a company name from a product idea.

### chain 2 input :
- Write a slogan for that company name.

```
from langchain.prompts import PromptTemplate
from langchain.chains import LLMChain, SequentialChain
from langchain.chat_models import ChatOpenAI
import os

llm = ChatOpenAI(openai_api_key=os.environ["OPEN_API_KEY"], temperature=0.7)

# Chain 1: Generate company name from product
prompt_name = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?"
)

name_chain = LLMChain(llm=llm, prompt=prompt_name, output_key="company_name")


# Chain 2: Generate slogan based on company name
prompt_slogan = PromptTemplate(
    input_variables=["company_name"],
    template="Write a short, catchy slogan for a company named {company_name}."
)

slogan_chain = LLMChain(llm=llm, prompt=prompt_slogan, output_key="slogan")

overall_chain = SequentialChain(
    chains=[name_chain, slogan_chain],
    input_variables = ['product'],
    output_variables = ['company_name','slogan'])

print(overall_chain.invoke('product':"perfume"))    

# output:
product: perfume
Company Name: gucci
Slogan: "smell like everything."

```

## When to Use SequentialChain:
- You have dependent steps, where later outputs rely on earlier ones.

- You want a simple, linear chain of operations.

- You need to pass and reuse intermediate results.

## Notes:
- Each chain in the sequence must have clearly defined input and output keys.

- Use SimpleSequentialChain if all chains use the same input/output names.

