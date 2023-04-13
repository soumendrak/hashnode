---
title: "Prompt Engineering"
datePublished: Fri Mar 17 2023 08:04:38 GMT+0000 (Coordinated Universal Time)
cuid: clfc98av401cg95nved7ibat4
slug: prompt-engineering
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677473467489/a5c17ab3-6378-4a0b-8b39-9994662e3a88.png
tags: nlp, llm, chatgpt, promptengineering, bard

---

## TL;DR

> Prompt engineering is a technique used in natural language processing (NLP) to design and create prompts to generate desired outputs from an NLP model. It is used in various NLP applications, such as chatbots, question-answering systems, and language translation. Generated knowledge prompting and ReAct are two advanced techniques that improve the performance of large-scale language models and allow for greater synergy between reasoning and acting. Incorporating external knowledge also benefits commonsense reasoning.

Prompt engineering is a technique used in natural language processing (NLP) that involves designing and creating prompts to generate desired outputs from an NLP model. In simpler terms, prompt engineering is crafting prompts or questions to get a specific response or answer from an AI model.

Prompt engineering is used in various NLP applications, including chatbots, question-answering systems, and language translation. Developers can train AI models to respond accurately and appropriately to user queries by designing effective prompts, improving the overall user experience.

Here are some of the critical steps involved in prompt engineering:

1. First, define the problem: The first step in prompt engineering is defining the problem you want to solve. This involves identifying the user's needs, the information required, and the expected outcome.
    
2. Choose the suitable model: Once you have identified the problem, you must choose the suitable NLP model for your application. This involves selecting a pre-trained language model, such as GPT-3, BERT, or T5, or building a custom model for your specific needs.
    
3. Design the prompt: The next step is to design the prompt. This involves crafting a question or a statement that prompts the model to generate the desired output. A good prompt should be clear, concise, and relevant to the problem you are trying to solve.
    
4. Test and refine: After designing the prompt, you must test it on the model and evaluate the output. If the work is unsatisfactory, refine the prompt and try again until you get the desired result.
    

There are different types of prompts that you can use in prompt engineering. Here are some of the most common types:

1. Generative prompts are designed to generate new content, such as text or images. Generative prompts are helpful in creative writing, image generation, and content creation.
    
2. Retrieval prompts are designed to retrieve specific information from a database or knowledge graph. Retrieval prompts are helpful in applications such as search engines, recommendation systems, and knowledge management systems.
    
3. Question-answering prompts: These prompts are designed to answer the user's specific questions. Question-answering prompts are helpful in applications such as chatbots, virtual assistants, and customer support systems.
    

Other than these, many advanced prompting techniques have been designed to improve performance on complex tasks. Which can be divided as:

