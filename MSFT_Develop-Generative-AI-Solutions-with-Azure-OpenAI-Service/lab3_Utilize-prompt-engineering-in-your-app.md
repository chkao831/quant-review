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


## Chat session
see https://microsoftlearning.github.io/mslearn-openai/Instructions/Exercises/03-prompt-engineering.html

## Visual Studio
```
.
└── mslearn-openai/
    └── Labfiles/
        └── 03-prompt-engineering/
            ├── CSharp
            ├── Python/
            │   ├── .env
            │   └── prompt-engineering.py
            └── prompts/
                ├── basic.txt
                ├── email-format.txt
                ├── specify-content.txt
                └── specify-tone.txt
```
- `prompts/basic.txt`
  ```
  System:You are an AI assistant
  Prompt:Write an intro for a new wildlife Rescue
  ```
- `prompts/email-format.txt`
  ```
  System:You are an AI assistant helping to write emails
  Prompt:Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants - Call for donations to be given at our website
  ```
- `prompts/specify-content.txt`
  ```
  System:You are an AI assistant helping to write emails
  Prompt:Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants, as well as zebras and giraffes - Call for donations to be given at our website \n\n Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits.
  ```
- `prompts/specify-tone.txt`
  ```
  System:You are an AI assistant that helps write promotional emails to generate interest in a new business. Your tone is light, chit-chat oriented and you always include at least two jokes
  Prompt:Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants, as well as zebras and giraffes - Call for donations to be given at our website \n\n Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits.

  ```

- `prompt-engineering.py`
  ```python3
  import os
  from dotenv import load_dotenv

  # Add Azure OpenAI package
  from openai import AzureOpenAI

  # Set to True to print the full response from OpenAI for each call
  printFullResponse = False

  def main():
      try:
          # Get configuration settings
          load_dotenv()
          azure_oai_endpoint = os.getenv("AZURE_OAI_ENDPOINT")
          azure_oai_key = os.getenv("AZURE_OAI_KEY")
          azure_oai_model = os.getenv("AZURE_OAI_MODEL")

          # Configure the Azure OpenAI client
          client = AzureOpenAI(
              azure_endpoint = azure_oai_endpoint,
              api_key=azure_oai_key,
              api_version="2023-05-15"
          )

          while True:
              print('1: Basic prompt (no prompt engineering)\n' +
                    '2: Prompt with email formatting and basic system message\n' +
                    '3: Prompt with formatting and specifying content\n' +
                    '4: Prompt adjusting system message to be light and use jokes\n' +
                    '\'quit\' to exit the program\n')
              command = input('Enter a number:')
              if command == '1':
                  call_openai_model(messages="../prompts/basic.txt", model=azure_oai_model, client=client)
              elif command =='2':
                  call_openai_model(messages="../prompts/email-format.txt", model=azure_oai_model, client=client)
              elif command =='3':
                  call_openai_model(messages="../prompts/specify-content.txt", model=azure_oai_model, client=client)
              elif command =='4':
                  call_openai_model(messages="../prompts/specify-tone.txt", model=azure_oai_model, client=client)
              elif command.lower() == 'quit':
                  print('Exiting program...')
                  break
              else:
                  print("Invalid input. Please try again.")
        except Exception as ex:
          print(ex)

      def call_openai_model(messages, model, client):
          # In this sample, each file contains both the system and user messages
          # First, read them into variables, strip whitespace, then build the messages array
          file = open(file=messages, encoding="utf8")
          system_message = file.readline().split(':', 1)[1].strip()
          user_message = file.readline().split(':', 1)[1].strip()

          # Print the messages to the console
          print("System message: " + system_message)
          print("User message: " + user_message)

          # Format and send the request to the model
          messages =[
              {"role": "system", "content": system_message},
              {"role": "user", "content": user_message},
          ]   

          # Call the Azure OpenAI model
          response = client.chat.completions.create(
              model=model,
              messages=messages,
              temperature=0.7,
              max_tokens=800
          )

          if printFullResponse:
              print(response)
          print("Completion: \n\n" + response.choices[0].message.content + "\n")

  if __name__ == '__main__':
      main()
  ```

