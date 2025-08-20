# Basic Questions :
## Q 1. What is a Large Language Model (LLM) ?
- A Large Language Model is an AI model trained on vast amounts of text data to understand and generate human-like language. These models use the Transformer architecture and can perform tasks like summarizing, translating, and answering questions.

## Q 2. How do LLMs like GPT-4 work at a high level?
- They work by predicting the next word (token) in a sequence based on the context of previous words. They use self-attention mechanisms to understand context and relationships between words.

## Q 3. What are tokens in LLMs?
- Tokens are chunks of text (words or subwords) used by LLMs. For example, the word "chatting" might be split into ["chat", "ting"] depending on the tokenizer. GPT models typically use Byte-Pair Encoding (BPE).

## Q 4. What are the differences between GPT-3, GPT-3.5, and GPT-4?
- GPT-3: 175B parameters, good at basic tasks.

- GPT-3.5: Improved fine-tuning, faster, better context handling.

- GPT-4: More advanced reasoning, larger context window (up to 128k tokens), supports image inputs (multimodal), more accurate and safer.

## Q 5. What are the limitations of LLMs?
- Hallucinations (making up facts)

- Lack of real-time awareness or knowledge after their training cutoff

- Bias in outputs

- Sensitive to prompt phrasing

- High computational cost

# Intermediate Questions ?
## Q 6. How does **fine-tuning** differ from **prompt engineering**?
- **Fine-tuning**: Retraining the model on specific data to improve performance.

- **Prompt engineering**: Crafting input prompts to guide the model's response without changing its weights.

## Q 7. What is zero-shot, one-shot, and few-shot learning in the context of LLMs?
- **Zero-shot**: Model solves a task with only instructions (no examples).

- **One-shot**: Model gets 1 example.

- **Few-shot**: Model gets a few examples.
LLMs like GPT-3+ are great at few-shot learning.

## Q 8. How do you handle hallucinations in LLM outputs?

- Use Retrieval-Augmented Generation (RAG) to pull real data

- Add fact-checking layers

- Improve prompts (e.g., "If you don't know, say 'I don't know'")

- Use external APIs for accurate information

## Q 9. What are embeddings and how are they used with LLMs ?
- Embeddings are vector representations of text. LLMs use embeddings to compare or retrieve similar content. They're often used in:

- Semantic search

- Clustering similar documents

- Vector databases (e.g., FAISS, Pinecone)

## Q 10. What is Retrieval-Augmented Generation (RAG)?

- RAG is a technique where you:

- Use a retriever (like a vector DB) to get relevant info

- Feed that info to the LLM for a better, grounded response
It reduces hallucinations and improves accuracy.

# Advanced Questions ?
## Q 11. How would you build a multi-turn dialogue system using an LLM?
- Store past interactions using memory

- Pass previous messages as context in each new prompt

- Use tools like LangChain or ChatML for formatting

- Limit history length to fit within token limits

## Q 12. Explain how attention mechanisms work in Transformer models.
- Attention lets the model focus on relevant parts of the input. It computes scores between words to weigh their importance in generating outputs. Self-attention helps understand context in a sentence.

## Q 13. What are the ethical considerations of deploying LLMs in production?
- Bias and discrimination

- Data privacy

- Misinformation (hallucination)

- Toxic or harmful outputs

- Over-reliance on AI in sensitive areas

## Q 14. What is temperature and top-k sampling in LLM decoding?

- **Temperature**: Controls randomness. Low = more deterministic. High = more creative.

- **Top-k**: Picks from top k most likely words.
Both control the diversity and creativity of the output.

## Q 15. How do you evaluate the performance of an LLM-powered application?
- Use BLEU, ROUGE, or BERTScore for text comparison

- Human evaluation for quality and relevance

- Monitor latency, cost, and token usage

- Check factual accuracy and toxicity scores