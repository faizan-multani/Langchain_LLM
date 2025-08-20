# Basic Questions ?
## Q 1. What is LangChain, and why is it useful?
- LangChain is a Python/JavaScript framework for building applications that use LLMs with additional functionality like memory, tools, and access to external data.

### Why it's useful:
- Makes it easier to build complex LLM-based apps

- Lets LLMs interact with real-world tools (databases, files, APIs)

- Modular, so you can customize parts easily

## Q 2. What components make up a LangChain application?

- Key components:

- LLMs: The language model (e.g., GPT-4)

- Chains: Sequences of calls (LLM + logic)

- Prompts: Templates that format the input to the LLM

- Memory: Stores conversation history

- Tools: External functions the LLM can use (e.g., calculator, web search)

- Agents: Decide which tools to use based on user input

## Q 3. How does LangChain interact with LLMs like GPT-4?
- LangChain uses wrappers to communicate with LLM APIs (like OpenAI, Anthropic, etc.). You can send prompts and get structured responses back using LangChain’s built-in modules.

## Q 4. What is a chain in LangChain?
- A chain is a sequence of components that are executed in order. Example:

- Input → Prompt → LLM → Output

- You can have SimpleChains (just one prompt + LLM) or MultiChains (LLM + tools + logic).

## Q 5. What are the main use cases for LangChain?

- Chatbots with memory

- Q&A over documents

- Data summarization

- Agents that can browse the web or call APIs

- Code generation tools



# Intermediate Questions ?
## Q 6. What are tools and agents in LangChain?

- **Tools**: Functions the LLM can call (e.g., search engine, math calculator)

- **Agents**: Use reasoning to decide which tools to use based on a task

### Agents follow steps like:

- Interpret user input

- Pick the right tool

- Use the tool

- Respond to the user

## Q 7. How do you use LangChain to answer questions from a PDF?
- Load the PDF using a document loader

- Split the text into chunks

- Create embeddings for the chunks

- Store them in a vector store (like FAISS or Pinecone)

- On user query, retrieve the most relevant chunks

- Use RAG to send relevant data + question to the LLM

## Q 8. What is a prompt template in LangChain and why use it?
### A prompt template is a structured way to create dynamic prompts. It helps you:

- Reuse common prompt structures

- Keep your code cleaner

- Add variables into prompts easily

### Example:

- PromptTemplate.from_template("What is a good name for a company that makes {product}?")

## Q 9. Explain memory in LangChain. What types of memory are available?
### Memory allows the LLM to remember past interactions (important for chatbots).

**Types**:

- BufferMemory: Stores entire conversation history

- SummaryMemory: Stores a summarized version (saves tokens)

- EntityMemory: Tracks specific entities (people, places)

- VectorStoreMemory: Uses embeddings to store memory chunks

## Q 10. How does LangChain support Retrieval-Augmented Generation (RAG)?
### LangChain provides:

- Document loaders (for files, web pages, etc.)

- Text splitters

- Embedding tools (OpenAI, HuggingFace)

- Vector store integrations (FAISS, Pinecone)

- Retriever modules to fetch context

- LLMs to generate responses based on retrieved content

- This forms a full RAG pipeline.

# Advanced Questions ?
## Q 11. How would you create a LangChain agent that uses multiple tools (e.g., calculator + web search)?

### Define each tool:

- Calculator → LangChain’s built-in tool

- Web search → Use SerpAPI or Tavily tool

- Set up agent type (e.g., ReActAgent or OpenAIFunctionsAgent)

- Pass tools and prompt to agent

- Use the agent to process input and select tools dynamically

## Q 12. How does LangChain manage multi-step reasoning or decision-making?

### LangChain uses agents with reasoning strategies (like ReAct or function-calling agents). They:

- Think about what steps to take

- Choose a tool or generate a response

- Repeat until the task is complete

- The LLM gets feedback from previous steps to adjust its plan.

## Q 13. How do you integrate LangChain with vector databases like Pinecone or FAISS?

- Convert documents to embeddings

- Store them in FAISS/Pinecone using LangChain wrappers

- Use .similarity_search() to find relevant chunks

- Pass chunks to LLM for generation (RAG)

- LangChain provides built-in support for many vector DBs.

## Q 14. What are LangChain callbacks, and how can you use them for logging or monitoring?

### Callbacks let you track and log what the LLM and chains are doing. You can:

- Log inputs/outputs

- Monitor performance

- Debug chain steps

- Visualize flow

- Use built-in or custom callback handlers.

## Q 15. Explain a real-world project you built using LangChain and LLMs.

**Example answer**:

- I built a chatbot that answers questions about internal documents. I used LangChain to load PDFs, split them into chunks, store them in FAISS with OpenAI embeddings, and used RetrievalQA to respond to user queries. The app was deployed as a web chatbot with memory and followed a RAG approach.