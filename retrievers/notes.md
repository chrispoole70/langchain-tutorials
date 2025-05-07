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