Output
```bash
PS C:\Users\Student\mslearn-openai\Labfiles\03-prompt-engineering\Python> python prompt-engineering.py
1: Basic prompt (no prompt engineering)
2: Prompt with email formatting and basic system message
3: Prompt with formatting and specifying content
4: Prompt adjusting system message to be light and use jokes
'quit' to exit the program

Enter a number:1
System message: You are an AI assistant
User message: Write an intro for a new wildlife Rescue
Completion: 

Welcome to the exciting world of wildlife rescue! We are thrilled to introduce you to our brand new wildlife rescue center, where we are dedicated to the well-being and preservation of Earth's diverse wildlife populations. Our mission is to provide a safe haven for injured, orphaned, and displaced animals, while also working towards their rehabilitation and release back into their natural habitats. With a team of passionate and experienced wildlife experts, we strive to make a positive impact on the lives of these incredible creatures, and in turn, contribute to the overall conservation efforts worldwide. Join us on this incredible journey as we work tirelessly to protect and nurture our precious wildlife for generations to come.

1: Basic prompt (no prompt engineering)
2: Prompt with email formatting and basic system message
3: Prompt with formatting and specifying content
4: Prompt adjusting system message to be light and use jokes
'quit' to exit the program

Enter a number:2
System message: You are an AI assistant helping to write emails
User message: Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants - Call for donations to be given at our website
Completion: 

Subject: Introducing Contoso: A New Wildlife Rescue Dedicated to Elephant Conservation

Dear [Recipient's Name],

We hope this email finds you well and filled with enthusiasm for wildlife conservation. We are excited to introduce Contoso, a new wildlife rescue organization that is committed to protecting and preserving elephants in their natural habitats.       

At Contoso, we recognize the urgent need to safeguard these majestic creatures from the multiple threats they face today. With your support, we aim to make a significant difference in the lives of elephants, ensuring their survival for generations to come.

Why Choose Contoso?

Contoso specializes in elephants, dedicating all our resources and expertise to their protection and well-being. Our team of passionate wildlife experts, veterinarians, and conservationists work tirelessly to provide the best care for elephants in need. From rescuing injured and orphaned elephants to rehabilitating them and releasing them back into the wild, every step we take is guided by our commitment to their welfare.

How You Can Help

We invite you to join us in our mission to save and protect elephants. Your generous donations play a crucial role in funding our operations and allowing us to continue our vital work. By contributing to Contoso, you are directly making a difference in the lives of these remarkable animals.

To make a donation, please visit our website [insert website URL]. Your support, no matter the amount, will enable us to provide necessary medical care, nutrition, and habitat preservation for elephants in need. Together, we can create a better future for these incredible creatures.

Stay Updated and Engaged

We encourage you to stay connected with Contoso and be a part of our journey. By subscribing to our newsletter, you will receive regular updates on our rescue efforts, inspiring success stories, and upcoming events. Our social media platforms are also a great way to stay engaged and share your love for elephants with others.

Spread the Word

Help us spread the word about Contoso and the urgent need to protect elephants. Share our mission with your friends, family, and colleagues to raise awareness about the challenges faced by these incredible creatures. Every voice matters in creating a movement that promotes elephant conservation and ensures a brighter future for them.

Thank you for taking the time to learn about Contoso and our commitment to elephant conservation. Together, we can make a significant impact and secure a thriving future for elephants.

With gratitude,

[Your Name]
[Your Position]
Contoso Wildlife Rescue
[Contact Information]

1: Basic prompt (no prompt engineering)
2: Prompt with email formatting and basic system message
3: Prompt with formatting and specifying content
4: Prompt adjusting system message to be light and use jokes
'quit' to exit the program

Enter a number:3
System message: You are an AI assistant helping to write emails
User message: Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants, as well as zebras and giraffes - Call for donations to be given at our website \n\n Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits.
Completion: 

Subject: Introducing Contoso Wildlife Rescue - Join Us in Saving Precious Lives!

Dear [Recipient's Name],

I hope this email finds you well. We are thrilled to introduce Contoso Wildlife Rescue, an organization dedicated to the preservation and protection of endangered wildlife. With a primary focus on elephants, as well as zebras and giraffes, we are committed to providing a safe haven for these magnificent creatures.

At Contoso Wildlife Rescue, we firmly believe that every life matters. With your support, we can make a significant impact on the lives of these incredible animals. Today, we are reaching out to you to ask for your generous donation, which will go directly towards the care and rehabilitation of the wildlife in our care.

Donating to Contoso Wildlife Rescue is quick and easy. Simply visit our website at [website URL] and click on the "Donate Now" button. Every contribution, no matter how big or small, makes a real difference in the lives of the animals we rescue and protect.

To give you a glimpse of the animals currently residing at Contoso Wildlife Rescue, here is a list of some of our incredible residents:

| Animal       | Species       |
|--------------|---------------|
| Elephants    | African       |
| Zebras       | Plains        |
| Giraffes     | Reticulated   |
| Gorillas     | Western Lowland   |
| Lizards      | Various       |
| Jackrabbits  | Desert       |

We are truly grateful for your consideration in supporting Contoso Wildlife Rescue. Together, we can ensure a brighter future for these majestic creatures.

Warm regards,

[Your Name]
[Your Position]
Contoso Wildlife Rescue

[Contact Information]

P.S. Remember, your donation has the power to save lives. Visit [website URL] today and make a real difference in the world of wildlife conservation. Thank you for your compassion and support!

Note: the table above may not display correctly in some email clients.

1: Basic prompt (no prompt engineering)
2: Prompt with email formatting and basic system message
3: Prompt with formatting and specifying content
4: Prompt adjusting system message to be light and use jokes
'quit' to exit the program

Enter a number:4
System message: You are an AI assistant that helps write promotional emails to generate interest in a new business. Your tone is light, chit-chat oriented and you always include at least two jokes.
User message: Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants, as well as zebras and giraffes - Call for donations to be given at our website \n\n Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits.
Completion: 

Subject: Join the Contoso Wildlife Rescue: Saving Elephants, Zebras, and Giraffes!

Hey there [First Name]!

How are you doing? I hope this email finds you in high spirits and with a big smile on your face. I'm thrilled to introduce you to the brand new Contoso Wildlife Rescue, where we're all about saving the magnificent creatures that roam our planet.    

At Contoso, we have a soft spot for elephants, zebras, and giraffes. These incredible animals deserve our love and protection, and that's exactly what we're here to do! Our dedicated team of experts is ready to provide top-notch care, medical attention, and a safe haven for these majestic beings.

But guess what? We can't do it alone! That's where you come in, [First Name]. We're calling on animal lovers like you to join our cause and help us give these amazing creatures a fighting chance. By making a donation at our website, you'll be contributing directly to the well-being and preservation of elephants, zebras, and giraffes.

Now, let's talk about the perks of supporting Contoso Wildlife Rescue. Apart from the warm and fuzzy feeling you'll get from knowing you're making a difference, we've got some exciting rewards lined up for our generous supporters. From personalized thank-you notes to exclusive behind-the-scenes tours, we want to show our gratitude in the wildest ways possible!

Oh, and speaking of wild, let me share a couple of jokes to brighten your day:

1. Why don't elephants use computers? Because they're afraid of the mouse!

2. What do you call a zebra with no stripes? A "de-brie-d" zebra!

If you're ready to embark on this incredible journey with us, simply visit our website at [website link] and make your donation today. Remember, no amount is too small. Every penny counts in the world of wildlife rescue!

Now, allow me to introduce you to some of the amazing creatures currently under our care at Contoso Wildlife Rescue:

| Animal    | Species     |
|-----------|-------------|
| Elephant  | African     |
| Zebra     | Plains      |
| Giraffe   | Reticulated |
| Gorilla   | Western     |
| Lizard    | Chameleon   |
| Jackrabbit| Desert      |

These adorable animals are just a glimpse of the wonderful beings we're working tirelessly to protect. With your support, we can continue providing them with the love, care, and attention they deserve.

Thank you for taking the time to read this email and for considering a donation to the Contoso Wildlife Rescue. Together, we can make a real difference!

Wishing you a day as amazing as a herd of elephants playing tag,

[Your Name]
Contoso Wildlife Rescue

P.S. Did you hear about the elephant who was always cool, calm, and collected? They say he had a lot of "tusk" control! 😉   

P.P.S. If you have any questions or want to learn more about our rescue, feel free to reach out. We're always here to chat about our furry, feathery, and scaly friends!

1: Basic prompt (no prompt engineering)
2: Prompt with email formatting and basic system message
3: Prompt with formatting and specifying content
4: Prompt adjusting system message to be light and use jokes
'quit' to exit the program

Enter a number:quit
Exiting program...
```
