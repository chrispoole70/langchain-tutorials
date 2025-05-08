# My Notes

## Tutorial Overview

This tutorial is called [Build a semantic search engine](https://python.langchain.com/docs/tutorials/retrievers/).

It demonstrates how to let a user ask questions about info in a PDF document.

## Important Concepts

* Documents are units of text. They often are chunks of an actual larger document. They contain:
   * `page_content` (string): The text
   * `metadata` (dictionary): Some metadata about the document
   * `id` (string, optional): An identifier for the document
* It's more common to use [document loaders](https://python.langchain.com/docs/concepts/document_loaders/) than creating the documents yourself.
   * Document loaders integrate with data sources.
   * [There are hundreds of integrations](https://python.langchain.com/docs/integrations/document_loaders/).
* [Text splitters](https://python.langchain.com/docs/concepts/text_splitters/) are used to split the text in documents into smaller chunks.
  * The benefits to splitting documents into smaller chunks include:
    * Each chunk of text will have a similar length.
    * LLM context windows have a max input. By splitting text into chunks, there's less concern for surpasing the max limit because only the necessary chunks are sent to the LLM.
    * Splitting text into smaller chunks can yield better quality embeddings than a document with a lot of text.
    * When a user asks an LLM a question about the text, having text split into chunks will help the LLM provide a more precise answer by only using the relevant chunks to answer the question.
    * Having smaller chunks of text is more memory-efficient. This also means more tasks can be run in parallel.
  * The recommended text splitter for generic text use cases is the `RecursiveCharacterTextSplitter` which splits the text based on common separators like newlines.
* When a user asks an LLM a question about text from a document, the relevant chunks of text need to be sent to the LLM for it to be able to answer the question. But how do you determine what are the relevant chunks of text? One popular way of doing this is by using [embeddings](https://python.langchain.com/docs/concepts/embedding_models/). Embeddings work like this:
 
![image](https://github.com/user-attachments/assets/45f593e0-5263-45fb-beb8-15363a489899)

  1. **Embed text as a vector**: This means text will be transformed into a numerical vector representation (ie [0.1, 0.2, ...].
  2. **Measure similarity**: When a user asks a question, that get's transformed into an embedding, too. Then it gets compared to the document's embeddings and the ones most similar are returned and shared with the LLM to try and answer the question.
* Vector stores are ways to store embeddings and text from documents:
 * There are lots of [vector store integrations](https://python.langchain.com/docs/integrations/vectorstores/).
 * Using a vector store works like this:
    1. Initialize the vector store with the embedding model
    2. Add the document text splits to the embedding model. This will also create an embedding for each text split.
    3. Query the vector store by passing a string (`vector_store.similarity_search`) or a vector (`vector_store.similarity_search_by_vector`). The most similar document text splits will be returned. You can also optionally return a similarity score.
* Vector stores can also be queried by initializing it as a `VectorStoreRetriever` by calling `vector_store.as_retriever()`. That will allow you to pass queries to the vector store by calling `retriever.invoke()` or `retriever.batch()`.
