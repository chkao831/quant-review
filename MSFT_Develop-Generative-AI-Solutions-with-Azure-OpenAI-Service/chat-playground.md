You can use the following code to start integrating your current prompt and settings into your application\
https://carolyn-kao.openai.azure.com/openai/deployments/carolyn-kao-model/chat/completions?api-version=2023-07-01-preview

Training key: FAEE79522539477F

[Launch lab 1 - Get started with Azure OpenAI Service](https://esi.learnondemand.net/Lab/63584?instructionSetLang=en&classId=590436)

```python3
#Note: The openai-python library support for Azure OpenAI is in preview.
      #Note: This code sample requires OpenAI Python library version 0.28.1 or lower.
import os
import openai

openai.api_type = "azure"
openai.api_base = "https://carolyn-kao.openai.azure.com/"
openai.api_version = "2023-07-01-preview"
openai.api_key = os.getenv("OPENAI_API_KEY")

message_text = [{"role":"system","content":"The system is an AI teacher that helps people learn about AI"},{"role":"user","content":"What are different types of artificial intelligence?"},{"role":"assistant","content":"There are three main types of artificial intelligence: Narrow or Weak AI (such as virtual assistants like Siri or Alexa, image recognition software, and spam filters), General or Strong AI (AI designed to be as intelligent as a human being. This type of AI does not currently exist and is purely theoretical), and Artificial Superintelligence (AI that is more intelligent than any human being and can perform tasks that are beyond human comprehension. This type of AI is also purely theoretical and has not yet been developed)."},{"role":"user","content":"What is artificial intelligence?"},{"role":"assistant","content":"Artificial Intelligence (AI) refers to the simulation of human intelligence in machines that are programmed to think, learn, and problem-solve like humans. AI involves the development of computer systems that can perform tasks that typically require human intelligence, such as speech recognition, decision-making, problem-solving, visual perception, and natural language understanding. AI technologies aim to replicate or exceed human capabilities in various domains, enabling machines to analyze vast amounts of data, recognize patterns, and make informed decisions or predictions. AI has applications in various fields, including healthcare, finance, transportation, gaming, and many others."},{"role":"user","content":"How is it related to machine learning?"},{"role":"assistant","content":"Machine Learning (ML) is a subset of Artificial Intelligence (AI) that focuses on the development of algorithms and models that enable machines to learn from data and improve their performance without being explicitly programmed. In other words, ML is a method or approach to achieve AI.\n\nAI encompasses a broader range of concepts and techniques beyond just machine learning. It includes various methods such as rule-based systems, expert systems, natural language processing, computer vision, and more. Machine learning, on the other hand, is a specific technique within AI that allows machines to automatically learn and improve from experience.\n\nMachine learning algorithms use data to train models and make predictions or decisions based on patterns and insights learned from that data. These models can then be used in AI systems to perform tasks such as image recognition, speech recognition, recommendation systems, and much more.\n\nIn summary, machine learning is a crucial component of AI that enables machines to learn and improve from data, contributing to the development and advancement of artificial intelligence systems."},{"role":"user","content":"Write three multiple choice questions based on the following text, indcating the correct answers.\n\nMost computer vision solutions are based on machine learning models that can be applied to visual input from cameras, videos, or images.*\n\n- Image classification involves training a machine learning model to classify images based on their contents. For example, in a traffic monitoring solution you might use an image classification model to classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and so on.*\n\n- Object detection machine learning models are trained to classify individual objects within an image, and identify their location with a bounding box. For example, a traffic monitoring solution might use object detection to identify the location of different classes of vehicle.*\n\n- Semantic segmentation is an advanced machine learning technique in which individual pixels in the image are classified according to the object to which they belong. For example, a traffic monitoring solution might overlay traffic images with \"mask\" layers to highlight different vehicles using specific colors."},{"role":"assistant","content":"1. What is the purpose of image classification in computer vision?\na) To identify the location of objects within an image\nb) To classify images based on their contents\nc) To highlight different vehicles using specific colors\nd) To classify individual objects within an image\n\nCorrect answer: b) To classify images based on their contents\n\n2. What does object detection in computer vision involve?\na) Classifying individual objects within an image and identifying their location with a bounding box\nb) Overlaying traffic images with \"mask\" layers to highlight different vehicles\nc) Training a machine learning model to classify images based on their contents\nd) Identifying the location of different classes of vehicles within an image\n\nCorrect answer: a) Classifying individual objects within an image and identifying their location with a bounding box\n\n3. What is semantic segmentation in computer vision?\na) Identifying the location of different classes of vehicles within an image\nb) Classifying individual objects within an image and identifying their location with a bounding box\nc) Overlaying traffic images with \"mask\" layers to highlight different vehicles\nd) Classifying individual pixels in an image according to the object to which they belong\n\nCorrect answer: d) Classifying individual pixels in an image according to the object to which they belong"}]

completion = openai.ChatCompletion.create(
  engine="carolyn-kao-model",
  messages = message_text,
  temperature=0,
  max_tokens=500,
  top_p=0.95,
  frequency_penalty=0,
  presence_penalty=0,
  stop=None
)
```
```python3
#Note: The openai-python library support for Azure OpenAI is in preview.
      #Note: This code sample requires OpenAI Python library version 0.28.1 or lower.
import os
import openai

openai.api_type = "azure"
openai.api_base = "https://carolyn-kao.openai.azure.com/"
openai.api_version = "2023-07-01-preview"
openai.api_key = os.getenv("OPENAI_API_KEY")

message_text = [{"role":"system","content":"You are a Python developer."},{"role":"user","content":"Write a Python function named Multiply that multiplies two numeric parameters."},{"role":"assistant","content":"Here is a Python function named Multiply that multiplies two numeric parameters:\n\n```python\ndef Multiply(num1, num2):\n    result = num1 * num2\n    return result\n```\n\nYou can call this function by passing two numeric values as arguments, like this:\n\n```python\nresult = Multiply(5, 6)\nprint(result)  # Output: 30\n```"}]

completion = openai.ChatCompletion.create(
  engine="carolyn-kao-model",
  messages = message_text,
  temperature=0.5,
  max_tokens=800,
  top_p=0.95,
  frequency_penalty=0,
  presence_penalty=0,
  stop=None
)
```

```python3
#Note: The openai-python library support for Azure OpenAI is in preview.
      #Note: This code sample requires OpenAI Python library version 0.28.1 or lower.
import os
import openai

openai.api_type = "azure"
openai.api_base = "https://carolyn-kao.openai.azure.com/"
openai.api_version = "2023-07-01-preview"
openai.api_key = os.getenv("OPENAI_API_KEY")

message_text = [{"role":"system","content":"This is a text message sentiment classifier."},{"role":"user","content":"Message: \"I loved the new adventure movie!\""},{"role":"assistant","content":"Sentiment: Positive"},{"role":"user","content":"Message text\n1. \"I loved the new adventure movie!\"\n2. \"I hate it when my phone battery dies\"\n3. \"My day has been 👍\"\n4. \"This is the link to the article\"\n5. \"This new music video is unreal\""},{"role":"assistant","content":"Sentiment:\n1. Positive\n2. Negative\n3. Positive\n4. Neutral\n5. Positive"}]

completion = openai.ChatCompletion.create(
  engine="carolyn-kao-model",
  messages = message_text,
  temperature=0.5,
  max_tokens=800,
  top_p=0.95,
  frequency_penalty=0,
  presence_penalty=0,
  stop=None
)
```
```python3
#Note: The openai-python library support for Azure OpenAI is in preview.
      #Note: This code sample requires OpenAI Python library version 0.28.1 or lower.
import os
import openai

openai.api_type = "azure"
openai.api_base = "https://carolyn-kao.openai.azure.com/"
openai.api_version = "2023-07-01-preview"
openai.api_key = os.getenv("OPENAI_API_KEY")

message_text = [{"role":"system","content":"Ideas involving education and virtual reality"},{"role":"user","content":"1. Virtual Mars\nStudents get to explore Mars via virtual reality and go on missions to collect and catalog what they see.\n\n2."},{"role":"assistant","content":"Virtual Field Trips\nStudents can visit historical landmarks, museums, and natural wonders from the comfort of their classroom, enhancing their learning experience and understanding of the world.\n\n3. Virtual Science Experiments\nVirtual reality can allow students to conduct complex and potentially dangerous science experiments in a safe and controlled environment, providing hands-on learning opportunities.\n\n4. Language Immersion\nVirtual reality can create immersive language learning experiences, allowing students to practice their language skills in realistic scenarios and interact with virtual native speakers.\n\n5. Historical Reenactments\nStudents can virtually step into historical events and experience them firsthand, gaining a deeper understanding of the past and its impact on the present.\n\n6. Virtual Tutoring\nVirtual reality can provide personalized tutoring experiences, allowing students to receive one-on-one instruction and support tailored to their specific needs.\n\n7. Career Exploration\nVirtual reality can simulate different career environments, giving students the opportunity to explore various professions and make more informed decisions about their future career paths.\n\n8. Cultural Exchange\nStudents can virtually connect with students from different countries and cultures, fostering cross-cultural understanding and promoting global citizenship.\n\n9. Special Education Support\nVirtual reality can provide customized learning experiences for students with special needs, helping them overcome challenges and engage in interactive and inclusive learning.\n\n10. Virtual Classroom Collaboration\nVirtual reality can enable students from different locations to collaborate on projects and share ideas, fostering teamwork and enhancing their communication and problem-solving skills."}]

completion = openai.ChatCompletion.create(
  engine="carolyn-kao-model",
  messages = message_text,
  temperature=0.5,
  max_tokens=800,
  top_p=0.95,
  frequency_penalty=0,
  presence_penalty=0,
  stop=None
)
```

Note: Few-shot examples are used to provide the model with examples of the types of responses that are expected. The model will attempt to reflect the tone and style of the examples in its own responses.


Probability settings: If you're asking for a response where there's only one right answer, you should specify lower values for these settings. If you're looking for a response that's not obvious, you might want to use higher values. 

- Temperature: controls the degree to which response generation includes an element of randomness. The value of 0 used in your submission minimizes randomness, resulting in stable, predictable responses.
- Top P
