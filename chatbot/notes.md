# My Notes

## Tutorial Overview

* This tutorial is called [Build a Chatbot](https://python.langchain.com/docs/tutorials/chatbot/)
* 

## Important Concepts

* A chat model does not know about the state of a conversation by default. That means you can't ask an LLM a question and then a follow-up question and expect it to understand.
* To have an LLM understand the state, you have to provide it with the entire [chat history](https://python.langchain.com/docs/concepts/chat_history/) so that you can have an effective conversation with it. LangGraph has a built-in persistence layer for this. You can save the conversation in-memory or to a database.
* When passing a message to a LangChain app, that will be sent as input to the chat model. And each message will be added to a list of messages. But you should also pass a config dictionary that contains a `thread_id` so that you can separate conversations between different users.
* 
