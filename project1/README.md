# LLM Chat Interface

## Overview

This program contains a simple yet effective Python script for interacting with language models, such as OpenAI's GPT and open-source models like LLaMA. The script streams responses from the model, providing real-time feedback, making it useful for AI engineering, coding assistance, and learning best practices in LLMs.

## Features

**Supports OpenAI GPT models** (Default: `gpt-4o-mini`).

**Customizable system prompt** for role-based AI interactions.

**Streaming responses** for real-time interaction.

**Uses `dotenv` for environment configuration** to securely load API keys.

**Displays formatted markdown responses** in an interactive environment like Jupyter Notebook.

## Requirements

Before running the script, ensure you have the following installed:

Python 3.8+

OpenAI SDK (`openai`)

`python-dotenv` (for environment variable management)

Jupyter Notebook (if using in an interactive environment)

You can install the dependencies using:

```bash
pip install openai python-dotenv jupyter
```

## Setup

**Set up API Keys:** Ensure you have an OpenAI API key and store it in a `.env` file:

```plaintext
OPENAI_API_KEY=your_api_key_here
```

**Clone the Repository:**

```bash
git clone https://github.com/yourusername/llm-chat-interface.git
cd llm-chat-interface
```

**Run the Script:**

```bash
python chat.py
```
*(Alternatively, execute the script in a Jupyter Notebook environment for interactive markdown output.)*

## Code Explanation

The script performs the following operations:

Loads environment variables using `dotenv`.

Initializes an OpenAI client.

Defines a **system prompt** for guiding the AI’s response style.

Sends a **user query** about Python generator expressions.

Streams the AI’s response dynamically, updating the output in real time.

Formats the response for better readability in markdown.

### Key Code Snippets

#### System Prompt

```python
system_prompt = "You are an LLM and AI engineering tutor who answers questions posed by the user about AI, Coding, LLMs, or best practices. You will respond in a friendly and engaging tone, structuring your answers first in layman's terms. You will use the Feynman technique, ensuring the user understands the answer to the question."
```

This ensures that responses are structured in an **educational and engaging** manner.

#### Streaming API Response

```python
stream = openai.chat.completions.create(model=MODEL_GPT, messages=messages, stream=True)
response = ""
display_handle = display(Markdown(""), display_id=True)
for chunk in stream:
response += chunk.choices[0].delta.content or ''
response = response.replace("",""").replace("markdown",""")
    update_display(Markdown(response), display_id=display_handle.display_id)
\

The AI response is streamed in real-time and displayed interactively using Jupyter’s `Markdown` renderer.

## Customization

**Switch to Open-Source Models:** Uncomment and replace `MODEL_GPT` with your desired LLaMA model.

**Modify the System Prompt:** Customize the AI’s personality and expertise by editing the `system_prompt` variable.

**Change Output Format:** Modify the `display` and `update_display` logic for different output styles.

## Contributing

Feel free to submit pull requests or report issues. Let’s improve and expand this project together!
