# ArXiv-Zotero Connector

A Python tool to automatically collect ArXiv papers and add them to your Zotero library based on specified keywords.

## Features

- Search ArXiv papers based on keywords
- Automatically create Zotero entries with full metadata
- Download PDF files and attach them to Zotero entries
- Organize papers into specific Zotero collections
- Configurable search parameters (time range, max results)
- Robust error handling and logging

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/arxiv-zotero-connector.git
cd arxiv-zotero-connector
```

2. Create and activate a virtual environment:
```bash
python -m venv .venv
# On Windows:
.\.venv\Scripts\activate
# On Unix/MacOS:
source .venv/bin/activate
```

3. Install required packages:
```bash
pip install -r requirements.txt
```

4. Set up your credentials by creating a `.env` file in the project directory:
```bash
ZOTERO_LIBRARY_ID=your_library_id
ZOTERO_API_KEY=your_api_key
COLLECTION_KEY=your_collection_key  # Optional
```
### How to get your_library_id
1. Go to https://www.zotero.org/settings/
2. Go to *Security* in the left side-bar
3. Scroll down to *Applications*
4. See the text: User ID: Your user ID for use in API calls is XXXXXX
5. XXXXXX - is your library_id

### How to get your_api_key
1. Go to https://www.zotero.org/settings/
2. Go to *Security* in the left side-bar
3. Scroll down to *Applications*
4. Press *Create new private key*
5. Name it and give it all the permissions to read and write
6. Press *Save Key*

### How to get your_collection_key
The easiest way is to:
1. Go to you web library in Zotero
2. Press on the folder in the sidebar
3. In the URL you'll see the collection key (like: XXX1XXX0)
   
## Usage

```python
from connector import ArxivZoteroCollector

# Initialize the collector
collector = ArxivZoteroCollector(
    zotero_library_id=credentials['library_id'],
    zotero_api_key=credentials['api_key'],
    collection_key=credentials['collection_key']  # Optional
)

keywords = [
    "multi-agent systems",
    "moral agents AI",
    "agent decision making"
]

successful, failed = collector.run_collection(
    keywords=keywords,
    max_results=5,
    days_back=7,
    download_pdfs=True
)
```

## Configuration Parameters

- `keywords`: List of search terms for ArXiv
- `max_results`: Maximum number of papers to process
- `days_back`: How far back to search for papers
- `download_pdfs`: Whether to download and attach PDFs

## Error Handling and Logs

Logs are stored in `zotero_collector.log` and include operation tracking, error messages, and API response information.

## License

MIT License

## Roadmap

 - Implement CRON job functionality
 - Develop intelligent paper summarization
 - Build intuitive user interface
 - Optimize Zotero storage management

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
