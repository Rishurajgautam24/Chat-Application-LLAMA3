# Helpful Assistant Chat Application

This project is a GUI-based chat application designed to assist users with queries. It uses the Streamlit framework and leverages the LLama3 Model from Ollama. The assistant responds to user queries by utilizing the `Ollama3` LLM model.

## Features

- User-friendly interface using Streamlit
- Utilizes advanced language model (Ollama Llama3)
- Environment variables management using dotenv

## Installation

1. **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2. **Create and activate a virtual environment (optional but recommended):**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install the required dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Set up environment variables:**

    Create a `.env` file in the project root and add your LangChain API key:

    ```bash
    LANGCHAIN_API_KEY=your_langchain_api_key
    ```

## Usage

1. **Run the Streamlit application:**

    ```bash
    streamlit run app.py
    ```

2. **Interact with the assistant:**

    Open your web browser and go to `http://localhost:8501`. You can type your queries into the input box and the assistant will respond accordingly.

## Code Overview

- **`app.py`**: Main file to run the Streamlit application.

## Example

Here's a brief overview of how the assistant works:

1. **Prompt Template:**

    ```python
    from langchain_core.prompts import ChatPromptTemplate
    prompt = ChatPromptTemplate.from_messages(
        [
            ("system", "You are a helpful assistant. Please respond to the user queries"),
            ("user", "Question:{question}")
        ]
    )
    ```

2. **Streamlit Framework:**

    ```python
    import streamlit as st

    st.title('YOUR HELPFUL ASSISTANT')
    input_text = st.text_input("How can I help you?")
    ```

3. **Ollama Llama3 LLM:**

    ```python
    from langchain_community.llms import Ollama
    llm = Ollama(model="llama3")
    output_parser = StrOutputParser()
    chain = prompt | llm | output_parser

    if input_text:
        st.write(chain.invoke({"question": input_text}))
    ```

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss your ideas.


