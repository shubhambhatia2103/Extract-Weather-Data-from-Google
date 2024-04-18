# Weather Data Extraction from Google

This guide demonstrates how to extract weather data from Google using Python. Google doesn't provide its own weather API; instead, it retrieves data from weather.com and displays it when you search on Google. Here, we'll scrape the data from Google and explore an alternative method to fetch a schematic depiction of a location’s weather data for the next two days in Python without utilizing an API.

## Module Required

- **Requests**: Requests allow you to send HTTP/1.1 requests extremely easily. This module also does not come built-in with Python. To install this, type the below command in the terminal.

    ```
    pip install requests
    ```

- **Beautiful Soup (bs4)**: Beautiful Soup is a library that makes it easy to scrape information from web pages. Whether it be an HTML or XML page, it can be used for iterating, searching, and modifying the data within it.

## Approach

1. Import the required modules.
2. Construct the URL with the entered city name.
3. Make a requests instance and pass the URL.
4. Extract the required data from the soup.
5. Print the required data.

## Step-wise Implementation

### Step 1: Import the requests and bs4 library

```python
# importing the library
import requests
from bs4 import BeautifulSoup

### Step 2: Create a URL with the entered city name and pass it to the get function.

```python
# enter city name
city = "lucknow"

# create url
url = "https://www.google.com/search?q="+"weather"+city

# requests instance
html = requests.get(url).content

# getting raw data
soup = BeautifulSoup(html, 'html.parser')
```
