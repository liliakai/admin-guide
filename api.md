PhishDetect clients and operators interact with the PhishDetect Node primarily through the REST API server.

**Note:** the examples below are simplified and might not reflect the full HTTP request or responses.


### Analysis

These APIs are used to request the analysis of a full URL, of a domain name or of an HTML page. They are primarily used internally by the PhishDetect Node GUI, but can also be used for other purposes. Requests to the REST API server should be sent using `Content-Type: application/json`.

#### `POST /api/analyze/link/`

Use this API to request a full dynamic analysis of a URL. This will launch a dockerized Google Chrome and instrument it to visit the page. Because of this, the request will take some time to complete (normally around 15-20 seconds).

##### Parameters

- `url`: The domain name to analyze.

##### Example

```
POST /api/analyze/domain/ HTTP/1.1
Content-Type: application/json
Host: <node>

{
    "url": "gmail.com"
}

HTTP/1.1 200 OK
Content-Type: application/json

{
    "brand": "google",
    "score": 85,
    "screenshot": "data:image/png;base64,<base64-encoded screenshot>",
    "url": "gmail.com",
    "url_final": "https://accounts.google.com/ServiceLogin?service=mail&passive=true&rm=false&continue=https://mail.google.com/mail/&ss=1&scc=1&ltmpl=default&ltmplcache=2&emr=1&osid=1",
    "warnings": [
        "The page contains mentions of original brand names (e.g. \"Google\", \"Facebook\", etc.)",
        "The page contains an hidden input",
        "The page contains a password input",
        "The page contains sign-in data, suggesting it is a clone",
        "The page has a suspicious title",
        "The page contains suspicious text",
        "The link might contain base64 encoded parameters (low confidence)"
    ],
    "whitelisted": true
}
```

#### `POST /api/analyze/domain/`

Use this API to request the static analysis of a domain name. **Note:** this will not perform a full dynamic analysis using Google Chrome.

##### Parameters

- `url`: The domain name to analyze.

##### Example

```
POST /api/analyze/domain/ HTTP/1.1
Content-Type: application/json
Host: <node>

{
    "url": "google.com"
}

HTTP/1.1 200 OK
Content-Type: application/json

{
    "brand": "google",
    "score": 0,
    "screenshot": "",
    "url": "google.com",
    "url_final": "http://google.com",
    "warnings": null,
    "whitelisted": true
}
```

#### `POST /api/analyze/html/`

TODO

### Indicators

These APIs are used by the clients to fetch indiators and by operators to add indicators to the PhishDetect Node database.

#### `GET /api/indicators/fetch/`

Use this API to retrieve the list of hashed indicators from the PhishDetect Node.

##### Parameters

None.

##### Example

```
GET /api/indicators/fetch/ HTTP/1.1
Host: <node>

HTTP/1.1 200 OK
Content-Type: application/json

{
    "domains": [<hash>, <hash>, <hash>, ...],
    "emails": [<hash>, <hash>, <hash>, ...]
}
```

#### `POST /api/indicators/add/`

Use this API to add indicators to the PhishDetect Node database. **Note:** this operation can only be performed by authorized users with their API key.

##### Parameters

- `type`: The indicator type (e.g. "email" or "domain").
- `indicators`: A list of indicators to add. They all should be of the same type.
- `tags`: A list of tags to mark the indicators with.
- `key`: Your PhishDetect Node API key.

##### Example

TODO

#### `POST /api/indicators/details/`

Use this API to retrieve additional information on the given hashed indicator. **Note:** this operation can only be performed by authorized users with their API key.

##### Parameters

- `indicator`: The SHA256 hashed indicator.
- `key`: Your PhishDetect Node API key.

##### Example

```
POST /api/indicators/details/ HTTP/1.1
Content-Type: application/json
Host: <node>

{
    "indicator": "<hash>",
    "key": "<apikey>"
}

HTTP/1.1 200 OK
Content-Type: application/json

{
    "datetime": "<datetime>",
    "hashed": "<hash>",
    "original": "<domain name>",
    "owner": "<user>",
    "tags": [
        "<tag>",
        "<tag>"
    ],
    "type": "domain"
}
```


### Events

These APIs are used by the clients to send event notifications and by the operators to review them.

#### `POST /api/events/fetch/`

TODO

#### `POST /api/events/add/`

TODO


### Raw messages

These APIs are used by the clients to send raw messages and by the operators to review them.

#### `POST /api/raw/fetch/`

TODO

#### `POST /api/raw/add/`

TODO

#### `POST /api/raw/details/`

TODO
