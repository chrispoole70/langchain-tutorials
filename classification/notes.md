# My Notes

## Tutorial Overview

* This tutorial is called [Classify Text into Labels](https://python.langchain.com/docs/tutorials/classification/).
* It demonstrates how to classify a passage of text into its sentiment, aggressiveness, and language.

## Important Concepts

* You can send an input message to an LLM and have it classify the text such as the sentiment, the language the text is in, the style it was written in, topics the text is about, etc. This is also known as tagging.
* Tagging works by defining the schema of the output message you want the LLM to use. You give the LLM a `structured_output` to use and it will call a function to format the output message. In LangChain, this is a two step process in a `RunnableSequence`:
  1. You send the input message to the LLM
  2. Behind the scenes, a function will be called to format the output message into your schema.
* A popular way to declare the output schema is by using a [Pydantic](https://docs.pydantic.dev/latest/#pydantic-examples) class. The main benefit to using a Pydantic class is that it will handle serializing the output message into the Python class. Each `Field` in the Pydantic class will be treated as an argument in the function called that formats the output. These `Fields` can be:
  * Optional or required
  * Have a type defined
  * List a possible set of values (using the `enum` argument)
  * Provide a clear description for the LLM to understand what it represents
