# My Notes

## Tutorial Overview

* This tutorial is called [Build an Extraction Chain](https://python.langchain.com/docs/tutorials/extraction/)
* It demonstrates how an LLM can extract info from unstructured text about a person's name, hair color, and height.

## Important Concepts

* When defining a schema for the information you want an LLM to try to extract from unstructured data, there are two best practices:
  1. Document the schema and it's attributes. If using a `Pydantic` class to represent your schema, then that means adding a docstring to the class for the LLM to understand its purpose. You should also add a description to each `Field` in the class.
  2. Each `Field` should be optional if you don't want the LLM to make up an answer when it can't find the information.
* It's also a good idea to make the output schema a list of elements:
  * That way the LLM can return zero elements if it can't extract any info. Or it can return multiple elements if it extracts info for multiples.
  * If using a `Pydantic` class for the schema, you can nest this inside another `Pydantic` class and make it an attribute with a list type like this: `elements: List[Element]`
* One of the most effective ways to improve model performance is to give a model examples of what you want it to do. The technique of adding example inputs and expected outputs to a model prompt is known as [few-shot prompting](https://python.langchain.com/docs/concepts/few_shot_prompting/).
