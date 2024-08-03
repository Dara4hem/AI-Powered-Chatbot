# AI-Powered Chatbot

This AI-Powered Chatbot leverages the `DialoGPT-large` model from Hugging Face to engage in conversations. It can generate human-like responses to user inputs, making it ideal for interactive applications.

## Description

The chatbot is built using the Hugging Face `transformers` library and utilizes `Gradio` for creating a user-friendly web interface. It generates responses based on the input text provided by the user.

## Files

- `app.py`: Contains the code for initializing the chatbot and setting up the Gradio interface.
- `requirements.txt`: Lists the necessary Python libraries required to run the chatbot.

## Setup Instructions

To run the chatbot locally or on a platform like Google Colab, follow these steps:

1. **Install Required Libraries**

   Ensure you have the required libraries installed. You can install them using:

   ```sh
   pip install transformers torch gradio
   ```

2. **Run the Chatbot Script**

   Create a file named `app.py` and add the following code:

   ```python
   from transformers import pipeline
   import gradio as gr

   # Initialize the chatbot pipeline
   chatbot = pipeline('text-generation', model='microsoft/DialoGPT-large')

   def chat_with_bot(user_input):
       # Generate a response from the chatbot
       response = chatbot(user_input, max_length=100, num_return_sequences=1)
       return response[0]['generated_text']

   # Short description for the chatbot
   description = """
   ## AI-Powered Chatbot
   This chatbot leverages the DialoGPT-large model from Hugging Face to engage in conversations. 
   Enter your message in the text box below and the AI will respond. 
   """

   # Define the Gradio interface
   interface = gr.Interface(
       fn=chat_with_bot,
       inputs=gr.Textbox(lines=2, placeholder="Type your message here..."),
       outputs=gr.Textbox(),
       title="AI-Powered Chatbot",
       description=description
   )

   # Launch the interface
   interface.launch(share=True)
   ```

3. **Create `requirements.txt`**

   Create a file named `requirements.txt` and add the following content:

   ```plaintext
   gradio
   transformers
   torch
   ```

4. **Run the Application**

   If running locally, execute the following command in your terminal:

   ```sh
   python app.py
   ```

   If using Google Colab, simply run the script in a Colab cell.

## Deploy to Hugging Face Spaces

To deploy the chatbot on Hugging Face Spaces:

1. **Prepare Your Files**

   Ensure you have `app.py` and `requirements.txt` ready.

2. **Upload Files**

   Upload `app.py` and `requirements.txt` to your Hugging Face Space repository.

3. **Build and Deploy**

   Hugging Face Spaces will automatically build and deploy your application. Access your chatbot using the Space URL provided by Hugging Face.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

