# Largest Companies by Revenue Web Scraping Project

This project is focused on web scraping to create a comprehensive dataset of the largest companies in the United States by revenue, which can be used for further analysis and insights in data projects.

## Project Overview

The goal of this project is to:

- Scrape data on the largest companies by revenue from a reliable source (such as Wikipedia).
- Compile and clean the data to create a structured dataset.
- Save this data for future projects and analysis.


## Project Structure

- **Project.ipynb**: The Jupyter Notebook containing the code for web scraping, data cleaning, and preliminary exploration.
- **data/**: Folder to store the scraped dataset in CSV format.
- **README.md**: Documentation for the project.

## Getting Started

### Prerequisites

To run this project, you will need:

- **Python 3.7** or higher
- **Jupyter Notebook** or **Google Colab**
- The following libraries:
  - `requests`
  - `BeautifulSoup`
  - `pandas`

## Installation
1.Clone this repository:
```bash
git clone https://github.com/your-username/World_Population_Web_Scrapping_Project.git
```

2.Install the required Python libraries:
```bash
pip install requests beautifulsoup4 pandas
```
## Running the Project

1. Open the `Project.ipynb` notebook.
2. Run the cells to execute the web scraping script, which will gather and clean population data.
3. The output dataset will be saved in the `data/` folder.

This Code Snippet  demonstrates a  web scraping process using BeautifulSoup and pandas:

### Code Explanation

This code imports two essential libraries for web scraping:



```python
#Import Necessary Libraries
from bs4 import BeautifulSoup
import requests
import pandas as pd
```

Define the URL to Scrape:

In this step, we define the URL of the webpage we want to scrape. The URL points to a Wikipedia page that lists the largest companies in the United States by revenue.

```python
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'
```

Send an HTTP Request to Fetch the Page:

This line of code sends an HTTP GET request to the URL defined earlier. It retrieves the HTML content of the webpage and stores it in the `page` variable.

```python
page = requests.get(url)
```

Parse the HTML Content with BeautifulSoup:

This line of code takes the HTML content retrieved in the previous step (`page.text`) and parses it using BeautifulSoup, a library for web scraping. The result is stored in the `soup` variable, which makes it easier to extract data from the webpage.

```python
soup = BeautifulSoup(page.text, 'html.parser')
```
Print the Parsed HTML:

The `print(soup)` command is used to display the entire HTML content of the webpage in a readable format. This helps to inspect and understand the structure of the page, especially if you want to locate specific data or elements to scrape.

```python
print(soup)
```
Find the First Table in the HTML:

The `soup.find('table')` command is used to search for the first occurrence of a `<table>` tag in the parsed HTML content.

```python
table = soup.find('table')
```
Find All Tables and Select the First One:

The `soup.find_all('table')[0]` command is used to find all the `<table>` elements on the webpage and select the first one.

```python
table = soup.find_all('table')[0]
```

Selecting the First Table on the Page:

The code `table = soup.find_all('table')[0]` is used to find all the `<table>` elements in the parsed HTML and assign the first table to a variable.

```python
table = soup.find_all('table')[0]
```
Printing the Table to Inspect Its Structure:

The code `print(table)` is used to display the contents of the `table` variable, which contains the first `<table>` element from the webpage.

```python
print(table)
```
Finding All Table Header Elements (`<th>`):

The code `soup.find_all('th')` is used to find all the `<th>` (table header) elements in the HTML of the page.

```python
soup.find_all('th')
```

Extracting Table Headers:

The code `world_title = table.find_all('th')` is used to find all the `<th>` (table header) elements in the specific table you are working with.

```python
world_title = table.find_all('th')
```
Printing the Table Headers:

The code `print(world_title)` is used to output the content of the `world_title` variable to the console.

```python
print(world_title)
```

Extracting Cleaned Header Text

The code `world_table_title = [title.text.strip() for title in world_title]` is a list comprehension used to clean and extract the text content from each table header (`<th>`) tag.

```python
world_table_title = [title.text.strip() for title in world_title]
```

Printing the Extracted Table Titles:

The code `print(world_table_title)` is used to display the list of cleaned table headers (column titles) that were extracted from the HTML table.

```python
print(world_table_title)
```

Creating a DataFrame with Table Titles as Columns

The code `df = pd.DataFrame(columns = world_table_title)` creates a new Pandas DataFrame with the extracted table headers (column titles) as its column names.

```python
df = pd.DataFrame(columns = world_table_title)
```

Extracting Row Data from the Table

The code `column_data = table.find_all('tr')` is used to extract all the rows from the HTML table.

```python
column_data = table.find_all('tr')
```

Extracting and Storing Row Data in DataFrame

The code below loops through the table rows (excluding the header) and extracts the data for each row, then stores it in a Pandas DataFrame.

```python
for row in column_data[1:]:
    row_data = row.find_all('td')
    individual_row_data = [data.text.strip() for data in row_data]

    length = len(df)
    df.loc[length] = individual_row_data
```

Mounting Google Drive in Google Colab:

The following code mounts your Google Drive to Google Colab so you can access files stored there (if you are using google colab):

```python
from google.colab import drive
drive.mount('/content/drive')
```
Saving DataFrame to a CSV File

The following code saves the DataFrame (`df`) to a CSV file on your local machine:

```python
df.to_csv(r'C:\Users\MWANGI\Desktop\web scraping\companies.csv', index=False)
```





















