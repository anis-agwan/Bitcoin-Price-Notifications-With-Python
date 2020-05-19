# Bitcoin-Price-Notifications-With-Python

1. Project Setup
Start by setting up a virtual environment : $ mkvirtualenv -p $(which python3) bitcoin_notifications

Activate virtual environment : $ workon bitcoin_notifications

Install the dependencies: $ pip install requests==2.18.4  # We only need the requests package




2. Retrieving the Bitcoin Price
Start by getting the latest price from the Coinmarketcap API in the Python console: import the requests module and define the bitcoin_api_url variable which contains the Coinmarketcap API URL for Bitcoin.
Send an HTTP GET request to the URL using the requests.get() function and save the response. Since the API returns a JSON response, we can convert it to a Python object by calling the .json() function on the response.

3. Sending a Test IFTTT Notification
To use IFTTT you’ll first need to set up a new account and install their mobile app (if you want to receive phone notifications from your Python app). Once you set that up, we’re going to create a new IFTTT applet for testing purposes.

To create a new test applet follow these steps:
Click on the big “this” button
Search for the “webhooks” service and select the “Receive a web request” trigger
Let’s name the event test_event
Now select the big “that” button
Search for the “notifications” service and select the “Send a notification from the IFTTT app”
Change the message to I just triggered my first IFTTT action! and click on “Create action”
Click on the “Finish” button and we’re done


4. Creating IFTTT Applets
Emergency bitcoin price notification applet:

Choose the “webhooks” service and select the “Receive a web request” trigger
Name the event bitcoin_price_emergency
For the action select the “Notifications” service and select the “Send a rich notification from the IFTTT app” action
Give it a title, like “Bitcoin price emergency!”
Set the message to Bitcoin price is at ${{Value1}}. Buy or sell now! (we’ll return to the {{Value1}} part later on)
Optionally you could add a Link URL to the Coinmarketcap Bitcoin page: https://coinmarketcap.com/currencies/bitcoin/
Create the action and finish setting up the applet
Regular price updates applet:

Again choose the “webhooks” service and select the “Receive a web request” trigger
Name the event bitcoin_price_update
For the action select the “Telegram” service and select the “Send message” action
Set the message text to: Latest bitcoin prices:<br>{{Value1}}
Create the action and finish with the applet

5. Putting It All Together
