---
layout: post
title: Deepseek API Usage with Langchain
date: 2025-02-01 20:00:00
description: This blog post describes way to connect Deepseep API using Langchain
tags: Deepseek, API, Langchain
categories: Deepseek
featured: false
---
In this article we'll see how we can use the deepseek api from Lanchain framework as per documentation provided by Deepseek.

1. Install following library. Remove single quotes in command prompt.
    ~~~python
        '!pip3 install langchain_openai'
    ~~~
2. Import BaseChatOpenAI class from the Langchain chat models 
    ~~~python
        from langchain_openai.chat_models.base import BaseChatOpenAI
    ~~~
3. Now create an BaseChatOpenAI object which will be used across our page.

    ~~~python
        llm = BaseChatOpenAI(
            model='deepseek-chat', 
            openai_api_key='<Your API Key>'
            openai_api_base='https://api.deepseek.com',
            max_tokens=1024
        )
    ~~~
4. lets give an sample prompt message to check whether the api is working fine. 
    ~~~python
        response = llm.invoke("Hi!")
        print(response.content)
    ~~~

    ~~~python
        Hello! How can I assist you today? 
    ~~~
5. lets givea proper message and see the output to ensure that API is responding as expected 

    ~~~python
        messages = [
            (
                "system",
                "You are a helpful assistant that translates English to Persian. Translate the user sentence.",
            ),
            ("human", "I love programming."),
        ]
        ai_msg = llm.invoke(messages)
        ai_msg.content
    ~~~

6. Check with complete message given to system
    ~~~python
    
        from langchain_core.prompts import ChatPromptTemplate
        
        prompt = ChatPromptTemplate(
            [
                (
                    "system",
                    "You are a helpful assistant that translates {input_language} to {output_language}.",
                ),
                ("human", "{input}"),
            ]
        )
        
        chain = prompt | llm
        chain.invoke(
            {
                "input_language": "English",
                "output_language": "German",
                "input": "I love agentic AI.",
            }
        )
    ~~~
7. Observe the output, esepcailly the KV Cache or content caching portion.
    ~~~python
        AIMessage(content='Ich liebe agentische KI.', additional_kwargs={'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 7, 'prompt_tokens': 20, 'total_tokens': 27, 'completion_tokens_details': None, 'prompt_tokens_details': {'audio_tokens': None, 'cached_tokens': 0}, 'prompt_cache_hit_tokens': 0, 'prompt_cache_miss_tokens': 20}, 'model_name': 'deepseek-chat', 'system_fingerprint': 'fp_3a5770e1b4', 'finish_reason': 'stop', 'logprobs': None}, id='run-46ca6f2a-21ef-45f4-83f6-814c07fab391-0', usage_metadata={'input_tokens': 20, 'output_tokens': 7, 'total_tokens': 27, 'input_token_details': {'cache_read': 0}, 'output_token_details': {}})
    ~~~

8. You can find working [google colab file](https://github.com/ashishnandagawali/agentic-ai/blob/0096abadca77518e8af77fa36df0cc15a64d929e/Langchain_deepseek.ipynb) in my github repo.
