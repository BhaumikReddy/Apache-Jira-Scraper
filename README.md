# S V Sai Bhaumik Reddy - E22CSEU0682 - Bennett University
# Apache JIRA Scraper

A simple tool to scrape and process issues from Apache's public JIRA instance.

## Features

- Scrapes issues and comments from Apache JIRA projects
- Handles pagination automatically
- Built-in rate limiting to avoid overwhelming the server
- Saves raw JSON data for each issue
- Cleans and transforms text data (removes HTML, normalizes whitespace)
- Resumable: remembers which issues have been processed

## Setup

1. Make sure you have Python installed

2. Install dependencies:

```bash
pip install -r requirements.txt
```

## Usage

Run with default projects (TIKA, ZOOKEEPER, OPENNLP):

```bash
python main.py
```

Run with specific projects:

```bash
python main.py --projects HADOOP SPARK KAFKA
```

Transform existing data without scraping:

```bash
python main.py --transform-only
```

## Output

The script creates two types of output:

1. Raw data: `data/raw/<PROJECT>/<ISSUE>.json`
   - Contains complete JSON data for each issue
   - Organized by project folders

2. Processed data: `data/train.jsonl`
   - One JSON object per line
   - Contains cleaned and transformed issue data
   - Includes: key, summary, description, status, comments

## Project Structure

- `main.py` - Main script to run
- `jira_scraper.py` - Handles JIRA API interaction
- `text_utils.py` - Text cleaning and transformation
- `config.py` - Configuration and constants