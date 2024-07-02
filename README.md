# YouTube Channel Data Scraper

## Overview

This project demonstrates how to scrape data from a specific YouTube channel using the YouTube Data API. The Jupyter Notebook fetches all video names, publish dates, views, likes, and comments from the specified channel.

## Features

- Fetches video titles.
- Retrieves the publish date of each video.
- Collects the number of views, likes, and comments for each video.
- Outputs the data in a structured format (e.g., CSV).

## Prerequisites

- Python 3.x
- Jupyter Notebook
- Google API client library for Python
- YouTube Data API v3 key

## Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/addanki-virinchi/Scraping-The-Youtube-Through-Its-API.git
    cd Scraping-The-Youtube-Through-Its-API
    ```

2. **Create a virtual environment (optional but recommended):**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install the required packages:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Set up your YouTube Data API key:**

    - Go to the [Google Developers Console](https://console.developers.google.com/).
    - Create a new project.
    - Enable the YouTube Data API v3.
    - Create credentials for the API and obtain your API key.

        ```python
        API_KEY = 'YOUR_YOUTUBE_API_KEY'
        ```

## Usage

1. **Open the Jupyter Notebook:**

    ```bash
    jupyter notebook
    ```

2. **Run the Notebook:**

    - Open `ScrapeYoutube.ipynb` in the Jupyter interface.
    - Execute the cells to scrape the data.

3. **Output:**

    - The notebook will output the data to a file named `Youtube.csv`.

## Notebook Details

The main notebook, `ScrapeYoutube.ipynb`, performs the following steps:

1. **Imports necessary libraries and modules:**

    ```python
    import os
    import googleapiclient.discovery
    import pandas as pd
    from config import API_KEY
    ```

2. **Initializes the YouTube Data API client:**

    ```python
    youtube = googleapiclient.discovery.build("youtube", "v3", developerKey=API_KEY)
    ```

3. **Fetches the channel's video data:**

    - Uses the `playlistItems` method to get video details from the channel's upload playlist.
    - Retrieves video statistics using the `videos` method.

4. **Stores the data in a structured format:**

    ```python
    data = {
        "Title": [],
        "Publish Date": [],
        "Views": [],
        "Likes": [],
        "Comments": []
    }

    # Append data to the dictionary
    ```

5. **Outputs the data to a CSV file:**

    ```python
    df = pd.DataFrame(data)
    df.to_csv('Youtube.csv', index=False)
    ```

## Example Output

The resulting `Youtube.csv` file will contain columns for the video title, publish date, views, likes, and comments.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [Google API Client Library for Python](https://github.com/googleapis/google-api-python-client)
- [YouTube Data API v3](https://developers.google.com/youtube/v3)
