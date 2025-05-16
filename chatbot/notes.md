# My Notes

## Tutorial Overview

* This tutorial is called [Build a Chatbot](https://python.langchain.com/docs/tutorials/chatbot/).
* It demonstrates how to have a back-and-forth conversation with an LLM.

## Important Concepts

* A chat model does not know about the state of a conversation by default. That means you can't ask an LLM a question and then a follow-up question and expect it to understand.
* To have an LLM understand the state, you have to provide it with the entire [chat history](https://python.langchain.com/docs/concepts/chat_history/) so that you can have an effective conversation with it. LangGraph has a built-in persistence layer for this. You can save the conversation in-memory or to a database.
* When passing a message to a LangChain app, that will be sent as input to the chat model. And each message will be added to a list of messages. But you should also pass a config dictionary that contains a `thread_id` so that you can separate conversations between different users.
* Conversations have the potential for having lots of messages. It's important that you manage how many messages are sent to the chat model because more messages means higher costs and can potentially surpass the LLM's context window. You should manage this by limiting the size and number of messages you pass to the chat model. There is a `trim_messages` function you can use for this.
* You should [stream](https://python.langchain.com/docs/how_to/streaming/) the generated output token by token because it's a better UX than waiting for the entire output to be generated. You can do this by calling `stream(stream_mode='messages')` with your LangGraph app.
