# DuckDuckGo Scraper

A Robomotion RPA flow that searches DuckDuckGo for a user-provided query and saves the results to an Excel file.

## What It Does

1. Prompts the user to enter a search query via an input dialog.
2. Opens a Chrome browser and navigates to DuckDuckGo.
3. Types the query into the search box and clicks the search button.
4. Waits for search results to load, then scrapes the **Title** and **Link** from each result using an in-page JavaScript snippet.
5. Parses the scraped data and writes it to `~/results.xlsx` with headers starting at cell A1.
6. Closes the browser and stops the flow.

## Dependencies

| Package            | Version |
| ------------------ | ------- |
| Core.Trigger       | 26.1.0  |
| Core.Dialog        | 26.1.0  |
| Core.Browser       | 26.1.0  |
| Core.Excel         | 26.1.0  |
| Core.Flow          | 26.1.0  |
| Core.Programming   | 26.1.0  |

## Output

An Excel file at `~/results.xlsx` containing two columns:

| Title              | Link                        |
| ------------------ | --------------------------- |
| Result title 1     | https://example.com/1       |
| Result title 2     | https://example.com/2       |
| ...                | ...                         |
