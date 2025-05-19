# My Notes

## Tutorial Overview

* This tutorial is called [Build an Agent](https://python.langchain.com/docs/tutorials/agents/)
* It demonstrates how to build an agent that can use a tool-call to get the current weather when asked for it.

## Important Concepts

* [Agents](https://langchain-ai.github.io/langgraph/concepts/agentic_concepts/) are systems that use LLMs for **reasoning**:
  * They reason what **actions** to take and what are the necessary inputs to perform those actions.
  * After executing actions, the results can be fed back to the LLM for more reasoning. The LLM can decide whether to finish or take more actions.
  * Actions are often taken using [tool-calling](https://python.langchain.com/docs/concepts/tool_calling/)
* Before you create an agent, you should have:
  1. A model
  2. Tools
* An easy way to create an agent is like this: `create_react_agent(model, tools)`
* Steaming an agent's response is a better user experience especially when an agent can take awhile to finish all of its steps. You can stream:
  * The message after each step with `stream_mode='values'`
  * Each token as its generated with `stream_mode='messages'`
