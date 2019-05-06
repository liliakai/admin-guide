PhishDetect clients and operators interact with the PhishDetect Node primarily through the REST API server.

### Analysis

These APIs are used to request the analysis of a full URL, of a domain name or of an HTML page. They are primarily used internally by the PhishDetect Node GUI, but can also be used for other purposes.

#### `POST /api/analyze/link/`

#### `POST /api/analyze/domain/`

#### `POST /api/analyze/html/`


### Indicators

These APIs are used by the clients to fetch indiators and by operators to add indicators to the PhishDetect Node database.

#### `GET /api/indicators/fetch/`

#### `POST /api/indicators/add/`

#### `POST /api/indicators/details/`


### Events

These APIs are used by the clients to send event notifications and by the operators to review them.

#### `POST /api/events/fetch/`

#### `POST /api/events/add/`


### Raw messages

These APIs are used by the clients to send raw messages and by the operators to review them.

#### `POST /api/raw/fetch/`

#### `POST /api/raw/add/`

#### `POST /api/raw/details/`
