# OpenTok PHP SDK

The OpenTok PHP SDK lets you generate [sessions](http://tokbox.com/opentok/tutorials/create-session/) and
[tokens](http://tokbox.com/opentok/tutorials/create-token/) for [OpenTok](http://www.tokbox.com/) applications.


## Installation

To install from PyPi using [pip](http://www.pip-installer.org/en/latest/), a package manager for Python. 
<pre>
pip install opentok
</pre>

If you get "Permission Denied" errors try running it with `sudo` in front:
<pre>
sudo pip install opentok
</pre>

You can download the OpenTok PHP SDK from GitHub:

<https://github.com/opentok/Opentok-PHP-SDK/archive/master.zip>


## Requirements

You need an OpenTok API key and API secret, which you can obtain at <https://dashboard.tokbox.com>.

# OpenTokSDK

In order to use any of the functions of the SDK, you must first create an `OpenTokSDK` object with your developer credentials.  
The `OpenTokSDK` constructor takes two parameters:

* api_key (string) - Your OpenTok [API key](https://dashboard.tokbox.com)
* api_secret (string) - Your OpenTok [API secret](https://dashboard.tokbox.com)

```python
import OpenTokSDK

# Creating an OpenTok Object
API_KEY = ''     # Replace with your API key.
API_SECRET = ''  # Replace with your API secret.
OTSDK = OpenTokSDK.OpenTokSDK(API_KEY,API_SECRET)
```


## Creating Sessions

Use the `createSession()` method of the OpenTokSDK object to create a session and a session ID:

```python
# creating an OpenTok server-enabled session:
session_id = OTSDK.create_session().session_id

# Creating a peer-to-peer session
session_properties = {OTSDK.SessionProperties.p2p_preference: "enabled"}
session_id = OTSDK.create_session(None, sessionProperties ).session_id
```

## Generating Tokens
With the generated sessionId, you generate tokens for each user.

```python
# Generate a publisher token that will expire in 24 hours:
token = OTSDK.generate_token(session_id)

# Generate a subscriber token that has connection data
role = OTSDK.RoleConstants.SUBSCRIBER
connect_data = "username=Bob,level=4"
token = OTSDK.generate_token(session_id, role, None, connect_data)
```

Possible Errors:
* "Null or empty session ID are not valid"  
* "An invalid session ID was passed"

# More information

See the [reference documentation](docs/reference.md).

For more information on OpenTok, go to <http://www.tokbox.com/>.
