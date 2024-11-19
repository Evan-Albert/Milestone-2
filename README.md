# Microservice for Pokemon card collecting
Random Card Generator Microservice This microservice provides an API to fetch random card details for use in various parts of the PokeCC application. It integrates with other parts of the app (e.g., Login and Reset Password pages) to dynamically display random cards.

# Communication Contract

1. Requesting Data from the Microservice
To programmatically request data from the Random Card Generator microservice, send a GET request to the following endpoint:

Endpoint: http://127.0.0.1:5020/api/random-cards
Parameters: None.
Headers: None.

2. Example API Request
Here’s an example of how to make the request using Python:
```
import requests

url = "http://127.0.0.1:5020/api/random-cards"

try:
    response = requests.get(url)
    if response.status_code == 200:
        cards = response.json().get("cards", [])
        print("Random Cards:", cards)
    else:
        print("Failed to fetch cards. Status Code:", response.status_code)
except requests.exceptions.RequestException as e:
    print("Error while connecting to the microservice:", str(e))
```

3. Example API Response
The microservice will return a JSON response containing 5 random cards. Each card includes the following fields:
```
name: The name of the card.
image_url: The URL to the card's image.
Example JSON Response:
{
  "cards": [
    {
      "name": "Card 3",
      "image_url": "/static/card3.png"
    },
    {
      "name": "Card 7",
      "image_url": "/static/card7.png"
    },
    {
      "name": "Card 1",
      "image_url": "/static/card1.png"
    },
    {
      "name": "Card 10",
      "image_url": "/static/card10.png"
    },
    {
      "name": "Card 5",
      "image_url": "/static/card5.png"
    }
  ]
}
```

4. How to Programmatically Receive and Use Data Once you receive the JSON response, iterate through the cards array to access each card’s name and image_url. 
Here’s an example:
```
response = requests.get("http://127.0.0.1:5020/api/random-cards")
if response.status_code == 200:
    random_cards = response.json().get("cards", [])
    for card in random_cards:
        print(f"Card Name: {card['name']}")
        print(f"Image URL: {card['image_url']}")
```

![image](https://github.com/user-attachments/assets/242274d2-c030-42d8-a71a-401369048701)



        
