# Algo-Trading-using-Machine-Learning-on-Zerodha-Kite-Connect

I am going to explain how I (un)successfully tried my hands on Algo Trading on the Zerodha Kite Connect platform using Python and Machine Learning.

Account Setup

Open an account on Zerodha and obtain a client id. I use my Zerodha account mostly for long term stock trading.

In order to do algo-trading on Zerodha Kite Connect platform, one needs to first create an app on the following page:

Login / Kite Connect developer
Kite connect developer dashboard
developers.kite.trade

Choose an app name that sounds cool.

For the redirect URL, you can choose anything. I chose ‘http://localhost:8000’

It is not necessary that the redirect URL must be a valid or functional URL if you are not building this app for other users but for your own fun. During login you will be 302 redirected to this URL on the browser along with the ‘request_token’ in the query parameter.

The Post-back URL field can remain blank.

After saving the details you will get an API Key and an API Secret. Store these somewhere safe as these 2 keys will be used to access the APIs in future.

For creating an app, it costs around INR 2000 per month. Additionally if you want to use the Historical API feature then you have to spend a extra INR 2000 per month. I had subscribed to the historical API because I wanted to use ML strategies for doing trading. But if your strategies are non-ML and do not require past data at all, you can skip the historical API.

For doing trading, every day after 7 AM in the morning, you need to login to Kite Connect website using your username and password. After login, paste the following URL:

‘https://kite.trade/connect/login?api_key=<YOUR API KEY>&v=3’

in the browser and you will be redirected to an URL given in your redirect URL of your app. In my case it looked something like:

‘http://localhost:8000?request_token=abcd1234’

Note that on redirect, if this URL is not a valid URL you will see an error page, but don't worry, we are only concerned with the ‘request_token’ in the query parameter of the URL. Copy the request_token.

Its all Python from here onwards

Install Python 3 if not present. I am using Python 3.9

Install the kiteconnect python package:
