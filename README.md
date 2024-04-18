# Weather Data Extraction from Google

This guide demonstrates how to extract weather data from Google using Python. Google doesn't provide its own weather API; instead, it retrieves data from weather.com and displays it when you search on Google. Here, we'll scrape the data from Google and explore an alternative method to fetch a schematic depiction of a location’s weather data for the next two days in Python without utilizing an API.

### Method 1:

#### Dependencies:
- **Requests**: Requests allow you to send HTTP/1.1 requests easily.
- **bs4 (Beautiful Soup)**: A library for scraping information from web pages.

To install the required modules, run the following command in your terminal:

```bash
pip install requests
```


## Approach

1. Import the required modules.
2. Construct the URL with the entered city name.
3. Make a requests instance and pass the URL.
4. Extract the required data from the soup.
5. Print the required data.

## Installation and Usage:
Follow the step-wise implementation provided in the code below:
```python
# importing the library
import requests
from bs4 import BeautifulSoup

# enter city name
city = input("Enter the Name of City ->  ")

# create url
url = "https://www.google.com/search?q=" + "weather" + city

# requests instance
html = requests.get(url).content

# getting raw data
soup = BeautifulSoup(html, 'html.parser')

# get the temperature
temp = soup.find('div', attrs={'class': 'BNeawe iBp4i AP7Wnd'}).text

# this contains time and sky description
str = soup.find('div', attrs={'class': 'BNeawe tAd8D AP7Wnd'}).text

# format the data
data = str.split('\n')
time = data[0]
sky = data[1]

# list having all div tags having particular class name
listdiv = soup.findAll('div', attrs={'class': 'BNeawe s3v9rd AP7Wnd'})

# particular list with required data
strd = listdiv[5].text

# formatting the string
pos = strd.find('Wind')
other_data = strd[pos:]

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