1. Few-shot prompts:
    
    1. Few-shot prompting allows us to provide exemplars in prompts to steer the model toward better performance
        
    2. ![a screen shot of a text message with numbers in it](https://cdn.hashnode.com/res/hashnode/image/upload/v1677467818862/aa3ca314-d362-4b4a-a70f-a0ebd064b35d.png align="center")
        
2. Chain-of-thought (CoT) prompting:
    
    1. Prompting can be further improved by instructing the model to reason about the task when responding. This is very useful for jobs that require reasoning. You can combine it with few-shot prompting to get better results.
        
    2. You can also do zero-shot CoT where exemplars are not available.
        
    3. ![CoT prompting](https://cdn.hashnode.com/res/hashnode/image/upload/v1677468052385/6a843170-0654-44a6-b5fa-cf73b6e6ace0.png align="center")
        
        Chain-of-thought prompting enables large language models to tackle complex arithmetic, commonsense, and symbolic reasoning tasks. Chain-of-thought reasoning processes are highlighted.
        
3. Self-Consistency:
    
    1. Self-Consistency aims to improve on the naive greedy decoding used in chain-of-thought prompting.
        
    2. The idea is to sample multiple, diverse reasoning paths through few-shot CoT and use the generations to select the most consistent answer.
        
    3. This helps to boost the performance of CoT prompting on tasks involving arithmetic and commonsense reasoning.
        
    4. ![a computer screen showing a text message that reads, when i was 6 my sister](https://cdn.hashnode.com/res/hashnode/image/upload/v1677471207737/1371559f-288d-4650-adbe-b1e0b8b2c092.png align="center")
        
        ![a screen shot of a text message](https://cdn.hashnode.com/res/hashnode/image/upload/v1677471998179/b8a96691-244b-4ea0-a487-a31c85eeb92e.png align="center")
        
4. Knowledge Generation Prompting:
    
    1. This technique involves using additional knowledge provided as part of the context to improve results on complex tasks such as commonsense reasoning.
        
    2. Incorporating external knowledge benefits commonsense reasoning while maintaining the flexibility of pre-trained sequence models.
        
    3. Generated knowledge prompting is a simple yet effective method that improves the performance of large-scale language models on four commonsense reasoning tasks without requiring task-specific supervision for knowledge integration or access to a structured knowledge base.
        
    4. It generated knowledge prompting highlighting large-scale language models as flexible sources of external expertise for improving commonsense reasoning.
        
    5. The knowledge used in the context is generated by a model and used in the prompt to make a prediction
        
        • Highest-confidence prediction is used
        
    6. ![a diagram of a class diagram](https://cdn.hashnode.com/res/hashnode/image/upload/v1677472414752/33f84af7-9632-4887-9729-eda7df8e30d7.png align="center")
        
        Generated knowledge prompting involves (a) using few-shot demonstrations to generate question-related knowledge statements from a language model; (b) using a second language model to make predictions with each knowledge statement, and then selecting the highest-confidence prediction.
        
    7. Generated knowledge prompting relies on external sources of information, while chain of thought prompting relies on internal associations and connections.
        
    8. The first step is to generate knowledge. Below is an example of how to generate the knowledge samples:
        
    9. ![a screen shot of a text message](https://cdn.hashnode.com/res/hashnode/image/upload/v1677472837399/b8e60ca4-9f3f-4114-81b6-4e196d3f2c2c.png align="center")
        
        The knowledge samples are then used to create knowledge-augmented questions to get answer proposals. The highest-confidence response is selected as the final answer:
        
    10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677472897368/295b674f-3b8f-4571-99a6-736a1d6c1ab0.png align="center")
        
5. ReAct
    
    1. ReAct (Reason + Act) is a framework where LLMs are used to generate both reasoning traces and task-specific actions in an interleaved manner.
        
        1. Generating reasoning traces allows the model to induce, track, update action plans, and even handle exceptions.
            
        2. The action step allows us to interface with and gather information from external sources such as knowledge bases or environments. ReAct will enable LLMs to interact with external tools to retrieve additional information, leading to more reliable and factual responses.
            
    2. ReAct interleaves reasoning and acting to allow for greater synergy between the two.
        
    3. Reasoning traces help the model induces, track, and update action plans and handle exceptions, while actions allow it to interface with external sources to gather additional information.
        
    4. ReAct outperforms state-of-the-art baselines on various language and decision-making tasks and generates human-like task-solving.
        
    5. ReAct improves human interpretability and trustworthiness over methods without reasoning or acting components.
        
    6. ![a screen shot of a computer screen with a text description](https://cdn.hashnode.com/res/hashnode/image/upload/v1677473335296/b17d32bc-0c0d-4f1a-a092-86fd239e2e21.png align="center")
        

In conclusion, prompt engineering is an essential technique in NLP that can help developers create more accurate and effective AI models. By following the key steps involved in prompt engineering and using the appropriate types of prompts, developers can design models that meet the needs of their users and provide a better overall user experience.

### References:

* [Prompt Engineering Lectures](https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/lecture/Prompt-Engineering-Lecture-Elvis.pdf)
    
* [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/pdf/2201.11903.pdf)
    
* [Large Language Models are Zero-Shot Reasoners](https://arxiv.org/abs/2205.11916)
    
* [Generated Knowledge Prompting for Commonsense Reasoning](https://arxiv.org/pdf/2110.08387.pdf)
    
* [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/pdf/2210.03629.pdf)