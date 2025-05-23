# My Notes

## Tutorial Overview

* This tutorial is called [Build a Retrieval Augmented Generation (RAG) App: Part 1](https://python.langchain.com/docs/tutorials/rag/)
* It demonstrates how to load a blog post and use an LLM to answer specific questions about it.

## Important Concepts

* RAG stands for Retrieval Augmented Generation. The main usecase for RAG is creating a sophisticated chatbot that can answer a user's questions on specific information.
* A RAG application has two main components:
  1. **Indexing**: This step happens offline. It involves loading the data and **indexing** it.
  2. **Retrieval and generation**: This step happens in real-time. It involves taking the user's question and **retrieving** relevant data from the index. Then that data gets passed to the LLM which **generates** an answer for the user.
* The full RAG process usually involves these five steps:
 
### Indexing

1. **Load** the data using [Document Loaders](https://python.langchain.com/docs/concepts/document_loaders/) to save them as `Documents`.
2. **Split** the large `Documents` into smaller chunks using [Text splitters](https://python.langchain.com/docs/concepts/text_splitters/). These are saved as `Splits`. There are two benefits to doing this:
    * The model will have an easier time retrieving the answer to a question if the data is broken into smaller chunks.
    * Models have context windows that are limited in size, so all the data in the `Documents` might not fit into the context window.
3. **Store** the splits somewhere for retrieval later. This step also involves transforming the splits into vectors using an embedding model. Both the splits and their embeddings (aka vectors) are stored in a [vector store](https://python.langchain.com/docs/concepts/vectorstores/).

![image](https://github.com/user-attachments/assets/8793d53f-cb89-46f4-868f-1c4ba545836b)

### Retrieval and Generation

4. **Retrieve** the splits from the vector store that are relevant to a user's question.
5. **Generate** an answer to the user's question by sending a prompt to an LLM that includes the user's question and the relevant splits.

![image](https://github.com/user-attachments/assets/66934a4a-1ca2-4a49-bf5a-dc323c2d38a4)

---

* [**Embedding models**](https://python.langchain.com/docs/concepts/embedding_models/) transform human language into a format that machines can understand the semantics of. That format are numerical vectors which machines can compare to understand similarities.
![image](https://github.com/user-attachments/assets/d524ad1b-46a2-4aca-b0c9-6b2378663876)

* [**Query analysis**](https://python.langchain.com/docs/concepts/retrieval/#query-analysis) is a helpful technique when you want the LLM to transform your question into one that is optimized for retrieving relevant data.
![image](https://github.com/user-attachments/assets/952f1261-86d6-4009-ba84-31d872457bf0)


