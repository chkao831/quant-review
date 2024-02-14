What is prompt Engineering?

  Constructing prompts to:
  - maximize relevancy and accuracy of completions
  - specify formatting and style of completions
  - provide conversational context
  - mitigate bias and improve fairness
    
Primary, supporting and grounding content
- Primary content = something to be summarized, traslated, etc.
- Supporting content = to provide clarity / specificity
- Grounding content = to define scrope for questions¸›Í
- section markers: --- or ###

Zero-shot (no example) vs. few-shot
- Few-shot: refers to a scenario where the model is provided with only a few examples (shots) of each class or task during the training phase.
- can include previous message for few-shot learning

System, user and assistant
- system message (optional) is sent every time you post to the API
  - provide a brief description to the ai role - default to be: you are a casual, helpful assistant.
- user: question
- assistant: answer


