# Siskel & Ebert Episode Matcher

This project scrapes and reconciles episode lists for two eras of the famous movie review show:
1.  **Siskel & Ebert**: The original run with Gene Siskel and Roger Ebert.
2.  **Ebert & Roeper**: The subsequent run with Roger Ebert and Richard Roeper.

It compares episode data from various sources (TheTVDB, an archived fan site, and a YouTube channel) to find matches, identify incomplete episodes, and generate statistics and HTML reports.

## Data Sources

- **YouTube Channel**: [The Misadventures of Siskel & Ebert](https://www.youtube.com/@TheMisadventuresofSiskelEbert/videos)
- **Website**: siskelebert.org (Note: Site is currently down, but data is archived in `data/archived_website_episodes.txt`)

## Project Structure

- `main.py`: The entry point of the application.
- `modules/`: Contains the scraping, processing, and reporting logic.
  - `names_tvdb.py`: Scrapes episode lists from TheTVDB.
  - `names_youtube.py`: Scrapes video titles from the YouTube channel.
  - `preprocessing.py`: Cleans titles and compares lists to find matches.
  - `html_writer.py`: Generates an HTML report of the match results.
  - `stats.py`: Calculates and prints statistics about the matches.
- `data/`: Stores the scraped text data.
  - `tvdb_episodes.txt`: The Siskel & Ebert episode list from TheTVDB.
  - `tvdb_roeper_episodes.txt`: The Ebert & Roeper episode list from TheTVDB.
  - `videos_youtube.txt`: Video titles from the YouTube channel.
  - `archived_website_episodes.txt`: An archived list from the `siskelebert.org` fan site.

## Installation

1. Clone the repository.
2. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   ```
3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the main script:
```bash
python main.py
```

The script will first ask if you want to update the data files by re-scraping the sources.

Based on the configuration in `main.py`, it will then:
1.  Perform the comparison for either "Siskel & Ebert" or "Ebert & Roeper".
2.  Generate an HTML report (`semantic_matches.html` or `roeper_matches.html`) with the results.
3.  Print a statistical summary to the console, including match counts and completion rates.

You can configure which comparison to run by editing the parameters in `main.py`.
```
