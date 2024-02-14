- In visual studio, clone `https://github.com/MicrosoftLearning/mslearn-openai`

```
.
└── mslearn-openai/
    └── Labfiles/
        └── 02-nlp-azure-openai/
            ├── CSharp
            ├── Python/
            │   ├── .env
            │   └── test-openai-model.py
            └── text-files/
                └── sample-text.txt
```

- `pip install openai==1.2.0`
- in `.env`, update
  ```
  AZURE_OAI_ENDPOINT=https://carolyn-kao-lab2.openai.azure.com/
  AZURE_OAI_KEY=764508ea6f3640b295327bd0c821fc96
  AZURE_OAI_MODEL=carolynkao-lab2
  ```
- `test-openai-model.py`
  ```python3
  import os
  from dotenv import load_dotenv

  # Add Azure OpenAI package
  from openai import AzureOpenAI

  def main():
      try:
          # Get configuration settings
          load_dotenv()
          azure_oai_endpoint = os.getenv("AZURE_OAI_ENDPOINT")
          azure_oai_key = os.getenv("AZURE_OAI_KEY")
          azure_oai_model = os.getenv("AZURE_OAI_MODEL")
    
          # Read text from file
          text = open(file="../text-files/sample-text.txt", encoding="utf8").read()
          print("\nSending request for summary to Azure OpenAI endpoint...\n\n")
    
          # Add code to build request...
          # Initialize the Azure OpenAI client
          client = AzureOpenAI(
              azure_endpoint = azure_oai_endpoint,
              api_key=azure_oai_key,
              api_version="2023-05-15"
          )
    
          # Send request to Azure OpenAI model
          response = client.chat.completions.create(
          model=azure_oai_model,
          temperature=1.0, # 0.7; Increasing the temperature often causes the summary to vary, even when provided the same text, due to the increased randomness. You can run it several times to see how the output may change. Try using different values for your temperature with the same input.
          max_tokens=120,
          messages=[
              {"role": "system", "content": "You are a helpful assistant."},
              {"role": "user", "content": "Summarize the following text in 20 words or less:\n" + text}
          ]
          )
          print("Summary: " + response.choices[0].message.content + "\n")

      except Exception as ex:
        print(ex)

  if __name__ == '__main__':
      main()
  ```
- `sample-text.txt`: This text file contains the text you will submit to the model to be summarized.
  ```
  The process of making maple syrup begins by tapping a spout (sometimes called a spile) into the sugar maple tree. The spile is inserted into the tree about 2 inches deep and the sap is collected as it flows out. The sap is then taken to a sugar shack where it is boiled down to concentrate the sugars. As the sap boils, water in the sap is evaporated and the syrup becomes more and more thick. Once the syrup reaches the right sugar content, which is usually when the boiling point reaches 219 degrees Fahrenheit, it is bottled and enjoyed.
  ```

```bash
PS C:\Users\Student\mslearn-openai\Labfiles\02-nlp-azure-openai\Python> python test-openai-model.py

Sending request for summary to Azure OpenAI endpoint...


Summary: Maple syrup is made by tapping a spout into a sugar maple tree, collecting sap, boiling it down, and bottling it.

PS C:\Users\Student\mslearn-openai\Labfiles\02-nlp-azure-openai\Python> python test-openai-model.py

Sending request for summary to Azure OpenAI endpoint...


Summary: Maple syrup is made by tapping a spout into a sugar maple tree to collect sap, which is then boiled down and bottled.

PS C:\Users\Student\mslearn-openai\Labfiles\02-nlp-azure-openai\Python> python test-openai-model.py

Sending request for summary to Azure OpenAI endpoint...


Summary: Maple syrup is made by tapping a spout into a sugar maple tree to collect sap, which is then boiled and bottled.
```
