nexmomessage
============


A Python wrapper for the [Nexmo API](https://docs.nexmo.com/index.php/messaging-sms-api/).


Installation
------------

    $ pip install -e git+https://github.com/marcuz/libpynexmo.git#egg=nexmomessage


Quick start (sending a message)
-------------------------------
( The following does not use the nexmoMessenger class )
First you need to load up the package and construct a dictionary
with your API credentials and message, like this:

```python
from nexmomessage import NexmoMessage

msg = {
	'reqtype': 'json',
	'api_key': YOUR_API_KEY,
	'api_secret': YOUR_API_SECRET_KEY,
	'from': YOUR_PHONE_NUMBER,
	'to': DESTINATION_PHONE_NUMBER,
	'text': 'Hello world!'
}
sms = NexmoMessage(msg)
sms.set_text_info(msg['text'])
```

Then you have a choice. For a "fire and forget" approach to sending a message,
use the `send_request` method, like this:

```python
sms.send_request()
```

This method call returns the message data if the message was sent successfully,
or raises an exception if there was an error.

```python
response = sms.send_request()

if response:
    # do something with response data
else:
    # handle the error
```


Troubleshooting
---------------

Remember that phone numbers should be specified in international format.

The Nexmo documentation contains a [list of error codes](https://docs.nexmo.com/index.php/sms-api/send-message)
which may be useful if you have problems sending a message.

Please report all bugs/issues via the GitHub issue tracker.
