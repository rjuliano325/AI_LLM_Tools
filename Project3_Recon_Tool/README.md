# Website Reconnaissance Tool

This script is a web scraping and analysis tool that extracts website content, identifies relevant links, and utilizes OpenAI's API to categorize and analyze the extracted data. It is designed to aid in reconnaissance by automating the process of gathering information from a given website.

## Features

- Scrapes website content and links using requests and BeautifulSoup
- Identifies relevant links such as About pages, Careers pages, and Company pages
- Uses OpenAI's GPT-4o-mini model to process and analyze web data
- Supports real-time streaming for continuous response updates
- Handles common web scraping obstacles, such as removing unnecessary elements (scripts, styles, images, etc.)

## Installation

### Prerequisites

- Python 3.8+
- OpenAI API key
- Required Python packages (see requirements.txt)

### Setup Instructions

1. Clone the repository:
   git clone https://github.com/your-repo-name.git
   cd your-repo-name

2. Install dependencies:
   pip install -r requirements.txt

3. Create a .env file in the root directory and add your OpenAI API key:
   OPENAI_API_KEY=your-api-key-here

## Usage

### Extracting Links from a Website

To analyze a website and retrieve relevant links:

from scraper import get_links

url = "https://example.com"
links = get_links(url)
print(links)

### Performing Website Reconnaissance

To retrieve structured reconnaissance data from a website:

from scraper import ws_recon

company_name = "ExampleCorp"
url = "https://example.com"
ws_recon(company_name, url)

### Streaming Reconnaissance (Live Updates)

To stream the extraction process and receive continuous updates:

from scraper import stream_ws_recon

company_name = "ExampleCorp"
url = "https://example.com"
stream_ws_recon(company_name, url)

## Configuration

- Model Used: gpt-4o-mini
- Headers: Uses a custom User-Agent header to avoid basic bot detection.
- Filtered Elements: Automatically removes <script>, <style>, <img>, and <input> tags to extract clean text.

## Notes

- Ensure your OpenAI API key is valid and properly set in the .env file.
- This tool is intended for legal and ethical reconnaissance only. Always adhere to a website's robots.txt policy.
- Avoid scraping websites that explicitly prohibit automated access in their terms of service.
