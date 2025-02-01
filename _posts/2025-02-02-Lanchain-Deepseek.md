
Deepseek API Usage with Langchain
============

In this article we'll see how we can use the deepseek api from Lanchain framework

 1. Install following librabry  - 
 ~~~python
!pip3 install langchain_openai
 ~~~

 2. Install 
 ~~~python
from langchain_openai.chat_models.base import BaseChatOpenAI
 ~~~
 3. Now create an BaseChatOpenAI object which will be used across our page.

~~~python
llm = BaseChatOpenAI(
    model='deepseek-chat', 
    openai_api_key='sk-b44fafb282f44d4f9d83f68e0f27f6e1', #api_key="sk-b44fafb282f44d4f9d83f68e0f27f6e1"
    openai_api_base='https://api.deepseek.com',
    max_tokens=1024
)
~~~

 4. lets give an trial to check whether the api is working fine. Hence sending a trivial message.
~~~python
response = llm.invoke("Hi!")
print(response.content)

Hello! How can I assist you today? 

~~~
 5. lets givea good serious message and see the output to ensure that API is working Fine

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

 5. Check with complete message given to system
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
 5. Observe the output, esepcailly the KV Cache or content caching portion.
 ***
 AIMessage(content='Ich liebe agentische KI.', additional_kwargs={'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 7, 'prompt_tokens': 20, 'total_tokens': 27, 'completion_tokens_details': None, 'prompt_tokens_details': {'audio_tokens': None, 'cached_tokens': 0}, 'prompt_cache_hit_tokens': 0, 'prompt_cache_miss_tokens': 20}, 'model_name': 'deepseek-chat', 'system_fingerprint': 'fp_3a5770e1b4', 'finish_reason': 'stop', 'logprobs': None}, id='run-46ca6f2a-21ef-45f4-83f6-814c07fab391-0', usage_metadata={'input_tokens': 20, 'output_tokens': 7, 'total_tokens': 27, 'input_token_details': {'cache_read': 0}, 'output_token_details': {}})
 ***

