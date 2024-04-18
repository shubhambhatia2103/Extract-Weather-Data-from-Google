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
```

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
### Step 3: Extract the required data from the soup.

```python
# get the temperature
temp = soup.find('div', attrs={'class': 'BNeawe iBp4i AP7Wnd'}).text

# this contains time and sky description
str = soup.find('div', attrs={'class': 'BNeawe tAd8D AP7Wnd'}).text

# format the data
data = str.split('\n')
time = data[0]
sky = data[1]
```

### Step 4: Extract additional data from the soup.
```python
# list having all div tags having a particular class name
listdiv = soup.findAll('div', attrs={'class': 'BNeawe s3v9rd AP7Wnd'})

# particular list with required data
strd = listdiv[5].text

# formatting the string
pos = strd.find('Wind')
other_data = strd[pos:]

```


### Step 5: Printing all the data\
```python
# printing all the data
print("Temperature is", temp)
print("Time: ", time)
print("Sky Description: ", sky)
print(other_data)

```
## Usage
To use this code, follow these steps:

1. Install the required modules using the provided command.
2. Copy the Python code into your project.
3. Replace the city variable with the desired city name.
4. Run the script.

## Dependencies
- Python 3.x
- requests
- bs4

## Contact

[<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/linkedin.png" title="LinkedIn">](https://www.linkedin.com/in/shubhambhatia2103/) [<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/github.png" title="Github">](https://github.com/shubhambhatia2103) [<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/instagram-new.png" title="Instagram">](https://instagram.com/6eingshubham) [<img target="_blank" src="https://img.icons8.com/bubbles/100/000000/twitter-squared.png" title="Twitter">](https://twitter.com/whoodattboyy)











