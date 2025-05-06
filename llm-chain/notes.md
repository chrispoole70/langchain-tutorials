# My Notes

## Tutorial Overview

This tutorial is called [Build a simple LLM application with chat models and prompt templates](https://python.langchain.com/docs/tutorials/llm_chain/).

It demonstrates how to translate English text into another language using a single LLM call and some prompting.

## Important Concepts

* [Chat Models](https://python.langchain.com/docs/concepts/chat_models/) are LLMs that accept a list of messages as input and return a message as an output. They use the [Runnable Interface](https://python.langchain.com/docs/concepts/runnables/) which lets you use the chat model in a standard way, such as:
   * Calling the `invoke` method to generate an output message synchronously.
   * Calling the `stream` method to generate an output message asynchronously, such as each token as its produced.
* [Prompt Templates](https://python.langchain.com/docs/concepts/prompt_templates/) help translate user messages into instructions for the LLM. The prompt templates are:
   * String `PromptTemplates` for formatting strings.
   * `ChatPromptTemplates` for formatting a list of `system` and `user` messages. `system` is mapped to `SystemMessage` and `user` is mapped to `HumanMessage`.
   * `MessagesPlaceholder` for specifying the location of `HumanMessages`.
