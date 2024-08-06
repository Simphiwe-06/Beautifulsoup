import requests
from bs4 import BeautifulSoup

def get_local_weather():
   
    url = "https://www.examplelocalnews.com/weather"

    response = requests.get(url)

    if response.status_code == 200:
        soup = BeautifulSoup(response.content, 'html.parser')

        weather_section = soup.find('div', class_='weather-forecast')

        temperature = weather_section.find('span', class_='temperature').text
        condition = weather_section.find('span', class_='condition').text
        humidity = weather_section.find('span', class_='humidity').text

        print(f"Temperature: {temperature}")
        print(f"Condition: {condition}")
        print(f"Humidity: {humidity}")
    else:
        print("Could not retrieve the weather information.")

get_local_weather()
