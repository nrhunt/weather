#weather
welcome = input("Welcome to my Python Weather Report Program: Please Press Enter to Continue")

# requesting the weather information by city name.
def by_city():
    city = input('Please Enter Your City Name: ')
    url = 'api.openweathermap.org/data/2.5/weather?q={city name}&appid={API key}23ecb260130416da949345d1af54c4f4'.format(city)
    res = requests.get(url) #not sure how to put the request into this program. 
    data = res.json()
    show_data(data)

    question = input('Do you want to do another search ? Type Yes or No: ')
    if question == 'Yes':
        main()
    if question == 'No':
        print("Thank you for using the program. Have a nice day!")
        exit()

# requesting the weather information by zip code.
def by_zip():
    zip_code = int(input('Please Enter Your Zip code: '))
    url = 'api.openweathermap.org/data/2.5/weather?zip={zip code},{country code}&appid={API key}23ecb260130416da949345d1af54c4f4'.format(zip_code)
    res = request.get(url) # Same as the first, not sure how to put the request code in.
    data = res.json()
    show_data(data)

    question = input('Do you want to do another search? Type Yes or No: ')
    if question == 'Yes':
        main()
    if question == 'No':
        print("Thank you for using the program. Have a nice day!")
        exit()

# This will display the weather data for the weather report.
def show_data(data):
    temp = data['main']['temp']
    hightemp = data['main']['temp_max']
    lowtemp = data['main']['temp_min']
    wind_speed = data['wind']['speed']
    press = data['main']['pressure']
    latitude = data['coord']['lat']
    longitude = data['coord']['lon']
    humid = data['main']['humidity']
    description = data['weather'][0]['description']

    print('Current Temperature : {} degree fahrenheit'.format(temp))
    print('High Temperature : {} degree fahrenheit'.format(hightemp))
    print('Low Temperature : {} degree fahrenheit'.format(lowtemp))
    print('Wind Speed : {} m/s'.format(wind_speed))
    print('Pressure : {} hPa'.format(press))
    print('Latitude : {}'.format(latitude))
    print('Longitude : {}'.format(longitude))
    print('Humidity : {} %'.format(humid))
    print('Description : {}'.format(description))

# defining the main function with while the loop code is running the program
def main():
 while True:
   
  answer = input("Want to know the weather? Please type zip for zip code or town for city name: ")
  if answer == 'town':
    try:
      print("Connection has been established.")
      by_city()

    except Exception:
                print("hmm, You did not enter a valid name. Try again")
                by_city()

  if answer == 'zip':
     try:
        print("Connection has been established.")
        by_zip()

     except Exception:
      print("hmm, You did not enter a valid zip code numbers. Try again")
     by_zip()

  else:
    print("well, that is not one of the options, please try again.")

main()
