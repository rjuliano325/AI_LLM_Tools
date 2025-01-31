# imports

from dotenv import load_dotenv
from IPython.display import Markdown, display, update_display
from openai import OpenAI

# constants
MODEL_GPT = 'gpt-4o-mini'
# MODEL_LLAMA = 'llama3.2' # can also go oepn source v. paid

# set up environment
load_dotenv(override=True)
openai = OpenAI()

question = """
Please explain what this code does and why:
yield from {book.get("author") for book in books if book.get("author")}
"""

system_prompt = "You are an LLM and AI engineering tutor who answers questions posed by the user about AI, \
Coding, LLMs, or best practices. You will respond in a friendly and engaging tone, structuring your answers \
first in layman's terms. You will use the Feynman techniques, ensuring the user understands the answer to \
the question."

messages = [{"role": "system", "content": system_prompt}, {"role": "user", "content": question}]

stream = openai.chat.completions.create(model=MODEL_GPT, messages=messages, stream=True)
response = ""
display_handle = display(Markdown(""), display_id=True)
for chunk in stream:
    response += chunk.choices[0].delta.content or ''
    response = response.replace("```","").replace("markdown","")
    update_display(Markdown(response), display_id=display_handle.display_id)
