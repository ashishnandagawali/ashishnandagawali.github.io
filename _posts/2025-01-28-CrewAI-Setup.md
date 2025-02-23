---
layout: post
title: CrewAI Installation Using Anaconda
date: 2025-01-28 20:00:00
description: This blog post describes CrewAI Installation Using Anaconda
tags: CrewAI Installation, Anaconda
categories: CrewAI
featured: false
---
In this article CrewAI Installation Using Anaconda.

1. Install anaconda from https://www.anaconda.com/download.
2. Start powershell from anaconda folder 
    <div class="row mt-3">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid loading="eager" path="assets/img/crewai-setup/Start-Menu-Ananconda-Powershell.png" class="img-fluid rounded z-depth-1" zoomable=true %}
        </div>
    </div>
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
