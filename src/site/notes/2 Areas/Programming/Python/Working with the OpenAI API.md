---
{"dg-publish":true,"permalink":"/2-areas/programming/python/working-with-the-open-ai-api/","created":"2025-09-27T13:33:35.114+07:00","updated":"2025-09-27T16:40:37.363+07:00"}
---


## Introduction
API = Application Programming Interface
- For sending Request and receiving response
OpenAI API
- Can specify model, data and parameters
- Used to integrate AI into products as it work with model programmatically
- Does not require computational power.

## Making Request
OpenAI has many API Endpoints
- Authentication: Unique key
- Usage Costs: depend on model request and size of model input / output
- Creating an API key -> API keys page and create a secret key

OpenAI has own python lbirary called `OpenAI`
- We create client to configurate environment for the OpenAI API, inside this add an api key `client = OpenAI(api_key=".....")`
- We use `response = client.chat.completions.create(model="gpt-4o-mini",messages=[{"role:"user","content": "ADD PROMPT HERE"}])` to send response and receive the response. Role = user is used for sending prompt and receive response.
- Response will be ChatCompletion object. Response message is stored in `choices` attribute. -> `response.choices[0]` -> access `message` attribute and then `content` attribute (`response.choices[0].message.content`)

You can use `"""` triple quotes to define multi-line prompt for ease of readability and processing
In `client.chat.completions.create`, specify argument `max_completion_tokens` to specify limit of the response (upper limit)

Cost depend on model and token size
Use `response.usage.prompt_tokens` for input token
Output tokens were mostly assumed as max_completion_tokens.

## Text Generation
Response is **non-deterministic** (inherently random)
Use `temperature` parameter to determine **determinism** (0 = highly deterministic, 2 = very random)
Providing an example can help with the uncertainty / randomness. (This technique called **shot prompting**)

## Shot Prompting
- Zero-shot: no examples just insturction
- One-shot: one example guides the response
- Few-shot: multiple examples provide more context
Use case text classification, sentiment analysis to identify opinions or emotion, data extraction, General categorization
**Adding an example to a role: user work for pattern completion BUT not for the instruction following or real conversation tasks (user + assistant should be used instead.)**


## Single-turn tasks / Multi-turn conversation
![Working with the OpenAI API.png|500](/img/user/3%20Resources/Attachment/Working%20with%20the%20OpenAI%20API.png)
Single turn tasks = One input return one output
With Chat Completion end points, you can do `Multi-turn conversation`
`Role` as stated earlier, came into play on this case.
- System = guardrails, control behavior, important template formatting
- User = instruct the assistant (context required for new input, often single-turn)
- Assistant = RESPONSE to the user instruction (example conversation) (the user-assistant is like an example of the INPUT and the example of a RESPONSE which the model can learn from.)
Add another dictionary into `messages` to provide their own role and content. 
**This can also be mitigating misuse (add guardrails)**

This is exactly what is going on with the ChatGPT. 
The response is stored into a role: assistant and send with the next role:user message (as it has access to the previous chat history!). And you can create your own chatbot (like ChatGPT) by just using LOOP

