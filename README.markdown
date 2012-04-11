# PyAPNs 

A Python library for interacting with the Apple Push Notification service 
(APNs)

The Oringal version of PyAPNs is writen by Simon Whitaker, Jeff kit folk and
make it support ehanced protocol, easy to work with [apnsagent][a0].

## Installation

Download the source from GitHub:
    
    $ git clone git://github.com/jeffkit/PyAPNs.git
    $ cd PyAPNs
    $ sudo python setup.py

## Sample usage

    from apns import APNs, Payload

    apns = APNs(use_sandbox=True, cert_file='cert.pem', key_file='key.pem')

    # Send a notification
    token_hex = 'b5bb9d8014a0f9b1d61e21e796d78dccdf1352f23cd32812f4850b87'
    payload = Payload(alert="Hello World!", sound="default", badge=1)
    apns.gateway_server.send_notification(token_hex, payload)
    
    # Get feedback messages
    for (token_hex, fail_time) in apns.feedback_server.items():
        # do stuff with token_hex and fail_time

For more complicated alerts including custom buttons etc, use the PayloadAlert 
class. Example:

    alert = PayloadAlert("Hello world!", action_loc_key="Click me")
    payload = Payload(alert=alert, sound="default")

To send custom payload arguments, pass a dictionary to the custom kwarg
of the Payload constructor.

    payload = Payload(alert="Hello World!", custom={'sekrit_number':123})

## Further Info

[iOS Reference Library: Local and Push Notification Programming Guide][a1]

## Credits

Written and maintained by Simon Whitaker at [Goo Software Ltd][goo].

Maintailed by Jeff Kit at [toraysoft][toray].

[a0]:https://github.com/jeffkit/apnsagent
[a1]:http://developer.apple.com/iphone/library/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008194-CH1-SW1
[goo]:http://www.goosoftware.co.uk/
[toray]:http://toraysoft.com
