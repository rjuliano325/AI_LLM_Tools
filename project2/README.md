# Website Summarizer with Ollama

## Overview

This program contains a Python script for extracting and summarizing website content using the Ollama local model. The script scrapes a given URL, removes unnecessary elements, and generates a concise summary of the webpage.

## Features

**Web scraping** using requests and BeautifulSoup.

**Customizable system prompt** for precise summarization.

**Integration with Ollama** for AI-driven summarization.

**Markdown-formatted output** for better readability.

## Requirements

Before running the script, ensure you have the following installed:

Python 3.8+

ollama for AI summarization.

requests for fetching webpage content.

beautifulsoup4 for parsing HTML.

Jupyter Notebook (if using interactive markdown output).

Install dependencies using:

```bash
pip install requests beautifulsoup4 ollama
```

## Setup

**Clone the Repository:**

```bash
git clone https://github.com/yourusername/website-summarizer.git
cd website-summarizer
```

**Run the Script:**

```bash
python summarize.py
```
*(Alternatively, execute the script in a Jupyter Notebook environment for interactive markdown output.)*

## Code Explanation

The script performs the following operations:

Initializes a Website object to extract relevant text from a given URL.

Uses BeautifulSoup to remove non-text elements like scripts and images.

Generates a structured AI prompt for summarization.

Sends the processed content to Ollama's local AI model.

Outputs the AI-generated summary in markdown format.

### Key Code Snippets

#### Website Class

```python
class Website:
def init(self, url):
"""
Initialize Website object to scrape and process content from a URL
"""
self.url = url
response = requests.get(url, headers=headers)
soup = BeautifulSoup(response.content, 'html.parser')
self.title = soup.title.string if soup.title else "No title found"
for tag in soup.body(["script", "style", "img", "input"]):
tag.decompose()
self.text = soup.body.get_text(separator="\n", strip=True)
```

The Website class fetches and cleans webpage content for processing.

#### AI Summarization

```python
def summarize_with_ollama(url):
"""
Generate a summary for a given URL using the Ollama local model.
"""
website = Website(url)
messages = messages_for(website)
response = ollama.chat(model="llama3.2", messages=messages)
return response['message']['content']
```

This function sends the cleaned webpage text to the AI model for summarization.

## Customization

**Modify the System Prompt:** Change the system_prompt variable to adjust the summarization style.

**Use a Different AI Model:** Replace llama3.2 with another supported model in Ollama.

**Adjust Output Formatting:** Modify the display_summary_with_ollama function for different output styles.

## Contributing

Feel free to submit pull requests or report issues. Let’s improve and expand this project together!
