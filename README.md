# FileDownloaderSpider

This Scrapy spider crawls the [Quebec Geological Survey EXAMINE directory](https://gq.mines.gouv.qc.ca/documents/EXAMINE/), follows specific links starting with `DP`, and downloads files from each of those pages. Files are organized into subfolders based on the link text that led to them (e.g., `DPV940`, `DPN123`).

## Features

- Crawls only links whose text starts with **DP**
- Ignores unwanted header links like **Name**, **Last modified**, **Size**, and **Description**
- Downloads files to a structured folder (`<download_folder>/<DP_FOLDER>/`)
- Includes a `dry_run` mode for safely testing the code without downloading files
- Uses polite scraping settings (e.g., delays, user agent, autothrottle)

## Usage

### 1. Install Dependencies

This project requires Python 3 and the following packages:

```bash
pip install scrapy requests
```

### 2. Run the Spider

To start the spider:
1. Run the imports cell.
2. Input the folder path you want for your outputs in `DOWNLOAD_DIR`
3. If the folder doesn't exist, run the cell to make the folder
4. Run the cell with the `scrapy.Spider` class. If you want **to test the code** and not download any files, set `dry_run = True`
5. Run the cell with process. 

### 3. Output

Downloaded files will be saved to:

```
downloaded_files/
└── DPV940/
    ├── file1.pdf
    ├── file2.docx
└── DPN123/
    ├── file3.zip
    ...
```

Each subfolder is named after the link that led to it.

## Notes

- You can adjust the Scrapy settings (delays, user agent, etc.) inside the `CrawlerProcess()` config.
- This spider is designed to be respectful of the target server and shouldn't cause high load.