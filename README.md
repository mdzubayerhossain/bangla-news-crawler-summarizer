# Bengali News Scraper and Summarizer

A Python-based tool that automatically scrapes news articles from Prothom Alo (a leading Bengali newspaper), generates summaries using a BERT-based RAG approach, and stores the data for further analysis.

## Features

- **Automated Web Scraping**: Periodically crawls the Prothom Alo website to gather fresh news articles
- **Content Extraction**: Extracts article title, full content, publication date, and featured images
- **AI-Powered Summarization**: Uses a BERT-based Retrieval-Augmented Generation (RAG) approach to create concise summaries of Bengali news articles
- **Duplicate Prevention**: Tracks already processed articles to avoid duplicates
- **Structured Data Storage**: Saves all data in CSV format with daily timestamps

## Requirements

- Python 3.7+
- Required Python packages:
  - requests
  - beautifulsoup4
  - pandas
  - torch
  - transformers
  - numpy
  - scikit-learn
  - re
  - csv
  - time
  - os
  - datetime

## Installation

1. Clone this repository
```bash
git clone https://github.com/mdzubayerhossain/bangla-news-crawler-summarizer
cd bengali-news-scraper
```

2. Install required packages
```bash
pip install -r requirements.txt
```

3. Create a `requirements.txt` file with the following dependencies:
```
requests>=2.25.1
beautifulsoup4>=4.9.3
pandas>=1.2.4
torch>=1.9.0
transformers>=4.8.2
numpy>=1.20.3
scikit-learn>=0.24.2
```

## Usage

Run the main script to start the scraper and summarizer:

```bash
python scraper.py
```

The program will:
1. Load the multilingual BERT model for Bengali text embedding
2. Start a continuous scraping cycle with 10-minute intervals
3. Extract news articles from various categories (bangladesh, world, economy, sports, etc.)
4. Generate AI-powered summaries using a RAG approach
5. Save the data to CSV files in the `data` directory

Press Ctrl+C to stop the program.

## How It Works

### Scraping Process
- The script accesses the Prothom Alo homepage and extracts article links from major categories
- For each new article, it extracts the title, content, publication date, and image URL
- All extracted data is saved to a date-stamped CSV file

### Summarization Approach
The project uses a Retrieval-Augmented Generation (RAG) inspired approach:
1. Text is split into sentences using Bengali-specific sentence boundary detection
2. BERT embeddings are generated for each sentence
3. Sentence centrality is calculated using cosine similarity
4. The most representative sentences are selected and combined to form a summary
5. Original sentence order is preserved in the final summary

### Data Storage
- Articles are saved in CSV files with daily timestamps (`data/prothom_alo_with_summaries_YYYYMMDD.csv`)
- A history file (`data/article_history.txt`) tracks processed URLs to prevent duplicates

## Output Format

The CSV output includes:
- `title`: Article title
- `full_content`: Complete article text
- `rag_summary`: AI-generated summary
- `image_url`: URL of the main article image
- `article_url`: Original article URL
- `published_at`: Publication timestamp
- `scraped_at`: Scraping timestamp

## Notes

- The script includes random delays between requests to avoid overloading the target website
- Error handling is implemented to ensure the program continues running even if individual article processing fails
- The multilingual BERT model supports Bengali language processing

## Ethical Considerations

This tool is designed for research and personal use only. Please:
- Respect the terms of service of the Prothom Alo website
- Consider the server load impact of your scraping activities
- Do not redistribute copyrighted content without permission
- Use the generated summaries in accordance with fair use principles

## License

MIT
