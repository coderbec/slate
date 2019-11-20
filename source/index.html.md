---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

<h1 id="messages">Messages v2.1.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

The MessageMedia Messages API provides a number of endpoints for building powerful two-way messaging applications.

Base URLs:

* <a href="https://api.messagemedia.com">https://api.messagemedia.com</a>

Email: <a href="mailto:developers@messagemedia.com">MessageMedia Developers</a> Web: <a href="https://developers.messagemedia.com">MessageMedia Developers</a> 

# Authentication

- HTTP Authentication, scheme: basic 

<h1 id="messages-messages">Messages</h1>

## GetMessageStatus

<a id="opIdGetMessageStatus"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/messages/{messageId} \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/messages/{messageId} HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/messages/{messageId}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/messages/{messageId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/messages/{messageId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/messages/{messageId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/messages/{messageId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/messages/{messageId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/messages/{messageId}`

*Get message status*

Retrieve the current status of a message using the message ID returned in the send messages end point.
A successful request to the get message status endpoint will return a response body as follows:
```json
{
    "format": "SMS",
    "content": "My first message!",
    "metadata": {
        "key1": "value1",
        "key2": "value2"
    },
    "message_id": "877c19ef-fa2e-4cec-827a-e1df9b5509f7",
    "callback_url": "https://my.callback.url.com",
    "delivery_report": true,
    "destination_number": "+61401760575",
    "scheduled": "2016-11-03T11:49:02.807Z",
    "source_number": "+61491570157",
    "source_number_type": "INTERNATIONAL",
    "message_expiry_timestamp": "2016-11-03T11:49:02.807Z",
    "status": "enroute"
}
```
The status property of the response indicates the current status of the message. See the Delivery
Reports section of this documentation for more information on message statues.
*Note: If an invalid or non existent message ID parameter is specified in the request, then
a HTTP 404 Not Found response will be returned*

<h3 id="getmessagestatus-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|messageId|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "callback_url": "https://my.url.com",
  "content": "Hello world!",
  "destination_number": "+61491570156",
  "delivery_report": false,
  "format": "SMS",
  "message_expiry_timestamp": "11/3/2016 11:49:02 AM",
  "metadata": {},
  "scheduled": "11/3/2016 11:49:02 AM",
  "source_number": "+61491570156",
  "source_number_type": "INTERNATIONAL",
  "message_id": "string",
  "status": "enroute"
}
```

<h3 id="getmessagestatus-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The submitted message including the status of the message|[Getmessagestatusresponse](#schemagetmessagestatusresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request was invalid|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Resource not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## CancelScheduledMessage

<a id="opIdCancelScheduledMessage"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.messagemedia.com/v1/messages/{messageId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: text/plain'

```

```http
PUT https://api.messagemedia.com/v1/messages/{messageId} HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: text/plain

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/messages/{messageId}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "status": "cancelled"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

fetch('https://api.messagemedia.com/v1/messages/{messageId}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'text/plain'
}

result = RestClient.put 'https://api.messagemedia.com/v1/messages/{messageId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'text/plain'
}

r = requests.put('https://api.messagemedia.com/v1/messages/{messageId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/messages/{messageId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://api.messagemedia.com/v1/messages/{messageId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /v1/messages/{messageId}`

*Cancel scheduled message*

Cancel a scheduled message that has not yet been delivered.
A scheduled message can be cancelled by updating the status of a message from ```scheduled```
to ```cancelled```. This is done by submitting a PUT request to the messages endpoint using
the message ID as a parameter (the same endpoint used above to retrieve the status of a message).
The body of the request simply needs to contain a ```status``` property with the value set
to ```cancelled```.
```json
{
    "status": "cancelled"
}
```
*Note: Only messages with a status of scheduled can be cancelled. If an invalid or non existent
message ID parameter is specified in the request, then a HTTP 404 Not Found response will be 
returned*

> Body parameter

```json
{
  "status": "cancelled"
}
```

<h3 id="cancelscheduledmessage-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|messageId|path|string|true|none|
|body|body|[Cancelscheduledmessagerequest](#schemacancelscheduledmessagerequest)|true|none|

> Example responses

> 200 Response

<h3 id="cancelscheduledmessage-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Message status updated successfully|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request was invalid|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Message not found|None|

<h3 id="cancelscheduledmessage-responseschema">Response Schema</h3>

Status Code **200**

*Message status updated successfully*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## SendMessages

<a id="opIdSendMessages"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/messages \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.messagemedia.com/v1/messages HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/messages',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "messages": [
    {
      "callback_url": "https://my.callback.url.com",
      "content": "My first message",
      "destination_number": "+61491570156",
      "delivery_report": true,
      "format": "SMS",
      "message_expiry_timestamp": "2016-11-03T11:49:02.807Z",
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      },
      "scheduled": "2016-11-03T11:49:02.807Z",
      "source_number": "+61491570157",
      "source_number_type": "INTERNATIONAL"
    },
    {
      "callback_url": "https://my.callback.url.com",
      "content": "My second message",
      "destination_number": "+61491570158",
      "delivery_report": true,
      "format": "MMS",
      "subject": "This is an MMS message",
      "media": [
        "https://images.pexels.com/photos/1018350/pexels-photo-1018350.jpeg?cs=srgb&dl=architecture-buildings-city-1018350.jpg"
      ],
      "message_expiry_timestamp": "2016-11-03T11:49:02.807Z",
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      },
      "scheduled": "2016-11-03T11:49:02.807Z",
      "source_number": "+61491570159",
      "source_number_type": "INTERNATIONAL"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/messages',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.messagemedia.com/v1/messages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.messagemedia.com/v1/messages', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/messages");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/messages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/messages`

*Send messages*

Submit one or more (up to 100 per request) SMS, MMS or text to voice messages for delivery.
The most basic message has the following structure:
```json
{
    "messages": [
        {
            "content": "My first message!",
            "destination_number": "+61491570156"
        }
    ]
}
```
More advanced delivery features can be specified by setting the following properties in a message:
- ```callback_url``` A URL can be included with each message to which Webhooks will be pushed to
  via a HTTP POST request. Webhooks will be sent if and when the status of the message changes as
  it is processed (if the delivery report property of the request is set to ```true```) and when replies
  are received. Specifying a callback URL is optional.
- ```content``` The content of the message. This can be a Unicode string, up to 5,000 characters long.
  Message content is required.
- ```delivery_report``` Delivery reports can be requested with each message. If delivery reports are requested, a webhook
  will be submitted to the ```callback_url``` property specified for the message (or to the webhooks)
  specified for the account every time the status of the message changes as it is processed. The
  current status of the message can also be retrieved via the Delivery Reports endpoint of the
  Messages API. Delivery reports are optional and by default will not be requested.
- ```destination_number``` The destination number the message should be delivered to. This should be specified in E.164
  international format. For information on E.164, please refer to http://en.wikipedia.org/wiki/E.164.
  A destination number is required.
- ```format``` The format specifies which format the message will be sent as, ```SMS``` (text message), ```MMS``` (multimedia message)
  or ```TTS``` (text to speech). With ```TTS``` format, we will call the destination number and read out the
  message using a computer generated voice. Specifying a format is optional, by default ```SMS``` will be used.
- ```source_number``` A source number may be specified for the message, this will be the number that
  the message appears from on the handset. By default this feature is _not_ available and will be ignored
  in the request. Please contact <support@messagemedia.com> for more information. Specifying a source
  number is optional and a by default a source number will be assigned to the message.
- ```media``` The media is used to specify the url of the media file that you are trying to send. Supported file formats include png, jpeg and gif. ```format``` parameter must be set to ```MMS``` for this to work.
- ```subject``` The subject field is used to denote subject of the MMS message and has a maximum size of 64 characters long. Specifying a subject is optional.
- ```source_number_type``` If a source number is specified, the type of source number may also be
  specified. This is recommended when using a source address type that is not an internationally
  formatted number, available options are ```INTERNATIONAL```, ```ALPHANUMERIC``` or ```SHORTCODE```. Specifying a
  source number type is only valid when the ```source_number``` parameter is specified and is optional.
  If a source number is specified and no source number type is specified, the source number type will be
  inferred from the source number, however this may be inaccurate.
- ```scheduled``` A message can be scheduled for delivery in the future by setting the scheduled property.
  The scheduled property expects a date time specified in ISO 8601 format. The scheduled time must be
  provided in UTC and is optional. If no scheduled property is set, the message will be delivered immediately.
- ```message_expiry_timestamp``` A message expiry timestamp can be provided to specify the latest time
  at which the message should be delivered. If the message cannot be delivered before the specified
  message expiry timestamp elapses, the message will be discarded. Specifying a message expiry 
  timestamp is optional.
- ```metadata``` Metadata can be included with the message which will then be included with any delivery
  reports or replies matched to the message. This can be used to create powerful two-way messaging
  applications without having to store persistent data in the application. Up to 10 key / value metadata data
  pairs can be specified in a message. Each key can be up to 100 characters long, and each value up to 
  256 characters long. Specifying metadata for a message is optional.
The response body of a successful POST request to the messages endpoint will include a ```messages```
property which contains a list of all messages submitted. The list of messages submitted will
reflect the list of messages included in the request, but each message will also contain two new
properties, ```message_id``` and ```status```. The returned message ID will be a 36 character UUID
which can be used to check the status of the message via the Get Message Status endpoint. The status
of the message which reflect the status of the message at submission time which will always be
```queued```. See the Delivery Reports section of this documentation for more information on message
statues.
*Note: when sending multiple messages in a request, all messages must be valid for the request to be successful.
If any messages in the request are invalid, no messages will be sent.*

> Body parameter

```json
{
  "messages": [
    {
      "callback_url": "https://my.callback.url.com",
      "content": "My first message",
      "destination_number": "+61491570156",
      "delivery_report": true,
      "format": "SMS",
      "message_expiry_timestamp": "2016-11-03T11:49:02.807Z",
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      },
      "scheduled": "2016-11-03T11:49:02.807Z",
      "source_number": "+61491570157",
      "source_number_type": "INTERNATIONAL"
    },
    {
      "callback_url": "https://my.callback.url.com",
      "content": "My second message",
      "destination_number": "+61491570158",
      "delivery_report": true,
      "format": "MMS",
      "subject": "This is an MMS message",
      "media": [
        "https://images.pexels.com/photos/1018350/pexels-photo-1018350.jpeg?cs=srgb&dl=architecture-buildings-city-1018350.jpg"
      ],
      "message_expiry_timestamp": "2016-11-03T11:49:02.807Z",
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      },
      "scheduled": "2016-11-03T11:49:02.807Z",
      "source_number": "+61491570159",
      "source_number_type": "INTERNATIONAL"
    }
  ]
}
```

<h3 id="sendmessages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Sendmessagesrequest](#schemasendmessagesrequest)|true|none|

> Example responses

> 202 Response

```json
{
  "messages": [
    {
      "callback_url": "https://my.url.com",
      "content": "Hello world!",
      "destination_number": "+61491570156",
      "delivery_report": false,
      "format": "SMS",
      "message_expiry_timestamp": "11/3/2016 11:49:02 AM",
      "metadata": {},
      "scheduled": "11/3/2016 11:49:02 AM",
      "source_number": "+61491570156",
      "source_number_type": "INTERNATIONAL",
      "message_id": "string",
      "status": "enroute",
      "media": [
        "string"
      ],
      "subject": "string"
    }
  ]
}
```

> 400 Response

```json
{
  "message": "Something went wrong. Please try again later."
}
```

<h3 id="sendmessages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Messages were accepted for processing|[Sendmessagesresponse](#schemasendmessagesresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Unexpected error in API call. See HTTP response body for details.|[Sendmessages400response](#schemasendmessages400response)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Message not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

<h1 id="messages-delivery-reports">Delivery Reports</h1>

## CheckDeliveryReports

<a id="opIdCheckDeliveryReports"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/delivery_reports \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/delivery_reports HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/delivery_reports',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/delivery_reports',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/delivery_reports',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/delivery_reports', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/delivery_reports");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/delivery_reports", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/delivery_reports`

*Check delivery reports*

Check for any delivery reports that have been received.
Delivery reports are a notification of the change in status of a message as it is being processed.
Each request to the check delivery reports endpoint will return any delivery reports received that
have not yet been confirmed using the confirm delivery reports endpoint. A response from the check
delivery reports endpoint will have the following structure:
```json
{
    "delivery_reports": [
        {
            "callback_url": "https://my.callback.url.com",
            "delivery_report_id": "01e1fa0a-6e27-4945-9cdb-18644b4de043",
            "source_number": "+61491570157",
            "date_received": "2017-05-20T06:30:37.642Z",
            "status": "enroute",
            "delay": 0,
            "submitted_date": "2017-05-20T06:30:37.639Z",
            "original_text": "My first message!",
            "message_id": "d781dcab-d9d8-4fb2-9e03-872f07ae94ba",
            "vendor_account_id": {
                "vendor_id": "MessageMedia",
                "account_id": "MyAccount"
            },
            "metadata": {
                "key1": "value1",
                "key2": "value2"
            }
        },
        {
            "callback_url": "https://my.callback.url.com",
            "delivery_report_id": "0edf9022-7ccc-43e6-acab-480e93e98c1b",
            "source_number": "+61491570158",
            "date_received": "2017-05-21T01:46:42.579Z",
            "status": "enroute",
            "delay": 0,
            "submitted_date": "2017-05-21T01:46:42.574Z",
            "original_text": "My second message!",
            "message_id": "fbb3b3f5-b702-4d8b-ab44-65b2ee39a281",
            "vendor_account_id": {
                "vendor_id": "MessageMedia",
                "account_id": "MyAccount"
            },
            "metadata": {
                "key1": "value1",
                "key2": "value2"
            }
        }
    ]
}
```
Each delivery report will contain details about the message, including any metadata specified
and the new status of the message (as each delivery report indicates a change in status of a
message) and the timestamp at which the status changed. Every delivery report will have a 
unique delivery report ID for use with the confirm delivery reports endpoint.
*Note: The source number and destination number properties in a delivery report are the inverse of
those specified in the message that the delivery report relates to. The source number of the
delivery report is the destination number of the original message.*
Subsequent requests to the check delivery reports endpoint will return the same delivery reports
and a maximum of 100 delivery reports will be returned in each request. Applications should use the
confirm delivery reports endpoint in the following pattern so that delivery reports that have been
processed are no longer returned in subsequent check delivery reports requests.
1. Call check delivery reports endpoint
2. Process each delivery report
3. Confirm all processed delivery reports using the confirm delivery reports endpoint
*Note: It is recommended to use the Webhooks feature to receive reply messages rather than
polling the check delivery reports endpoint.*

> Example responses

> 200 Response

```json
{
  "delivery_reports": [
    {
      "callback_url": "https://my.callback.url.com",
      "delivery_report_id": "01e1fa0a-6e27-4945-9cdb-18644b4de043",
      "source_number": "+61491570157",
      "date_received": "2017-05-20T06:30:37.642Z",
      "status": "enroute",
      "delay": 0,
      "submitted_date": "2017-05-20T06:30:37.639Z",
      "original_text": "My first message!",
      "message_id": "d781dcab-d9d8-4fb2-9e03-872f07ae94ba",
      "vendor_account_id": {
        "vendor_id": "MessageMedia",
        "account_id": "MyAccount"
      },
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      }
    },
    {
      "callback_url": "https://my.callback.url.com",
      "delivery_report_id": "0edf9022-7ccc-43e6-acab-480e93e98c1b",
      "source_number": "+61491570158",
      "date_received": "2017-05-21T01:46:42.579Z",
      "status": "submitted",
      "delay": 0,
      "submitted_date": "2017-05-21T01:46:42.574Z",
      "original_text": "My second message!",
      "message_id": "fbb3b3f5-b702-4d8b-ab44-65b2ee39a281",
      "vendor_account_id": {
        "vendor_id": "MessageMedia",
        "account_id": "MyAccount"
      },
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      }
    }
  ]
}
```

<h3 id="checkdeliveryreports-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Unconfirmed reports|[Checkdeliveryreportsresponse](#schemacheckdeliveryreportsresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request was invalid|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Message not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## ConfirmDeliveryReportsAsReceived

<a id="opIdConfirmDeliveryReportsAsReceived"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/delivery_reports/confirmed \
  -H 'Content-Type: application/json' \
  -H 'Accept: text/plain'

```

```http
POST https://api.messagemedia.com/v1/delivery_reports/confirmed HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: text/plain

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/delivery_reports/confirmed',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "delivery_report_ids": [
    "011dcead-6988-4ad6-a1c7-6b6c68ea628d",
    "3487b3fa-6586-4979-a233-2d1b095c7718",
    "ba28e94b-c83d-4759-98e7-ff9c7edb87a1"
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

fetch('https://api.messagemedia.com/v1/delivery_reports/confirmed',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'text/plain'
}

result = RestClient.post 'https://api.messagemedia.com/v1/delivery_reports/confirmed',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'text/plain'
}

r = requests.post('https://api.messagemedia.com/v1/delivery_reports/confirmed', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/delivery_reports/confirmed");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/delivery_reports/confirmed", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/delivery_reports/confirmed`

*Confirm delivery reports as received*

Mark a delivery report as confirmed so it is no longer return in check delivery reports requests.
The confirm delivery reports endpoint is intended to be used in conjunction with the check delivery
reports endpoint to allow for robust processing of delivery reports. Once one or more delivery
reports have been processed, they can then be confirmed using the confirm delivery reports endpoint so they
are no longer returned in subsequent check delivery reports requests.
The confirm delivery reports endpoint takes a list of delivery report IDs as follows:
```json
{
    "delivery_report_ids": [
        "011dcead-6988-4ad6-a1c7-6b6c68ea628d",
        "3487b3fa-6586-4979-a233-2d1b095c7718",
        "ba28e94b-c83d-4759-98e7-ff9c7edb87a1"
    ]
}
```
Up to 100 delivery reports can be confirmed in a single confirm delivery reports request.

> Body parameter

```json
{
  "delivery_report_ids": [
    "011dcead-6988-4ad6-a1c7-6b6c68ea628d",
    "3487b3fa-6586-4979-a233-2d1b095c7718",
    "ba28e94b-c83d-4759-98e7-ff9c7edb87a1"
  ]
}
```

<h3 id="confirmdeliveryreportsasreceived-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Confirmdeliveryreportsasreceivedrequest](#schemaconfirmdeliveryreportsasreceivedrequest)|true|none|

> Example responses

> 202 Response

<h3 id="confirmdeliveryreportsasreceived-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Requested delivery reports will be marked as confirmed|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request was invalid|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Message not found|None|

<h3 id="confirmdeliveryreportsasreceived-responseschema">Response Schema</h3>

Status Code **202**

*Requested delivery reports will be marked as confirmed*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

<h1 id="messages-replies">Replies</h1>

## CheckReplies

<a id="opIdCheckReplies"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/replies \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/replies HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/replies',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/replies',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/replies',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/replies', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/replies");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/replies", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/replies`

*Check replies*

Check for any replies that have been received.
Replies are messages that have been sent from a handset in response to a message sent by an
application or messages that have been sent from a handset to a inbound number associated with
an account, known as a dedicated inbound number (contact <support@messagemedia.com> for more
information on dedicated inbound numbers).
Each request to the check replies endpoint will return any replies received that have not yet
been confirmed using the confirm replies endpoint. A response from the check replies endpoint
will have the following structure:
```json
{
    "replies": [
        {
            "metadata": {
                "key1": "value1",
                "key2": "value2"
            },
            "message_id": "877c19ef-fa2e-4cec-827a-e1df9b5509f7",
            "reply_id": "a175e797-2b54-468b-9850-41a3eab32f74",
            "date_received": "2016-12-07T08:43:00.850Z",
            "callback_url": "https://my.callback.url.com",
            "destination_number": "+61491570156",
            "source_number": "+61491570157",
            "vendor_account_id": {
                "vendor_id": "MessageMedia",
                "account_id": "MyAccount"
            },
            "content": "My first reply!"
        },
        {
            "metadata": {
                "key1": "value1",
                "key2": "value2"
            },
            "message_id": "8f2f5927-2e16-4f1c-bd43-47dbe2a77ae4",
            "reply_id": "3d8d53d8-01d3-45dd-8cfa-4dfc81600f7f",
            "date_received": "2016-12-07T08:43:00.850Z",
            "callback_url": "https://my.callback.url.com",
            "destination_number": "+61491570157",
            "source_number": "+61491570158",
            "vendor_account_id": {
                "vendor_id": "MessageMedia",
                "account_id": "MyAccount"
            },
            "content": "My second reply!"
        }
    ]
}
```
Each reply will contain details about the reply message, as well as details of the message the reply was sent
in response to, including any metadata specified. Every reply will have a reply ID to be used with the
confirm replies endpoint.
*Note: The source number and destination number properties in a reply are the inverse of those
specified in the message the reply is in response to. The source number of the reply message is the
same as the destination number of the original message, and the destination number of the reply
message is the same as the source number of the original message. If a source number
wasn't specified in the original message, then the destination number property will not be present
in the reply message.*
Subsequent requests to the check replies endpoint will return the same reply messages and a maximum
of 100 replies will be returned in each request. Applications should use the confirm replies endpoint
in the following pattern so that replies that have been processed are no longer returned in
subsequent check replies requests.
1. Call check replies endpoint
2. Process each reply message
3. Confirm all processed reply messages using the confirm replies endpoint
*Note: It is recommended to use the Webhooks feature to receive reply messages rather than polling
the check replies endpoint.*

> Example responses

> 200 Response

```json
{
  "replies": [
    {
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      },
      "message_id": "877c19ef-fa2e-4cec-827a-e1df9b5509f7",
      "reply_id": "a175e797-2b54-468b-9850-41a3eab32f74",
      "date_received": "2016-12-07T08:43:00.850Z",
      "callback_url": "https://my.callback.url.com",
      "destination_number": "+61491570156",
      "source_number": "+61491570157",
      "vendor_account_id": {
        "vendor_id": "MessageMedia",
        "account_id": "MyAccount"
      },
      "content": "My first reply!"
    },
    {
      "metadata": {
        "key1": "value1",
        "key2": "value2"
      },
      "message_id": "8f2f5927-2e16-4f1c-bd43-47dbe2a77ae4",
      "reply_id": "3d8d53d8-01d3-45dd-8cfa-4dfc81600f7f",
      "date_received": "2016-12-07T08:43:00.850Z",
      "callback_url": "https://my.callback.url.com",
      "destination_number": "+61491570157",
      "source_number": "+61491570158",
      "vendor_account_id": {
        "vendor_id": "MessageMedia",
        "account_id": "MyAccount"
      },
      "content": "My second reply!"
    }
  ]
}
```

<h3 id="checkreplies-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Unconfirmed replies|[Checkrepliesresponse](#schemacheckrepliesresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request was invalid|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Message not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## ConfirmRepliesAsReceived

<a id="opIdConfirmRepliesAsReceived"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/replies/confirmed \
  -H 'Content-Type: application/json' \
  -H 'Accept: text/plain'

```

```http
POST https://api.messagemedia.com/v1/replies/confirmed HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: text/plain

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/replies/confirmed',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "reply_ids": [
    "011dcead-6988-4ad6-a1c7-6b6c68ea628d",
    "3487b3fa-6586-4979-a233-2d1b095c7718",
    "ba28e94b-c83d-4759-98e7-ff9c7edb87a1"
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

fetch('https://api.messagemedia.com/v1/replies/confirmed',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'text/plain'
}

result = RestClient.post 'https://api.messagemedia.com/v1/replies/confirmed',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'text/plain'
}

r = requests.post('https://api.messagemedia.com/v1/replies/confirmed', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/replies/confirmed");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/replies/confirmed", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/replies/confirmed`

*Confirm replies as received*

Mark a reply message as confirmed so it is no longer returned in check replies requests.
The confirm replies endpoint is intended to be used in conjunction with the check replies endpoint
to allow for robust processing of reply messages. Once one or more reply messages have been processed
they can then be confirmed using the confirm replies endpoint so they are no longer returned in
subsequent check replies requests.
The confirm replies endpoint takes a list of reply IDs as follows:
```json
{
    "reply_ids": [
        "011dcead-6988-4ad6-a1c7-6b6c68ea628d",
        "3487b3fa-6586-4979-a233-2d1b095c7718",
        "ba28e94b-c83d-4759-98e7-ff9c7edb87a1"
    ]
}
```
Up to 100 replies can be confirmed in a single confirm replies request.

> Body parameter

```json
{
  "reply_ids": [
    "011dcead-6988-4ad6-a1c7-6b6c68ea628d",
    "3487b3fa-6586-4979-a233-2d1b095c7718",
    "ba28e94b-c83d-4759-98e7-ff9c7edb87a1"
  ]
}
```

<h3 id="confirmrepliesasreceived-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Confirmrepliesasreceivedrequest](#schemaconfirmrepliesasreceivedrequest)|true|none|

> Example responses

> 202 Response

<h3 id="confirmrepliesasreceived-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Requested replies will be marked as confirmed|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Request was invalid|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Message not found|None|

<h3 id="confirmrepliesasreceived-responseschema">Response Schema</h3>

Status Code **202**

*Requested replies will be marked as confirmed*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

<h1 id="messages-lookups">Lookups</h1>

multi  line

## LookupAPhoneNumber

<a id="opIdLookupAPhoneNumber"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/lookups/phone/{phone_number} \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/lookups/phone/{phone_number} HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/lookups/phone/{phone_number}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/lookups/phone/{phone_number}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/lookups/phone/{phone_number}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/lookups/phone/{phone_number}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/lookups/phone/{phone_number}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/lookups/phone/{phone_number}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/lookups/phone/{phone_number}`

*Lookup a phone number*

Use the Lookups API to find information about a phone number.
A request to the lookups API has the following format:
```/v1/lookups/phone/{phone_number}?options={x}```
where `{x}` is an individual value or a combination of values. 
The `{phone_number}` parameter is a required field and should be set to the phone number to be looked up.
The options query parameter can also be used to request additional information about the phone number.
By default, a request will only return the `country_code` and `phone_number` properties in the response.
```json
{
  "country_code": "AU",
  "phone_number": "+61491570156",
}
```
To request details about the the carrier, include `carrier` as a value of the options parameter and to 
request details about the type, include `type` as a value of the options parameter. The `carrier` and
and the `type` values can be used together using a comma separated list, i.e. `carrier,type`.
To request details about the location, include `hlr` as a value of the options parameter. 
NOTE: The `hlr` value CANNOT be used in conjuction with the other values.
A successful request to the lookups endpoint with `carrier` and `type` as values will return a response body as follows:
```json
{
  "country_code": "AU",
  "phone_number": "+61491570156",
  "type": "mobile",
  "carrier": {
    "name": "Telstra"
  }
}
```
A successful request to the lookups endpoint with `hlr` as the value will return a response body as follows:
```json
{
    "result": "OK",
    "imsi": 24008,
    "location": 46
}
```
Each property in the response body is defined as follows:
- ```country_code``` ISO ALPHA 2 country code of the phone number
- ```phone_number``` E.164 formatted phone number
- ```type``` The type of number. This can be ```"mobile"``` or ```"landline"```
- ```carrier``` Holds information about the specific carrier (if available)
  - ```name``` The carrier's name as reported by the network
- `imsi` A unique number identifying a GSM subscriber
- `location` The location of the mobile number

<h3 id="lookupaphonenumber-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|phone_number|path|string|true|The phone number to be looked up|
|options|query|string|false|The options query parameter can also be used to request additional information about the phone number.|

> Example responses

> 200 Response

```json
{
  "country_code": "AU",
  "phone_number": 61491570156,
  "type": "mobile",
  "carrier": {
    "name": "Telstra"
  }
}
```

> 404 Response

```json
{
  "message": "The number could not be found or is invalid."
}
```

<h3 id="lookupaphonenumber-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Number was looked up successfully|[Lookupaphonenumberresponse](#schemalookupaphonenumberresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Unexpected error in API call. See HTTP response body for details.|[Lookupaphonenumber404response](#schemalookupaphonenumber404response)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

<h1 id="messages-messaging-reports">Messaging Reports</h1>

The MessageMedia Reports API provides a number of endpoints for running reports of messages sent and received using Messages API. Reports can be detailed, a list of all messages and details of each message, or summary reports, which can be aggregated on a number of dimensions.

## GetMetadataKeys

<a id="opIdGetMetadataKeys"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys?start_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&end_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29 \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys?start_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&end_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29 HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys',
  method: 'get',
  data: '?start_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&end_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys?start_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&end_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys',
  params: {
  'start_date' => 'string',
'end_date' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys', params={
  'start_date': "2017-02-10T13:30:00.000Z",  'end_date': "2017-02-12T13:30:00.000Z"
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys?start_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&end_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/{messageType}/metadata/keys", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/{messageType}/metadata/keys`

*getMetadataKeys*

Returns a list of metadata keys

<h3 id="getmetadatakeys-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|messageType|path|[message_type](#schemamessage_type)|true|Message type. Possible values are sent messages and received messages.|
|start_date|query|string|true|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format|
|end_date|query|string|true|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format|
|accounts|query|array[string]|false|Filter results by a specific account. By default results|
|timezone|query|string|false|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|

#### Detailed descriptions

**accounts**: Filter results by a specific account. By default results

will be returned for the account associated with the authentication

credentials and all sub accounts.

#### Enumerated Values

|Parameter|Value|
|---|---|
|messageType|SENT_MESSAGES|
|messageType|RECEIVED_MESSAGES|

> Example responses

> 200 Response

```json
{
  "data": [],
  "properties": {
    "end_date": "2017-02-10T13:30:00.000Z",
    "start_date": "2017-02-12T13:30:00.000Z",
    "accounts": []
  }
}
```

<h3 id="getmetadatakeys-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of all metadata keys used in the specified time window|[MetadataKeysResponse](#schemametadatakeysresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## GetAsyncReports

<a id="opIdGetAsyncReports"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/async_reports \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/async_reports HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/async_reports',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/async_reports',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/async_reports',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/async_reports', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/async_reports");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/async_reports", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/async_reports`

*getAsyncReports*

Lists asynchronous reports.

<h3 id="getasyncreports-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|number(double)|false|Page number for paging through paginated result sets.|
|page_size|query|number(double)|false|Number of results to return in a page for paginated result sets.|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "created_datetime": "2017-02-12T13:30:00.000Z",
      "last_modified_datetime": "2017-02-12T13:30:00.000Z"
    }
  ],
  "pagination": {}
}
```

<h3 id="getasyncreports-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of requested asynchronous reports.|[getAsyncReportsResponse](#schemagetasyncreportsresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## GetAsyncReportById

<a id="opIdGetAsyncReportById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/async_reports/{report_id} \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/async_reports/{report_id} HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/async_reports/{report_id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/async_reports/{report_id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/async_reports/{report_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/async_reports/{report_id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/async_reports/{report_id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/async_reports/{report_id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/async_reports/{report_id}`

*getAsyncReportById*

Gets a single asynchronous report.

<h3 id="getasyncreportbyid-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|report_id|path|string|true|Unique ID of the async report|

> Example responses

> 200 Response

```json
{
  "created_datetime": "2017-02-12T13:30:00.000Z",
  "last_modified_datetime": "2017-02-12T13:30:00.000Z"
}
```

<h3 id="getasyncreportbyid-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The asynchronous report.|[AsyncReport](#schemaasyncreport)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested report was not found.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## GetAsyncReportDataById

<a id="opIdGetAsyncReportDataById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data \
  -H 'Accept: binary'

```

```http
GET https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data HTTP/1.1
Host: api.messagemedia.com
Accept: binary

```

```javascript
var headers = {
  'Accept':'binary'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'binary'

};

fetch('https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'binary'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'binary'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"binary"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/async_reports/{report_id}/data", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/async_reports/{report_id}/data`

*getAsyncReportDataById*

Gets the data of an asynchronous report.

<h3 id="getasyncreportdatabyid-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|report_id|path|string|true|Unique ID of the async report|

> Example responses

> 200 Response

<h3 id="getasyncreportdatabyid-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Report not found or not finished.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## SubmitReceivedMessagesDetail

<a id="opIdSubmitReceivedMessagesDetail"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/reporting/received_messages/detail/async \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.messagemedia.com/v1/reporting/received_messages/detail/async HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/received_messages/detail/async',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "period": "TODAY",
  "sort_by": "ACCOUNT",
  "sort_direction": "ASCENDING",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/received_messages/detail/async',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.messagemedia.com/v1/reporting/received_messages/detail/async',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.messagemedia.com/v1/reporting/received_messages/detail/async', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/received_messages/detail/async");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/reporting/received_messages/detail/async", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/reporting/received_messages/detail/async`

*submitReceivedMessagesDetail*

Submits a request to generate an async detail report

> Body parameter

```json
{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "period": "TODAY",
  "sort_by": "ACCOUNT",
  "sort_direction": "ASCENDING",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}
```

<h3 id="submitreceivedmessagesdetail-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[asyncreceivedmessagesdetailrequest](#schemaasyncreceivedmessagesdetailrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "b8ffd5b3-050a-46b9-9192-fbd7c20a22ec"
}
```

<h3 id="submitreceivedmessagesdetail-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The identifier of the async report request|[AsyncReportResponse](#schemaasyncreportresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## GetReceivedMessagesDetail

<a id="opIdGetReceivedMessagesDetail"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/received_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29 \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/received_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29 HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/received_messages/detail',
  method: 'get',
  data: '?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/received_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/received_messages/detail',
  params: {
  'end_date' => 'string',
'start_date' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/received_messages/detail', params={
  'end_date': "2017-02-10T13:30:00.000Z",  'start_date': "2017-02-12T13:30:00.000Z"
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/received_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/received_messages/detail", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/received_messages/detail`

*getReceivedMessagesDetail*

Returns a list message received

<h3 id="getreceivedmessagesdetail-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|end_date|query|string|true|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|query|string|true|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|accounts|query|array[string]|false|Filter results by a specific account. By default results|
|action|query|[action](#schemaaction)|false|Filter results by the action that was invoked for this message.|
|destination_address_country|query|string|false|Filter results by destination address country.|
|destination_address|query|string|false|Filter results by destination address.|
|message_format|query|[message_format](#schemamessage_format)|false|Filter results by message format.|
|metadata_key|query|string|false|Filter results for messages that include a metadata key.|
|metadata_value|query|string|false|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|page|query|number(double)|false|Page number for paging through paginated result sets.|
|page_size|query|number(double)|false|Number of results to return in a page for paginated result sets.|
|sort_by|query|[sort_by](#schemasort_by)|false|Field to sort results set by|
|sort_direction|query|[sort_direction](#schemasort_direction)|false|Order to sort results by.|
|source_address_country|query|string|false|Filter results by source address country.|
|source_address|query|string|false|Filter results by source address.|
|timezone|query|string|false|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|

#### Detailed descriptions

**accounts**: Filter results by a specific account. By default results

will be returned for the account associated with the authentication

credentials and all sub accounts.

#### Enumerated Values

|Parameter|Value|
|---|---|
|action|MyAccount001|
|action|OPT_OUT|
|action|OPT_IN|
|action|GLOBAL_OPT_OUT|
|message_format|SMS|
|message_format|TTS|
|sort_by|ACCOUNT|
|sort_by|ACTION|
|sort_by|DESTINATION_ADDRESS|
|sort_by|DESTINATION_ADDRESS_COUNTRY|
|sort_by|FORMAT|
|sort_by|SOURCE_ADDRESS|
|sort_by|SOURCE_ADDRESS_COUNTRY|
|sort_by|TIMESTAMP|
|sort_direction|ASCENDING|
|sort_direction|DESCENDING|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "account": "MyAccount001",
      "action": "MyAccount001",
      "content": "Hello back",
      "destination_address": 61491570156,
      "destination_address_country": "AU",
      "format": "AU",
      "source_address": 61491570156,
      "source_address_country": "AU",
      "timestamp": "2017-02-12T13:30:00.000Z"
    }
  ],
  "pagination": {},
  "properties": {
    "end_date": "2017-02-10T13:30:00.000Z",
    "start_date": "2017-02-12T13:30:00.000Z",
    "sorting": {},
    "filters": {
      "accounts": []
    },
    "timezone": "The timezone that this report is presented in, this may be passed in as a parameter to the report, or taken from account settings"
  }
}
```

<h3 id="getreceivedmessagesdetail-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of all messages received in the specified time window|[ReceivedMessages](#schemareceivedmessages)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## SubmitSentMessagesDetail

<a id="opIdSubmitSentMessagesDetail"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/reporting/sent_messages/detail/async \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.messagemedia.com/v1/reporting/sent_messages/detail/async HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/sent_messages/detail/async',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "period": "TODAY",
  "sort_by": "DELIVERY_REPORT",
  "sort_direction": "ASCENDING",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "statuses": [
    "CANCELLED"
  ],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/sent_messages/detail/async',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.messagemedia.com/v1/reporting/sent_messages/detail/async',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.messagemedia.com/v1/reporting/sent_messages/detail/async', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/sent_messages/detail/async");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/reporting/sent_messages/detail/async", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/reporting/sent_messages/detail/async`

*submitSentMessagesDetail*

Submits a request to generate an async detail report

> Body parameter

```json
{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "period": "TODAY",
  "sort_by": "DELIVERY_REPORT",
  "sort_direction": "ASCENDING",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "statuses": [
    "CANCELLED"
  ],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}
```

<h3 id="submitsentmessagesdetail-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[asyncsentmessagesdetailrequest](#schemaasyncsentmessagesdetailrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "b8ffd5b3-050a-46b9-9192-fbd7c20a22ec"
}
```

<h3 id="submitsentmessagesdetail-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The identifier of the async report request|[AsyncReportResponse](#schemaasyncreportresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## GetSentMessagesDetail

<a id="opIdGetSentMessagesDetail"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/sent_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29 \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/sent_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29 HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/sent_messages/detail',
  method: 'get',
  data: '?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/sent_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/sent_messages/detail',
  params: {
  'end_date' => 'string',
'start_date' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/sent_messages/detail', params={
  'end_date': "2017-02-10T13:30:00.000Z",  'start_date': "2017-02-12T13:30:00.000Z"
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/sent_messages/detail?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/sent_messages/detail", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/sent_messages/detail`

*getSentMessagesDetail*

Returns a list of message sent

<h3 id="getsentmessagesdetail-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|end_date|query|string|true|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|query|string|true|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|accounts|query|array[string]|false|Filter results by a specific account. By default results|
|delivery_report|query|boolean|false|Filter results by delivery report.|
|destination_address_country|query|string|false|Filter results by destination address country.|
|destination_address|query|string|false|Filter results by destination address.|
|message_format|query|[message_format](#schemamessage_format)|false|Filter results by message format.|
|metadata_key|query|string|false|Filter results for messages that include a metadata key.|
|metadata_value|query|string|false|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|status_code|query|string|false|Filter results by message status code.|
|status|query|[status](#schemastatus)|false|Filter results by message status. Can't be combined with statuses.|
|statuses|query|[statuses](#schemastatuses)|false|Filter results by message status. Can't be combined with status.{array}|
|page|query|number(double)|false|Page number for paging through paginated result sets.|
|page_size|query|number(double)|false|Number of results to return in a page for paginated result sets.|
|sort_by|query|[sort_by](#schemasort_by)|false|Field to sort results set by|
|sort_direction|query|[sort_direction](#schemasort_direction)|false|Order to sort results by.|
|source_address_country|query|string|false|Filter results by source address country.|
|source_address|query|string|false|Filter results by source address.|
|timezone|query|string|false|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|

#### Detailed descriptions

**accounts**: Filter results by a specific account. By default results

will be returned for the account associated with the authentication

credentials and all sub accounts.

#### Enumerated Values

|Parameter|Value|
|---|---|
|message_format|SMS|
|message_format|TTS|
|status|CANCELLED|
|status|DELIVERED|
|status|ENROUTE|
|status|EXPIRED|
|status|HELD|
|status|PROCESSED|
|status|PROCESSING|
|status|QUEUED|
|status|REJECTED|
|status|SCHEDULED|
|status|SUBMITTED|
|statuses|CANCELLED|
|statuses|DELIVERED|
|statuses|ENROUTE|
|statuses|EXPIRED|
|statuses|HELD|
|statuses|PROCESSED|
|statuses|PROCESSING|
|statuses|QUEUED|
|statuses|REJECTED|
|statuses|SCHEDULED|
|statuses|SUBMITTED|
|sort_by|ACCOUNT|
|sort_by|ACTION|
|sort_by|DESTINATION_ADDRESS|
|sort_by|DESTINATION_ADDRESS_COUNTRY|
|sort_by|FORMAT|
|sort_by|SOURCE_ADDRESS|
|sort_by|SOURCE_ADDRESS_COUNTRY|
|sort_by|TIMESTAMP|
|sort_direction|ASCENDING|
|sort_direction|DESCENDING|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "account": "MyAccount001",
      "content": "Hello world!",
      "delivered_timestamp": "2017-02-12T13:30:00.000Z",
      "destination_address": 61491570156,
      "destination_address_country": "AU",
      "format": "AU",
      "source_address": 61491570156,
      "source_address_country": "AU",
      "units": 2,
      "timestamp": "2017-02-12T13:30:00.000Z"
    }
  ],
  "pagination": {},
  "properties": {
    "end_date": "2017-02-10T13:30:00.000Z",
    "start_date": "2017-02-12T13:30:00.000Z",
    "sorting": {},
    "filters": {
      "accounts": []
    },
    "timezone": "The timezone that this report is presented in, this may be passed in as a parameter to the report, or taken from account settings"
  }
}
```

<h3 id="getsentmessagesdetail-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of all messages sent in the specified time window|[SentMessages](#schemasentmessages)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## SubmitReceivedMessagesSummary

<a id="opIdSubmitReceivedMessagesSummary"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/reporting/received_messages/summary/async \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.messagemedia.com/v1/reporting/received_messages/summary/async HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/received_messages/summary/async',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "summary_by": "COUNT",
  "summary_field": "MESSAGE_ID",
  "group_by": [
    "DAY"
  ],
  "period": "THIS_WEEK",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/received_messages/summary/async',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.messagemedia.com/v1/reporting/received_messages/summary/async',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.messagemedia.com/v1/reporting/received_messages/summary/async', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/received_messages/summary/async");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/reporting/received_messages/summary/async", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/reporting/received_messages/summary/async`

*submitReceivedMessagesSummary*

Submits a summarised report of received messages

> Body parameter

```json
{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "summary_by": "COUNT",
  "summary_field": "MESSAGE_ID",
  "group_by": [
    "DAY"
  ],
  "period": "THIS_WEEK",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}
```

<h3 id="submitreceivedmessagessummary-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[asyncreceivedmessagessummaryrequest](#schemaasyncreceivedmessagessummaryrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "b8ffd5b3-050a-46b9-9192-fbd7c20a22ec"
}
```

<h3 id="submitreceivedmessagessummary-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The identifier of the async report request|[AsyncReportResponse](#schemaasyncreportresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|
|501|[Not Implemented](https://tools.ietf.org/html/rfc7231#section-6.6.2)|The group_by combination is not currently implemented|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## GetReceivedMessagesSummary

<a id="opIdGetReceivedMessagesSummary"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/received_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/received_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/received_messages/summary',
  method: 'get',
  data: '?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/received_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/received_messages/summary',
  params: {
  'end_date' => 'string',
'start_date' => 'string',
'group_by' => '[group_by](#schemagroup_by)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/received_messages/summary', params={
  'end_date': "2017-02-10T13:30:00.000Z",  'start_date': "2017-02-12T13:30:00.000Z",  'group_by': 'DAY'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/received_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/received_messages/summary", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/received_messages/summary`

*getReceivedMessagesSummary*

Returns a summarised report of messages received

<h3 id="getreceivedmessagessummary-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|end_date|query|string|true|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|query|string|true|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|group_by|query|[group_by](#schemagroup_by)|true|List of fields to group results set by{array}|
|accounts|query|array[string]|false|Filter results by a specific account. By default results|
|destination_address_country|query|string|false|Filter results by destination address country.|
|destination_address|query|string|false|Filter results by destination address.|
|message_format|query|[message_format](#schemamessage_format)|false|Filter results by message format.|
|metadata_key|query|string|false|Filter results for messages that include a metadata key.|
|metadata_value|query|string|false|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|summary_by|query|[summary_by](#schemasummary_by)|false|Function to apply when summarising results|
|summary_field|query|[summary_field](#schemasummary_field)|false|Field to summarise results by|
|source_address_country|query|string|false|Filter results by source address country.|
|source_address|query|string|false|Filter results by source address.|
|timezone|query|string|false|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|

#### Detailed descriptions

**accounts**: Filter results by a specific account. By default results

will be returned for the account associated with the authentication

credentials and all sub accounts.

#### Enumerated Values

|Parameter|Value|
|---|---|
|group_by|DAY|
|group_by|DESTINATION_ADDRESS|
|group_by|DESTINATION_ADDRESS_COUNTRY|
|group_by|FORMAT|
|group_by|HOUR|
|group_by|METADATA_KEY|
|group_by|METADATA_VALUE|
|group_by|MINUTE|
|group_by|MONTH|
|group_by|SOURCE_ADDRESS|
|group_by|SOURCE_ADDRESS_COUNTRY|
|group_by|STATUS|
|group_by|STATUS_CODE|
|group_by|YEAR|
|group_by|ACCOUNT|
|message_format|SMS|
|message_format|TTS|
|summary_by|COUNT|
|summary_field|UNITS|
|summary_field|MESSAGE_ID|

> Example responses

> 200 Response

```json
{
  "properties": {
    "end_date": "2017-02-10T13:30:00.000Z",
    "start_date": "2017-02-12T13:30:00.000Z",
    "timezone": "The timezone that this report is presented in, this may be passed in as a parameter to the report, or taken from account settings"
  },
  "data": [
    {}
  ]
}
```

<h3 id="getreceivedmessagessummary-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A summarised report of all messages received in the specified time, grouped by by the specified grouping parameter|[SummaryReport](#schemasummaryreport)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|
|501|[Not Implemented](https://tools.ietf.org/html/rfc7231#section-6.6.2)|The group_by combination is not currently implemented|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## SubmitSentMessagesSummary

<a id="opIdSubmitSentMessagesSummary"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/reporting/sent_messages/summary/async \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.messagemedia.com/v1/reporting/sent_messages/summary/async HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/sent_messages/summary/async',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "group_by": [
    "DAY"
  ],
  "period": "YESTERDAY",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/sent_messages/summary/async',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.messagemedia.com/v1/reporting/sent_messages/summary/async',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.messagemedia.com/v1/reporting/sent_messages/summary/async', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/sent_messages/summary/async");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/reporting/sent_messages/summary/async", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/reporting/sent_messages/summary/async`

*submitSentMessagesSummary*

Submits a summarised report of sent messages

> Body parameter

```json
{
  "end_date": "2017-02-10T13:30:00.000Z",
  "start_date": "2017-02-12T13:30:00.000Z",
  "group_by": [
    "DAY"
  ],
  "period": "YESTERDAY",
  "timezone": "Australia/Melbourne",
  "accounts": [],
  "delivery_options": [
    {
      "delivery_type": "EMAIL",
      "delivery_addresses": [],
      "delivery_format": "CSV"
    }
  ]
}
```

<h3 id="submitsentmessagessummary-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[asyncsentmessagesrequest](#schemaasyncsentmessagesrequest)|true|none|

> Example responses

> 201 Response

```json
{
  "id": "b8ffd5b3-050a-46b9-9192-fbd7c20a22ec"
}
```

<h3 id="submitsentmessagessummary-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The identifier of the async report request|[AsyncReportResponse](#schemaasyncreportresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|
|501|[Not Implemented](https://tools.ietf.org/html/rfc7231#section-6.6.2)|The group_by combination is not currently implemented|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## GetSentMessagesSummary

<a id="opIdGetSentMessagesSummary"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/sent_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/sent_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/sent_messages/summary',
  method: 'get',
  data: '?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/sent_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/sent_messages/summary',
  params: {
  'end_date' => 'string',
'start_date' => 'string',
'group_by' => '[group_by](#schemagroup_by)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/sent_messages/summary', params={
  'end_date': "2017-02-10T13:30:00.000Z",  'start_date': "2017-02-12T13:30:00.000Z",  'group_by': 'DAY'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/sent_messages/summary?end_date=Sat%20Feb%2011%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&start_date=Mon%20Feb%2013%202017%2000%3A30%3A00%20GMT%2B1100%20%28Australian%20Eastern%20Daylight%20Time%29&group_by=DAY");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/sent_messages/summary", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/sent_messages/summary`

*getSentMessagesSummary*

Returns a summarised report of messages sent

<h3 id="getsentmessagessummary-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|end_date|query|string|true|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|query|string|true|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|group_by|query|[group_by](#schemagroup_by)|true|List of fields to group results set by{array}|
|accounts|query|array[string]|false|Filter results by a specific account. By default results|
|delivery_report|query|boolean|false|Filter results by delivery report.|
|destination_address_country|query|string|false|Filter results by destination address country.|
|destination_address|query|string|false|Filter results by destination address.|
|summary_by|query|[summary_by](#schemasummary_by)|false|Function to apply when summarising results|
|summary_field|query|[summary_field](#schemasummary_field)|false|Field to summarise results by|
|message_format|query|[message_format](#schemamessage_format)|false|Filter results by message format.|
|metadata_key|query|string|false|Filter results for messages that include a metadata key.|
|metadata_value|query|string|false|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|status_code|query|string|false|Filter results by message status code.|
|source_address_country|query|string|false|Filter results by source address country.|
|source_address|query|string|false|Filter results by source address.|
|timezone|query|string|false|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|

#### Detailed descriptions

**accounts**: Filter results by a specific account. By default results

will be returned for the account associated with the authentication

credentials and all sub accounts.

#### Enumerated Values

|Parameter|Value|
|---|---|
|group_by|DAY|
|group_by|DESTINATION_ADDRESS|
|group_by|DESTINATION_ADDRESS_COUNTRY|
|group_by|FORMAT|
|group_by|HOUR|
|group_by|METADATA_KEY|
|group_by|METADATA_VALUE|
|group_by|MINUTE|
|group_by|MONTH|
|group_by|SOURCE_ADDRESS|
|group_by|SOURCE_ADDRESS_COUNTRY|
|group_by|STATUS|
|group_by|STATUS_CODE|
|group_by|YEAR|
|group_by|ACCOUNT|
|summary_by|COUNT|
|summary_field|UNITS|
|summary_field|MESSAGE_ID|
|message_format|SMS|
|message_format|TTS|

> Example responses

> 200 Response

```json
{
  "properties": {
    "end_date": "2017-02-10T13:30:00.000Z",
    "start_date": "2017-02-12T13:30:00.000Z",
    "timezone": "The timezone that this report is presented in, this may be passed in as a parameter to the report, or taken from account settings"
  },
  "data": [
    {}
  ]
}
```

<h3 id="getsentmessagessummary-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A summarised report of all messages received in the specified time, grouped by by the specified grouping parameter|[SummaryReport](#schemasummaryreport)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Check the json response for more details on what went wrong.|None|
|501|[Not Implemented](https://tools.ietf.org/html/rfc7231#section-6.6.2)|The group_by combination is not currently implemented|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

<h1 id="messages-short-trackable-links-reports">Short Trackable Links Reports</h1>

## LogSummary

<a id="opIdLogSummary"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/links/summary \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/links/summary HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/links/summary',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/links/summary',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/links/summary',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/links/summary', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/links/summary");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/links/summary", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/links/summary`

*LogSummary*

Clicks summary report for metadata key value pair, long url and short url.

<h3 id="logsummary-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|key|query|string|false|none|
|value|query|string|false|none|
|url|query|string|false|none|
|recipient|query|string|false|none|
|page|query|number(double)|false|none|
|pageSize|query|number(double)|false|none|

> Example responses

> 200 Response

```json
{
  "total_clicks": 3,
  "unique_clicks": 1,
  "total_views": 2,
  "unique_views": 1,
  "short_urls_generated": 1,
  "short_urls": [
    {
      "click_count": 3,
      "view_count": 2,
      "message_id": "00000000-0000-0000-0000-000000000000",
      "long_url": "https://developers.messagemedia.com",
      "short_url": "https://nxt.to/abc1234",
      "destination_number": 61491570157
    }
  ],
  "pagination": {
    "page": 1,
    "page_size": 100,
    "page_count": 3
  }
}
```

<h3 id="logsummary-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[LogSummaryResult](#schemalogsummaryresult)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Invalid data provided|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Data cannot be found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|System Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## LogDetail

<a id="opIdLogDetail"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/reporting/links/detail?hash=string \
  -H 'Accept: application/json'

```

```http
GET https://api.messagemedia.com/v1/reporting/links/detail?hash=string HTTP/1.1
Host: api.messagemedia.com
Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/reporting/links/detail',
  method: 'get',
  data: '?hash=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.messagemedia.com/v1/reporting/links/detail?hash=string',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.messagemedia.com/v1/reporting/links/detail',
  params: {
  'hash' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.messagemedia.com/v1/reporting/links/detail', params={
  'hash': 'string'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/reporting/links/detail?hash=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/reporting/links/detail", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/reporting/links/detail`

*LogDetail*

Detailed clicks report for a hashcode.

<h3 id="logdetail-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|hash|query|string|true|none|
|page|query|number(double)|false|none|
|pageSize|query|number(double)|false|none|

> Example responses

> 200 Response

```json
{
  "message_id": "00000000-0000-0000-0000-000000000000",
  "long_url": "https://developers.messagemedia.com",
  "short_url": "https://nxt.to/abc1234",
  "destination_number": 61491570157,
  "click_count": 3,
  "view_count": 2,
  "clicks": [
    {
      "dt": "2018-09-18T01:22:17.071Z",
      "user_agent": "Mozilla/5.0 (Windows NT...",
      "ip": "127.0.0.1"
    }
  ],
  "views": [
    {
      "dt": "2018-09-18T01:22:17.071Z",
      "user_agent": "Mozilla/5.0 (Windows NT...",
      "ip": "127.0.0.1"
    }
  ],
  "pagination": {
    "page": 1,
    "page_size": 100,
    "page_count": 3
  }
}
```

<h3 id="logdetail-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[LogsDetailResult](#schemalogsdetailresult)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request. Invalid data provided|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Data cannot be found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|System Error|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

<h1 id="messages-webhooks-management">Webhooks Management</h1>

Webhooks Management API allows you to manage your webhooks configuration. You can subscribe to one or several events, retrieve the webhooks, update them or even delete them if needed.
[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/4484dfbb1fef44e53094)

## CreateWebhook

<a id="opIdCreateWebhook"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.messagemedia.com/v1/webhooks/messages \
  -H 'Content-Type: application/json' \
  -H 'Accept: text/plain'

```

```http
POST https://api.messagemedia.com/v1/webhooks/messages HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: text/plain

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/webhooks/messages',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "url": "http://webhook.com",
  "method": "POST",
  "encoding": "JSON",
  "headers": {
    "Account": "DeveloperPortal7000"
  },
  "events": [
    "ENROUTE_DR",
    "DELIVERED_DR"
  ],
  "template": "{\"id\":\"$mtId\",\"status\":\"$statusCode\"}"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

fetch('https://api.messagemedia.com/v1/webhooks/messages',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'text/plain'
}

result = RestClient.post 'https://api.messagemedia.com/v1/webhooks/messages',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'text/plain'
}

r = requests.post('https://api.messagemedia.com/v1/webhooks/messages', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/webhooks/messages");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://api.messagemedia.com/v1/webhooks/messages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/webhooks/messages`

*Create Webhook*

Create a webhook for one or more of the specified events.

A webhook would typically have the following structure:

```
{
  "url": "http://webhook.com",
  "method": "POST",
  "encoding": "JSON",
  "headers": {
    "Account": "DeveloperPortal7000"
  },
  "events": [
    "RECEIVED_SMS"
  ],
  "template": "{\"id\":\"$mtId\",\"status\":\"$statusCode\"}"
}
```

A valid webhook must consist of the following properties:

- ```url``` The configured URL which will trigger the webhook when a selected event occurs.

- ```method``` The methods to map CRUD (create, retrieve, update, delete) operations to HTTP requests.

- ```encoding``` Webhooks can be delivered using different content types. You can choose from ```JSON```, ```FORM_ENCODED``` or ```XML```. This will automatically add the Content-Type header for you so you don't have to add it again in the `headers` property.

- ```headers``` HTTP header fields which provide required information about the request or response, or about the object sent in the message body. This should NOT include the `Content-Type` header.

- ```events``` Event or events that will trigger the webhook. Atleast one event should be present.

- ```template``` The structure of the payload that will be returned. You can format this in JSON or XML.

#### Types of Events

You can select all of the events (listed below) or combine them in whatever way you like but atleast one event must be used. Otherwise, the webhook won't be created.

A webhook will be triggered when any one or more of the events occur:

+ **SMS**
    + `RECEIVED_SMS` Receive an SMS
    + `OPT_OUT_SMS` Opt-out occured

+ **MMS**
    + `RECEIVED_MMS` Receive an MMS

+ **DR (Delivery Reports)**
    + `ENROUTE_DR` Message is enroute
    + `EXPIRED_DR` Message has expired
    + `REJECTED_DR` Message is rejected
    + `FAILED_DR` Message has failed 
    + `DELIVERED_DR` Message is delivered
    + `SUBMITTED_DR` Message is submitted

#### Template Parameters

You can choose what to include in the data that will be sent as the payload via the Webhook. It's upto you to choose what format you would like the payload to be returned. You can choose between JSON or XML.
Keep in my mind, if you've chosen JSON as the format, you must escape the JSON in the template value (see example above).

The table illustrates a list of all the parameters that can be included in the template and which event types it can be applied to.

| Data  | Parameter Name | Example | Event Type |
|:--|--|--|--|--|
| **Service Type**  | $type| `SMS` | `DR` `MO` `MO MMS` |
| **Message ID**  | $mtId, $messageId| `877c19ef-fa2e-4cec-827a-e1df9b5509f7` | `DR` `MO` `MO MMS`|
| **Delivery Report ID** |$drId, $reportId| `01e1fa0a-6e27-4945-9cdb-18644b4de043` | `DR` |
| **Reply ID**| $moId, $replyId| `a175e797-2b54-468b-9850-41a3eab32f74` | `MO` `MO MMS` |
| **Account ID**  | $accountId| `DeveloperPortal7000` | `DR` `MO` `MO MMS` |
| **Message Timestamp**  | $submittedTimestamp| `2016-12-07T08:43:00.850Z` | `DR` `MO` `MO MMS` |
| **Provider Timestamp**  | $receivedTimestamp| `2016-12-07T08:44:00.850Z` | `DR` `MO` `MO MMS` |
| **Message Status** | $status| `enroute` | `DR` |
| **Status Code**  | $statusCode| `200` | `DR` |
| **External Metadata** | $metadata.get('key')| `name` | `DR` `MO` `MO MMS` |
| **Source Address**| $sourceAddress| `+61491570156` | `DR` `MO` `MO MMS` |
| **Destination Address**| $destinationAddress| `+61491593156` | `MO` `MO MMS` |
| **Message Content**| $mtContent, $messageContent| `Hi Derp` | `DR` `MO` `MO MMS` |
| **Reply Content**| $moContent, $replyContent| `Hello Derpina` | `MO` `MO MMS` |
| **Retry Count**| $retryCount| `1` | `DR` `MO` `MO MMS` |

*Note: A 400 response will be returned if the `url` is invalid, the `events`, `encoding` or `method` is null or the `headers` has a Content-Type  attribute.*

> Body parameter

```json
{
  "url": "http://webhook.com",
  "method": "POST",
  "encoding": "JSON",
  "headers": {
    "Account": "DeveloperPortal7000"
  },
  "events": [
    "ENROUTE_DR",
    "DELIVERED_DR"
  ],
  "template": "{\"id\":\"$mtId\",\"status\":\"$statusCode\"}"
}
```

<h3 id="createwebhook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CreateWebhookrequest](#schemacreatewebhookrequest)|true|none|

> Example responses

> 201 Response

> 400 Response

```json
{
  "message": "Something went wrong. Please try again later."
}
```

> 409 Response

```json
{
  "message": "A webhook with the given url and method already exists."
}
```

<h3 id="createwebhook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Webhook successfully created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Unexpected error in API call. See HTTP response body for details.|[UpdateWebhook400response](#schemaupdatewebhook400response)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Unexpected error in API call. See HTTP response body for details.|[UpdateWebhook400response](#schemaupdatewebhook400response)|

<h3 id="createwebhook-responseschema">Response Schema</h3>

Status Code **201**

*Webhook successfully created*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## RetrieveWebhook

<a id="opIdRetrieveWebhook"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.messagemedia.com/v1/webhooks/messages/ \
  -H 'Accept: text/plain'

```

```http
GET https://api.messagemedia.com/v1/webhooks/messages/ HTTP/1.1
Host: api.messagemedia.com
Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/webhooks/messages/',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'text/plain'

};

fetch('https://api.messagemedia.com/v1/webhooks/messages/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain'
}

result = RestClient.get 'https://api.messagemedia.com/v1/webhooks/messages/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.get('https://api.messagemedia.com/v1/webhooks/messages/', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/webhooks/messages/");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.messagemedia.com/v1/webhooks/messages/", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/webhooks/messages/`

*Retrieve Webhook*

Retrieve all the webhooks created for the connected account.
A successful request to the retrieve webhook endpoint will return a response body as follows:

```
{
    "page": 0,
    "pageSize": 100,
    "pageData": [
        {
            "url": "https://webhook.com",
            "method": "POST",
            "id": "8805c9d8-bef7-41c7-906a-69ede93aa024",
            "encoding": "JSON",
            "events": [
                "RECEIVED_SMS"
            ],
            "headers": {},
            "template": "{\"id\":\"$mtId\", \"status\":\"$statusCode\"}"
        }
    ]
}
```

*Note: Response 400 is returned when the `page` query parameter is not valid or the `pageSize` query parameter is not valid.*

<h3 id="retrievewebhook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer(int32)|false|none|
|pageSize|query|integer(int32)|false|none|

> Example responses

> 200 Response

> 400 Response

```json
{
  "message": "Something went wrong. Please try again later."
}
```

<h3 id="retrievewebhook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Unexpected error in API call. See HTTP response body for details.|[UpdateWebhook400response](#schemaupdatewebhook400response)|

<h3 id="retrievewebhook-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## DeleteWebhook

<a id="opIdDeleteWebhook"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.messagemedia.com/v1/webhooks/messages/{webhookId}

```

```http
DELETE https://api.messagemedia.com/v1/webhooks/messages/{webhookId} HTTP/1.1
Host: api.messagemedia.com

```

```javascript

$.ajax({
  url: 'https://api.messagemedia.com/v1/webhooks/messages/{webhookId}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

fetch('https://api.messagemedia.com/v1/webhooks/messages/{webhookId}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.delete 'https://api.messagemedia.com/v1/webhooks/messages/{webhookId}',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.delete('https://api.messagemedia.com/v1/webhooks/messages/{webhookId}', params={

)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/webhooks/messages/{webhookId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://api.messagemedia.com/v1/webhooks/messages/{webhookId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /v1/webhooks/messages/{webhookId}`

*Delete Webhook*

Delete a webhook that was previously created for the connected account.
A webhook can be cancelled by appending the UUID of the webhook to the endpoint and submitting a DELETE request to the /webhooks/messages endpoint.

A successful request to the retrieve webhook endpoint will return a null response.

*Note: Only pre-created webhooks can be deleted. If an invalid or non existent webhook ID parameter is specified in the request, then a HTTP 404 Not Found response will be returned.*

<h3 id="deletewebhook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|webhookId|path|string(uuid)|true|none|

<h3 id="deletewebhook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Webhook deleted successfully|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|none|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

## UpdateWebhook

<a id="opIdUpdateWebhook"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.messagemedia.com/v1/webhooks/messages/{webhookId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: text/plain'

```

```http
PATCH https://api.messagemedia.com/v1/webhooks/messages/{webhookId} HTTP/1.1
Host: api.messagemedia.com
Content-Type: application/json
Accept: text/plain

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

$.ajax({
  url: 'https://api.messagemedia.com/v1/webhooks/messages/{webhookId}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "url": "https://myurl.com",
  "method": "POST",
  "encoding": "FORM_ENCODED",
  "events": [
    "ENROUTE_DR"
  ],
  "template": "{\"id\":\"$mtId\", \"status\":\"$statusCode\"}"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'text/plain'

};

fetch('https://api.messagemedia.com/v1/webhooks/messages/{webhookId}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'text/plain'
}

result = RestClient.patch 'https://api.messagemedia.com/v1/webhooks/messages/{webhookId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'text/plain'
}

r = requests.patch('https://api.messagemedia.com/v1/webhooks/messages/{webhookId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("https://api.messagemedia.com/v1/webhooks/messages/{webhookId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://api.messagemedia.com/v1/webhooks/messages/{webhookId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /v1/webhooks/messages/{webhookId}`

*Update Webhook*

Update a webhook. You can update individual attributes or all of them by submitting a PATCH request to the /webhooks/messages endpoint (the same endpoint used above to delete a webhook)

A successful request to the retrieve webhook endpoint will return a response body as follows:

```
{
    "url": "https://webhook.com",
    "method": "POST",
    "id": "04442623-0961-464e-9cbc-ec50804e0413",
    "encoding": "JSON",
    "events": [
        "RECEIVED_SMS"
    ],
    "headers": {},
    "template": "{\"id\":\"$mtId\", \"status\":\"$statusCode\"}"
}
```

*Note: Only pre-created webhooks can be deleted. If an invalid or non existent webhook ID parameter is specified in the request, then a HTTP 404 Not Found response will be returned.*

> Body parameter

```json
{
  "url": "https://myurl.com",
  "method": "POST",
  "encoding": "FORM_ENCODED",
  "events": [
    "ENROUTE_DR"
  ],
  "template": "{\"id\":\"$mtId\", \"status\":\"$statusCode\"}"
}
```

<h3 id="updatewebhook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|webhookId|path|string(uuid)|true|none|
|body|body|[UpdateWebhookrequest](#schemaupdatewebhookrequest)|true|none|

> Example responses

> 200 Response

> 400 Response

```json
{
  "message": "Something went wrong. Please try again later."
}
```

<h3 id="updatewebhook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Webhook updated successfully|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Unexpected error in API call. See HTTP response body for details.|[UpdateWebhook400response](#schemaupdatewebhook400response)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|none|None|

<h3 id="updatewebhook-responseschema">Response Schema</h3>

Status Code **200**

*Webhook updated successfully*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
httpBasic
</aside>

# Schemas

<h2 id="tocSconfirmdeliveryreportsasreceivedrequest">Confirmdeliveryreportsasreceivedrequest</h2>

<a id="schemaconfirmdeliveryreportsasreceivedrequest"></a>

```yaml
delivery_report_ids:
  - 011dcead-6988-4ad6-a1c7-6b6c68ea628d
  - 3487b3fa-6586-4979-a233-2d1b095c7718
  - ba28e94b-c83d-4759-98e7-ff9c7edb87a1

```

*Confirmdeliveryreportsasreceivedrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|delivery_report_ids|[string]|true|none|none|

<h2 id="tocScheckdeliveryreportsresponse">Checkdeliveryreportsresponse</h2>

<a id="schemacheckdeliveryreportsresponse"></a>

```yaml
delivery_reports:
  - callback_url: 'https://my.callback.url.com'
    delivery_report_id: 01e1fa0a-6e27-4945-9cdb-18644b4de043
    source_number: '+61491570157'
    date_received: '2017-05-20T06:30:37.642Z'
    status: enroute
    delay: 0
    submitted_date: '2017-05-20T06:30:37.639Z'
    original_text: My first message!
    message_id: d781dcab-d9d8-4fb2-9e03-872f07ae94ba
    vendor_account_id:
      vendor_id: MessageMedia
      account_id: MyAccount
    metadata:
      key1: value1
      key2: value2
  - callback_url: 'https://my.callback.url.com'
    delivery_report_id: 0edf9022-7ccc-43e6-acab-480e93e98c1b
    source_number: '+61491570158'
    date_received: '2017-05-21T01:46:42.579Z'
    status: submitted
    delay: 0
    submitted_date: '2017-05-21T01:46:42.574Z'
    original_text: My second message!
    message_id: fbb3b3f5-b702-4d8b-ab44-65b2ee39a281
    vendor_account_id:
      vendor_id: MessageMedia
      account_id: MyAccount
    metadata:
      key1: value1
      key2: value2

```

*Checkdeliveryreportsresponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|delivery_reports|[[DeliveryReport](#schemadeliveryreport)]|false|none|The oldest 100 unconfirmed delivery reports|

<h2 id="tocSconfirmrepliesasreceivedrequest">Confirmrepliesasreceivedrequest</h2>

<a id="schemaconfirmrepliesasreceivedrequest"></a>

```yaml
reply_ids:
  - 011dcead-6988-4ad6-a1c7-6b6c68ea628d
  - 3487b3fa-6586-4979-a233-2d1b095c7718
  - ba28e94b-c83d-4759-98e7-ff9c7edb87a1

```

*Confirmrepliesasreceivedrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|reply_ids|[string]|true|none|none|

<h2 id="tocSvendoraccountid">VendorAccountId</h2>

<a id="schemavendoraccountid"></a>

```yaml
vendor_id: MessageMedia
account_id: MyAccount001

```

*VendorAccountId*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|vendor_id|string|false|none|none|
|account_id|string|false|none|The account used to submit the original message.|

<h2 id="tocScheckrepliesresponse">Checkrepliesresponse</h2>

<a id="schemacheckrepliesresponse"></a>

```yaml
replies:
  - metadata:
      key1: value1
      key2: value2
    message_id: 877c19ef-fa2e-4cec-827a-e1df9b5509f7
    reply_id: a175e797-2b54-468b-9850-41a3eab32f74
    date_received: '2016-12-07T08:43:00.850Z'
    callback_url: 'https://my.callback.url.com'
    destination_number: '+61491570156'
    source_number: '+61491570157'
    vendor_account_id:
      vendor_id: MessageMedia
      account_id: MyAccount
    content: My first reply!
  - metadata:
      key1: value1
      key2: value2
    message_id: 8f2f5927-2e16-4f1c-bd43-47dbe2a77ae4
    reply_id: 3d8d53d8-01d3-45dd-8cfa-4dfc81600f7f
    date_received: '2016-12-07T08:43:00.850Z'
    callback_url: 'https://my.callback.url.com'
    destination_number: '+61491570157'
    source_number: '+61491570158'
    vendor_account_id:
      vendor_id: MessageMedia
      account_id: MyAccount
    content: My second reply!

```

*Checkrepliesresponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|replies|[[Reply](#schemareply)]|false|none|The oldest 100 unconfirmed replies|

<h2 id="tocSsourcenumbertype">SourceNumberType</h2>

<a id="schemasourcenumbertype"></a>

```yaml
INTERNATIONAL

```

*SourceNumberType*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|SourceNumberType|string|false|none|Type of source address specified, this can be INTERNATIONAL, ALPHANUMERIC or SHORTCODE|

#### Enumerated Values

|Property|Value|
|---|---|
|SourceNumberType|INTERNATIONAL|
|SourceNumberType|ALPHANUMERIC|
|SourceNumberType|SHORTCODE|

<h2 id="tocScancelscheduledmessagerequest">Cancelscheduledmessagerequest</h2>

<a id="schemacancelscheduledmessagerequest"></a>

```yaml
status: cancelled

```

*Cancelscheduledmessagerequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|string|true|none|none|

<h2 id="tocSsendmessages400response">Sendmessages400response</h2>

<a id="schemasendmessages400response"></a>

```yaml
message: Something went wrong. Please try again later.

```

*Sendmessages400response*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message|string|true|none|none|

<h2 id="tocSsendmessagesrequest">Sendmessagesrequest</h2>

<a id="schemasendmessagesrequest"></a>

```yaml
messages:
  - callback_url: 'https://my.callback.url.com'
    content: My first message
    destination_number: '+61491570156'
    delivery_report: true
    format: SMS
    message_expiry_timestamp: '2016-11-03T11:49:02.807Z'
    metadata:
      key1: value1
      key2: value2
    scheduled: '2016-11-03T11:49:02.807Z'
    source_number: '+61491570157'
    source_number_type: INTERNATIONAL
  - callback_url: 'https://my.callback.url.com'
    content: My second message
    destination_number: '+61491570158'
    delivery_report: true
    format: MMS
    subject: This is an MMS message
    media:
      - >-
        https://images.pexels.com/photos/1018350/pexels-photo-1018350.jpeg?cs=srgb&dl=architecture-buildings-city-1018350.jpg
    message_expiry_timestamp: '2016-11-03T11:49:02.807Z'
    metadata:
      key1: value1
      key2: value2
    scheduled: '2016-11-03T11:49:02.807Z'
    source_number: '+61491570159'
    source_number_type: INTERNATIONAL

```

*Sendmessagesrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|messages|[[Message](#schemamessage)]|true|none|none|

<h2 id="tocSreply">Reply</h2>

<a id="schemareply"></a>

```yaml
callback_url: 'https://my.url.com'
content: Hello back
date_received: '11/3/2016 11:49:02 AM'
destination_number: '+61491570156'
message_id: string
metadata: {}
reply_id: string
source_number: '+61491570156'
vendor_account_id:
  vendor_id: MessageMedia
  account_id: MyAccount001

```

*Reply*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|callback_url|string|false|none|The URL specified as the callback URL in the original submit message request|
|content|string|false|none|Content of the reply|
|date_received|string(date-time)|false|none|Date time when the reply was received|
|destination_number|string|false|none|Address from which this reply was sent to|
|message_id|string(uuid)|false|none|Unique ID of the original message|
|metadata|object|false|none|Any metadata that was included in the original submit message request|
|reply_id|string(uuid)|false|none|Unique ID of this reply|
|source_number|string|false|none|Address from which this reply was received from|
|vendor_account_id|[VendorAccountId](#schemavendoraccountid)|false|none|none|

<h2 id="tocSdeliveryreport">DeliveryReport</h2>

<a id="schemadeliveryreport"></a>

```yaml
callback_url: 'https://my.url.com'
date_received: '11/3/2016 11:49:02 AM'
delay: 0
delivery_report_id: string
message_id: string
metadata: {}
original_text: Hello back
source_number: '+61491570156'
status: enroute
submitted_date: '11/3/2016 11:49:02 AM'
vendor_account_id:
  vendor_id: MessageMedia
  account_id: MyAccount001

```

*DeliveryReport*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|callback_url|string|false|none|The URL specified as the callback URL in the original submit message request|
|date_received|string(date-time)|false|none|The date and time at which this delivery report was generated in UTC.|
|delay|integer(int32)|false|none|Deprecated, no longer in use|
|delivery_report_id|string(uuid)|false|none|Unique ID for this delivery report|
|message_id|string(uuid)|false|none|Unique ID of the original message|
|metadata|object|false|none|Any metadata that was included in the original submit message request|
|original_text|string|false|none|Text of the original message.|
|source_number|string|false|none|Address from which this delivery report was received|
|status|[Status](#schemastatus)|false|none|The status of the message|
|submitted_date|string(date-time)|false|none|The date and time when the message status changed in UTC. For a delivered DR this may indicate the time at which the message was received on the handset.|
|vendor_account_id|[VendorAccountId](#schemavendoraccountid)|false|none|none|

<h2 id="tocSgetmessagestatusresponse">Getmessagestatusresponse</h2>

<a id="schemagetmessagestatusresponse"></a>

```yaml
callback_url: 'https://my.url.com'
content: Hello world!
destination_number: '+61491570156'
delivery_report: false
format: SMS
message_expiry_timestamp: '11/3/2016 11:49:02 AM'
metadata: {}
scheduled: '11/3/2016 11:49:02 AM'
source_number: '+61491570156'
source_number_type: INTERNATIONAL
message_id: string
status: enroute

```

*Getmessagestatusresponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|callback_url|string|false|none|URL replies and delivery reports to this message will be pushed to|
|content|string|false|none|Content of the message|
|destination_number|string|false|none|Destination number of the message|
|delivery_report|boolean|false|none|Request a delivery report for this message|
|format|[Format](#schemaformat)|false|none|Format of message, SMS or TTS (Text To Speech).|
|message_expiry_timestamp|string(date-time)|false|none|Date time after which the message expires and will not be sent|
|metadata|object|false|none|Metadata for the message specified as a set of key value pairs, each key can be up to 100 characters long and each value can be up to 256 characters long ``` {    "myKey": "myValue",    "anotherKey": "anotherValue" } ```|
|scheduled|string(date-time)|false|none|Scheduled delivery date time of the message|
|source_number|string|false|none|none|
|source_number_type|[SourceNumberType](#schemasourcenumbertype)|false|none|Type of source address specified, this can be INTERNATIONAL, ALPHANUMERIC or SHORTCODE|
|message_id|string(uuid)|false|none|Unique ID of this message|
|status|[Status](#schemastatus)|false|none|The status of the message|

<h2 id="tocSstatus">Status</h2>

<a id="schemastatus"></a>

```yaml
enroute

```

*Status*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Status|string|false|none|The status of the message|

#### Enumerated Values

|Property|Value|
|---|---|
|Status|enroute|
|Status|submitted|
|Status|delivered|
|Status|expired|
|Status|rejected|
|Status|undeliverable|
|Status|queued|
|Status|processed|
|Status|cancelled|
|Status|scheduled|
|Status|failed|

<h2 id="tocSmessage">Message</h2>

<a id="schemamessage"></a>

```yaml
callback_url: 'https://my.url.com'
content: Hello world!
destination_number: '+61491570156'
delivery_report: false
format: SMS
message_expiry_timestamp: '11/3/2016 11:49:02 AM'
metadata: {}
scheduled: '11/3/2016 11:49:02 AM'
source_number: '+61491570156'
source_number_type: INTERNATIONAL
message_id: string
status: enroute
media:
  - string
subject: string

```

*Message*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|callback_url|string|false|none|URL replies and delivery reports to this message will be pushed to|
|content|string|true|none|Content of the message|
|destination_number|string|true|none|Destination number of the message|
|delivery_report|boolean|false|none|Request a delivery report for this message|
|format|[Format](#schemaformat)|false|none|Format of message, SMS or TTS (Text To Speech).|
|message_expiry_timestamp|string(date-time)|false|none|Date time after which the message expires and will not be sent|
|metadata|object|false|none|Metadata for the message specified as a set of key value pairs, each key can be up to 100 characters long and each value can be up to 256 characters long ``` {    "myKey": "myValue",    "anotherKey": "anotherValue" } ```|
|scheduled|string(date-time)|false|none|Scheduled delivery date time of the message|
|source_number|string|false|none|none|
|source_number_type|[SourceNumberType](#schemasourcenumbertype)|false|none|Type of source address specified, this can be INTERNATIONAL, ALPHANUMERIC or SHORTCODE|
|message_id|string(uuid)|false|none|Unique ID of this message|
|status|[Status](#schemastatus)|false|none|The status of the message|
|media|[string]|false|none|The media is used to specify the url of the media file that you are trying to send. Supported file formats include png, jpeg and gif. format parameter must be set to MMS for this to work.|
|subject|string|false|none|The subject field is used to denote subject of the MMS message and has a maximum size of 64 characters long|

<h2 id="tocSsendmessagesresponse">Sendmessagesresponse</h2>

<a id="schemasendmessagesresponse"></a>

```yaml
messages:
  - callback_url: 'https://my.url.com'
    content: Hello world!
    destination_number: '+61491570156'
    delivery_report: false
    format: SMS
    message_expiry_timestamp: '11/3/2016 11:49:02 AM'
    metadata: {}
    scheduled: '11/3/2016 11:49:02 AM'
    source_number: '+61491570156'
    source_number_type: INTERNATIONAL
    message_id: string
    status: enroute
    media:
      - string
    subject: string

```

*Sendmessagesresponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|messages|[[Message](#schemamessage)]|false|none|none|

<h2 id="tocSformat">Format</h2>

<a id="schemaformat"></a>

```yaml
SMS

```

*Format*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Format|string|false|none|Format of message, SMS or TTS (Text To Speech).|

#### Enumerated Values

|Property|Value|
|---|---|
|Format|SMS|
|Format|TTS|
|Format|MMS|

<h2 id="tocSlookupaphonenumberresponse">Lookupaphonenumberresponse</h2>

<a id="schemalookupaphonenumberresponse"></a>

```yaml
country_code: AU
phone_number: 61491570156
type: mobile
carrier:
  name: Telstra

```

*Lookupaphonenumberresponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|country_code|string|true|none|none|
|phone_number|string|true|none|none|
|type|string|true|none|none|
|carrier|[Carrier](#schemacarrier)|true|none|none|
|result|string|true|none|none|
|imsi|integer(int64)|true|none|A unique number identifying a GSM subscriber|
|location|integer(int32)|true|none|The location of the mobile number|

<h2 id="tocScarrier">Carrier</h2>

<a id="schemacarrier"></a>

```yaml
name: string

```

*Carrier*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|

<h2 id="tocSlookupaphonenumber404response">Lookupaphonenumber404response</h2>

<a id="schemalookupaphonenumber404response"></a>

```yaml
message: The number could not be found or is invalid.

```

*Lookupaphonenumber404response*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message|string|true|none|none|

<h2 id="tocSmetadatakeysresponse">MetadataKeysResponse</h2>

<a id="schemametadatakeysresponse"></a>

```yaml
data: []
properties:
  end_date: 2017-02-10T13:30:00.000Z
  start_date: 2017-02-12T13:30:00.000Z
  accounts: []

```

*MetadataKeysResponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[string]|false|none|none|
|properties|[Properties](#schemaproperties)|false|none|none|

<h2 id="tocSproperties">Properties</h2>

<a id="schemaproperties"></a>

```yaml
end_date: 2019-11-20T03:52:53.019Z
start_date: 2019-11-20T03:52:53.019Z
accounts:
  - string

```

*Properties*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|end_date|string|true|none|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|string|true|none|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|accounts|[string]|false|none|List of accounts that were considered when fetching the metadata keys.|

<h2 id="tocSdeliveryoptionsbody">deliveryOptionsBody</h2>

<a id="schemadeliveryoptionsbody"></a>

```yaml
delivery_type: EMAIL
delivery_addresses:
  - string
delivery_format: CSV

```

*deliveryOptionsBody*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|delivery_type|string|false|none|How to deliver the report.|
|delivery_addresses|[string]|false|none|A list of email addresses to use as the recipient of the email. Only works for EMAIL delivery type|
|delivery_format|string|false|none|Format of the report.|

<h2 id="tocSpagination">Pagination</h2>

<a id="schemapagination"></a>

```yaml
page: 0
page_size: 0
total_count: 0
page_count: 0
next_uri: string
previous_uri: string

```

*Pagination*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page|number|false|none|The current page of results|
|page_size|number|false|none|The amount of results returned per page|
|total_count|number|false|none|The total number of results in the results set|
|page_count|number|false|none|The total number of pages in the results set|
|next_uri|string|false|none|Link to the next page of results|
|previous_uri|string|false|none|Link to the previous page of results|

<h2 id="tocSreportingdetailproperties">ReportingDetailProperties</h2>

<a id="schemareportingdetailproperties"></a>

```yaml
end_date: 2019-11-20T03:52:53.019Z
start_date: 2019-11-20T03:52:53.019Z
sorting:
  field: ACCOUNT
  order: ASCENDING
filters:
  delivery_report: string
  destination_address_country: string
  destination_address: string
  message_format: string
  metadata_key: string
  metadata_value: string
  source_address_country: string
  source_address: string
  status_code: string
  status: string
  action: string
  accounts:
    - string
timezone: >-
  The timezone that this report is presented in, this may be passed in as a
  parameter to the report, or taken from account settings

```

*ReportingDetailProperties*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|end_date|string|true|none|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|string|true|none|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|sorting|[Sorting](#schemasorting)|false|none|none|
|filters|[Filters](#schemafilters)|false|none|none|
|timezone|string|false|none|none|

<h2 id="tocSsorting">Sorting</h2>

<a id="schemasorting"></a>

```yaml
field: ACCOUNT
order: ASCENDING

```

*Sorting*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|field|[field](#schemafield)|false|none|The value of the sort_by field provided for this report|
|order|[order](#schemaorder)|false|none|The value of the sort_direction field provided for this report|

<h2 id="tocSfilters">Filters</h2>

<a id="schemafilters"></a>

```yaml
delivery_report: string
destination_address_country: string
destination_address: string
message_format: string
metadata_key: string
metadata_value: string
source_address_country: string
source_address: string
status_code: string
status: string
action: string
accounts:
  - string

```

*Filters*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|delivery_report|string|false|none|none|
|destination_address_country|string|false|none|none|
|destination_address|string|false|none|none|
|message_format|string|false|none|none|
|metadata_key|string|false|none|none|
|metadata_value|string|false|none|none|
|source_address_country|string|false|none|none|
|source_address|string|false|none|none|
|status_code|string|false|none|none|
|status|string|false|none|none|
|action|string|false|none|none|
|accounts|[string]|false|none|List of accounts that were used to generate this report|

<h2 id="tocSasyncreport">AsyncReport</h2>

<a id="schemaasyncreport"></a>

```yaml
created_datetime: 2017-02-12T13:30:00.000Z
last_modified_datetime: 2017-02-12T13:30:00.000Z

```

*AsyncReport*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|Unique ID for this reply|
|message_type|[message_type](#schemamessage_type)|false|none|none|
|type|[type](#schematype)|false|none|none|
|report_status|[report_status](#schemareport_status)|false|none|none|
|created_datetime|string|false|none|Date time at which this report was created.|
|last_modified_datetime|string|false|none|Date time at which this report was last modified.|

<h2 id="tocSreceivedmessage">ReceivedMessage</h2>

<a id="schemareceivedmessage"></a>

```yaml
account: MyAccount001
action: MyAccount001
content: Hello back
destination_address: 61491570156
destination_address_country: AU
format: AU
id: string
in_response_to: string
metadata: {}
source_address: 61491570156
source_address_country: AU
timestamp: 2019-11-20T03:52:53.020Z

```

*ReceivedMessage*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account|string|false|none|Account associated with this message|
|action|[action](#schemaaction)|false|none|Action that was invoked for this message if any, OPT_OUT, OPT_IN, GLOBAL_OPT_OUT|
|content|string|false|none|Content of the message|
|destination_address|string|false|none|Address this message was delivered to. If this message was received in response to a sent message, this is the source address of the sent message|
|destination_address_country|string|false|none|Country associated with the destination address|
|format|[format](#schemaformat)|false|none|Format of message, SMS or TTS (Text To Speech)|
|id|string|false|none|Unique ID for this reply|
|in_response_to|string|false|none|If this message was received in response to a sent message, this is the ID of the sent message|
|metadata|object|false|none|If this message was received in response to a sent message, this is the metadata associated with the sent message|
|source_address|string|false|none|Address this message was received from. If this message was received in response to a sent message, this is the destination address of the sent message.|
|source_address_country|string|false|none|Country associated with the source address|
|timestamp|string|false|none|Date time at which this message was received|

<h2 id="tocSreceivedmessages">ReceivedMessages</h2>

<a id="schemareceivedmessages"></a>

```yaml
data:
  - account: MyAccount001
    action: MyAccount001
    content: Hello back
    destination_address: 61491570156
    destination_address_country: AU
    format: AU
    source_address: 61491570156
    source_address_country: AU
    timestamp: 2017-02-12T13:30:00.000Z
pagination: {}
properties:
  end_date: 2017-02-10T13:30:00.000Z
  start_date: 2017-02-12T13:30:00.000Z
  sorting: {}
  filters:
    accounts: []
  timezone: >-
    The timezone that this report is presented in, this may be passed in as a
    parameter to the report, or taken from account settings

```

*ReceivedMessages*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[ReceivedMessage](#schemareceivedmessage)]|false|none|List of received messages|
|pagination|[Pagination](#schemapagination)|false|none|none|
|properties|[ReportingDetailProperties](#schemareportingdetailproperties)|false|none|none|

<h2 id="tocSsentmessage">SentMessage</h2>

<a id="schemasentmessage"></a>

```yaml
account: MyAccount001
content: Hello world!
delivered_timestamp: 2019-11-20T03:52:53.021Z
delivery_report: true
destination_address: 61491570156
destination_address_country: AU
format: AU
id: string
in_response_to: string
metadata: {}
source_address: 61491570156
source_address_country: AU
units: 2
timestamp: 2019-11-20T03:52:53.021Z

```

*SentMessage*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account|string|false|none|Account associated with this message|
|content|string|false|none|Content of the message|
|delivered_timestamp|string|false|none|If a delivery report was requested for this message, this is the time at which the message was delivered (or failed to be delivered) to the destination address.|
|delivery_report|boolean|false|none|Indicates if a delivery report was requested for this message|
|destination_address|string|false|none|Address this message was delivered to|
|destination_address_country|string|false|none|Country associated with the destination address|
|format|[format](#schemaformat)|false|none|Format of message, SMS or TTS (Text To Speech)|
|id|string|false|none|Unique ID for this message|
|in_response_to|string|false|none|If this message was sent in response to a received message (an auto response message for example) this is the ID of the received message.|
|metadata|object|false|none|Metadata associated with this message|
|source_address|string|false|none|Address this message was sent from|
|source_address_country|string|false|none|Country associated with the source address|
|units|number|false|none|The total number of calculated SMS units this message cost. 1 SMS unit is defined as 160 GSM characters, or 153 GSM characters for multi-part messages as some characters are used to concatenate the message on the receiving handset.  Messages with one or more non-GSM characters will be submitted using UCS-2 encoding. UCS-2 encoding means the message has a maximum of 70 characters per SMS, or 67 characters for multi-part messages.|
|timestamp|string|false|none|Date time at which this message was submitted to the API, refer to the delivered timestamp for the time at which the message was delivered (or failed to be delivered) to the destination address.|

<h2 id="tocSsentmessages">SentMessages</h2>

<a id="schemasentmessages"></a>

```yaml
data:
  - account: MyAccount001
    content: Hello world!
    delivered_timestamp: 2017-02-12T13:30:00.000Z
    destination_address: 61491570156
    destination_address_country: AU
    format: AU
    source_address: 61491570156
    source_address_country: AU
    units: 2
    timestamp: 2017-02-12T13:30:00.000Z
pagination: {}
properties:
  end_date: 2017-02-10T13:30:00.000Z
  start_date: 2017-02-12T13:30:00.000Z
  sorting: {}
  filters:
    accounts: []
  timezone: >-
    The timezone that this report is presented in, this may be passed in as a
    parameter to the report, or taken from account settings

```

*SentMessages*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[SentMessage](#schemasentmessage)]|false|none|List of sent messages|
|pagination|[Pagination](#schemapagination)|false|none|none|
|properties|[ReportingDetailProperties](#schemareportingdetailproperties)|false|none|none|

<h2 id="tocSasyncreportresponse">AsyncReportResponse</h2>

<a id="schemaasyncreportresponse"></a>

```yaml
id: b8ffd5b3-050a-46b9-9192-fbd7c20a22ec

```

*AsyncReportResponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|The identifier for this async report|

<h2 id="tocSsummaryreport">SummaryReport</h2>

<a id="schemasummaryreport"></a>

```yaml
properties:
  end_date: 2017-02-10T13:30:00.000Z
  start_date: 2017-02-12T13:30:00.000Z
  timezone: >-
    The timezone that this report is presented in, this may be passed in as a
    parameter to the report, or taken from account settings
data:
  - {}

```

*SummaryReport*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|properties|[Properties33](#schemaproperties33)|false|none|none|
|data|[[SummaryReportItem](#schemasummaryreportitem)]|false|none|none|

<h2 id="tocSproperties33">Properties33</h2>

<a id="schemaproperties33"></a>

```yaml
end_date: 2019-11-20T03:52:53.022Z
start_date: 2019-11-20T03:52:53.022Z
filters: {}
grouping: DAY
summary: COUNT
summary_field: UNITS
timezone: >-
  The timezone that this report is presented in, this may be passed in as a
  parameter to the report, or taken from account settings

```

*Properties33*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|end_date|string|true|none|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|string|true|none|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|filters|object|false|none|Any filters provided as parameters for this report|
|grouping|[grouping](#schemagrouping)|false|none|The value of the group by parameter provided for this report|
|summary|[summary](#schemasummary)|false|none|The value of the summary_by parameter provided for this report|
|summary_field|[summary_field](#schemasummary_field)|false|none|The value of the summary_field parameter provided for this report|
|timezone|string|false|none|none|

<h2 id="tocSsummaryreportitem">SummaryReportItem</h2>

<a id="schemasummaryreportitem"></a>

```yaml
group: string
value: 0

```

*SummaryReportItem*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|group|string|false|none|none|
|value|number|false|none|none|

<h2 id="tocSgetasyncreportsresponse">getAsyncReportsResponse</h2>

<a id="schemagetasyncreportsresponse"></a>

```yaml
data:
  - created_datetime: 2017-02-12T13:30:00.000Z
    last_modified_datetime: 2017-02-12T13:30:00.000Z
pagination: {}

```

*getAsyncReportsResponse*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[AsyncReport](#schemaasyncreport)]|false|none|List of asynchronous reports|
|pagination|[Pagination](#schemapagination)|false|none|none|

<h2 id="tocSasyncreceivedmessagesdetailrequest">asyncreceivedmessagesdetailrequest</h2>

<a id="schemaasyncreceivedmessagesdetailrequest"></a>

```yaml
end_date: 2017-02-10T13:30:00.000Z
start_date: 2017-02-12T13:30:00.000Z
period: TODAY
sort_by: ACCOUNT
sort_direction: ASCENDING
timezone: Australia/Melbourne
accounts: []
delivery_options:
  - delivery_type: EMAIL
    delivery_addresses: []
    delivery_format: CSV

```

*asyncreceivedmessagesdetailrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|end_date|string|true|none|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|string|true|none|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|period|[period](#schemaperiod)|false|none|Automatically set a date range based on the period value. Can't be combined with start_date and end_date.|
|sort_by|[sort_by](#schemasort_by)|false|none|Field to sort results set by|
|sort_direction|[sort_direction](#schemasort_direction)|false|none|Order to sort results by.|
|timezone|string|false|none|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|
|accounts|[string]|false|none|Filter results by a specific account. By default results  will be returned for the account associated with the authentication  credentials and all sub accounts.|
|destination_address_country|string|false|none|Filter results by destination address country.|
|destination_address|string|false|none|Filter results by destination address.|
|message_format|[message_format](#schemamessage_format)|false|none|Filter results by message format.|
|metadata_key|string|false|none|Filter results for messages that include a metadata key.|
|metadata_value|string|false|none|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|source_address_country|string|false|none|Filter results by source address country.|
|source_address|string|false|none|Filter results by source address.|
|action|[action](#schemaaction)|false|none|Action that was invoked for this message if any, OPT_OUT, OPT_IN, GLOBAL_OPT_OUT|
|delivery_options|[[deliveryOptionsBody](#schemadeliveryoptionsbody)]|false|none|Delivery options for this asynchronous report.|

<h2 id="tocSasyncsentmessagesdetailrequest">asyncsentmessagesdetailrequest</h2>

<a id="schemaasyncsentmessagesdetailrequest"></a>

```yaml
end_date: 2017-02-10T13:30:00.000Z
start_date: 2017-02-12T13:30:00.000Z
period: TODAY
sort_by: DELIVERY_REPORT
sort_direction: ASCENDING
timezone: Australia/Melbourne
accounts: []
statuses:
  - CANCELLED
delivery_options:
  - delivery_type: EMAIL
    delivery_addresses: []
    delivery_format: CSV

```

*asyncsentmessagesdetailrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|end_date|string|true|none|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|string|true|none|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|period|[period](#schemaperiod)|false|none|Automatically set a date range based on the period value. Can't be combined with start_date and end_date.|
|sort_by|[sort_by](#schemasort_by)|false|none|Field to sort results set by|
|sort_direction|[sort_direction](#schemasort_direction)|false|none|Order to sort results by.|
|timezone|string|false|none|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|
|accounts|[string]|false|none|Filter results by a specific account. By default results  will be returned for the account associated with the authentication  credentials and all sub accounts.|
|destination_address_country|string|false|none|Filter results by destination address country.|
|destination_address|string|false|none|Filter results by destination address.|
|message_format|[message_format](#schemamessage_format)|false|none|Filter results by message format.|
|metadata_key|string|false|none|Filter results for messages that include a metadata key.|
|metadata_value|string|false|none|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|source_address_country|string|false|none|Filter results by source address country.|
|source_address|string|false|none|Filter results by source address.|
|status|[status](#schemastatus)|false|none|Filter results by message status. Can't be combined with statuses.|
|statuses|[[statuses](#schemastatuses)]|false|none|Filter results by message statuses. Can't be combined with status.|
|status_code|string|false|none|Filter results by message status code.|
|delivery_report|boolean|false|none|Filter results by delivery report.|
|delivery_options|[[deliveryOptionsBody](#schemadeliveryoptionsbody)]|false|none|Delivery options for this asynchronous report.|

<h2 id="tocSasyncreceivedmessagessummaryrequest">asyncreceivedmessagessummaryrequest</h2>

<a id="schemaasyncreceivedmessagessummaryrequest"></a>

```yaml
end_date: 2017-02-10T13:30:00.000Z
start_date: 2017-02-12T13:30:00.000Z
summary_by: COUNT
summary_field: MESSAGE_ID
group_by:
  - DAY
period: THIS_WEEK
timezone: Australia/Melbourne
accounts: []
delivery_options:
  - delivery_type: EMAIL
    delivery_addresses: []
    delivery_format: CSV

```

*asyncreceivedmessagessummaryrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|end_date|string|true|none|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|string|true|none|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|summary_by|[summary_by](#schemasummary_by)|false|none|Function to apply when summarising results|
|summary_field|[summary_field](#schemasummary_field)|false|none|The value of the summary_field parameter provided for this report|
|group_by|[[group_by](#schemagroup_by)]|false|none|List of fields to group results set by|
|period|[period](#schemaperiod)|false|none|Automatically set a date range based on the period value. Can't be combined with start_date and end_date.|
|timezone|string|false|none|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|
|accounts|[string]|false|none|Filter results by a specific account. By default results  will be returned for the account associated with the authentication  credentials and all sub accounts.|
|destination_address_country|string|false|none|Filter results by destination address country.|
|destination_address|string|false|none|Filter results by destination address.|
|message_format|[message_format](#schemamessage_format)|false|none|Filter results by message format.|
|metadata_key|string|false|none|Filter results for messages that include a metadata key.|
|metadata_value|string|false|none|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|source_address_country|string|false|none|Filter results by source address country.|
|source_address|string|false|none|Filter results by source address.|
|action|[action](#schemaaction)|false|none|Action that was invoked for this message if any, OPT_OUT, OPT_IN, GLOBAL_OPT_OUT|
|delivery_options|[[deliveryOptionsBody](#schemadeliveryoptionsbody)]|false|none|Delivery options for this asynchronous report.|

<h2 id="tocSasyncsentmessagesrequest">asyncsentmessagesrequest</h2>

<a id="schemaasyncsentmessagesrequest"></a>

```yaml
end_date: 2017-02-10T13:30:00.000Z
start_date: 2017-02-12T13:30:00.000Z
group_by:
  - DAY
period: YESTERDAY
timezone: Australia/Melbourne
accounts: []
delivery_options:
  - delivery_type: EMAIL
    delivery_addresses: []
    delivery_format: CSV

```

*asyncsentmessagesrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|end_date|string|true|none|End date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|start_date|string|true|none|Start date time for report window. By default, the timezone for this parameter will be taken from the account settings for the account associated with the credentials used to make the request, or the account included in the Account parameter. This can be overridden using the timezone parameter per request. The date must be in ISO8601 format.|
|summary_by|[summary_by](#schemasummary_by)|false|none|Function to apply when summarising results|
|summary_field|[summary_field](#schemasummary_field)|false|none|The value of the summary_field parameter provided for this report|
|group_by|[[group_by](#schemagroup_by)]|false|none|List of fields to group results set by|
|period|[period](#schemaperiod)|false|none|Automatically set a date range based on the period value. Can't be combined with start_date and end_date.|
|timezone|string|false|none|The timezone to use for the context of the request. If provided this will be used as the timezone for the start date and end date parameters, and all datetime fields returns in the response. The timezone should be provided as a IANA (Internet Assigned Numbers Authority) time zone database zone name, i.e., 'Australia/Melbourne'.|
|accounts|[string]|false|none|Filter results by a specific account. By default results  will be returned for the account associated with the authentication  credentials and all sub accounts.|
|destination_address_country|string|false|none|Filter results by destination address country.|
|destination_address|string|false|none|Filter results by destination address.|
|message_format|[message_format](#schemamessage_format)|false|none|Filter results by message format.|
|metadata_key|string|false|none|Filter results for messages that include a metadata key.|
|metadata_value|string|false|none|Filter results for messages that include a metadata key containing this value. If this parameter is provided, the metadata_key parameter must also be provided.|
|source_address_country|string|false|none|Filter results by source address country.|
|source_address|string|false|none|Filter results by source address.|
|delivery_report|boolean|false|none|Filter results by delivery report.|
|status_code|string|false|none|Filter results by message status code.|
|delivery_options|[[deliveryOptionsBody](#schemadeliveryoptionsbody)]|false|none|Delivery options for this asynchronous report.|

<h2 id="tocSaction">action</h2>

<a id="schemaaction"></a>

```yaml
MyAccount001

```

*action*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|action|string|false|none|Action that was invoked for this message if any, OPT_OUT, OPT_IN, GLOBAL_OPT_OUT|

#### Enumerated Values

|Property|Value|
|---|---|
|action|MyAccount001|
|action|OPT_OUT|
|action|OPT_IN|
|action|GLOBAL_OPT_OUT|

<h2 id="tocSfield">field</h2>

<a id="schemafield"></a>

```yaml
ACCOUNT

```

*field*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|field|string|false|none|The value of the sort_by field provided for this report|

#### Enumerated Values

|Property|Value|
|---|---|
|field|ACCOUNT|
|field|DELIVERED_TIMESTAMP|
|field|MESSAGE_EXPIRY_TIMESTAMP|
|field|DELIVERY_REPORT|
|field|DESTINATION_ADDRESS|
|field|DESTINATION_ADDRESS_COUNTRY|
|field|FORMAT|
|field|SOURCE_ADDRESS|
|field|SOURCE_ADDRESS_COUNTRY|
|field|STATUS|
|field|STATUS_CODE|
|field|UNITS|
|field|TIMESTAMP|

<h2 id="tocSformat">format</h2>

<a id="schemaformat"></a>

```yaml
AU

```

*format*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|format|string|false|none|Format of message, SMS or TTS (Text To Speech)|

#### Enumerated Values

|Property|Value|
|---|---|
|format|AU|
|format|SMS|
|format|TTS|

<h2 id="tocSgroup_by">group_by</h2>

<a id="schemagroup_by"></a>

```yaml
DAY

```

*group_by*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|group_by|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|group_by|DAY|
|group_by|DESTINATION_ADDRESS|
|group_by|DESTINATION_ADDRESS_COUNTRY|
|group_by|FORMAT|
|group_by|HOUR|
|group_by|METADATA_KEY|
|group_by|METADATA_VALUE|
|group_by|MINUTE|
|group_by|MONTH|
|group_by|SOURCE_ADDRESS|
|group_by|SOURCE_ADDRESS_COUNTRY|
|group_by|STATUS|
|group_by|STATUS_CODE|
|group_by|YEAR|
|group_by|ACCOUNT|

<h2 id="tocSgrouping">grouping</h2>

<a id="schemagrouping"></a>

```yaml
DAY

```

*grouping*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|grouping|string|false|none|The value of the group by parameter provided for this report|

#### Enumerated Values

|Property|Value|
|---|---|
|grouping|DAY|
|grouping|DELIVERY_REPORT|
|grouping|DESTINATION_ADDRESS|
|grouping|DESTINATION_ADDRESS_COUNTRY|
|grouping|FORMAT|
|grouping|HOUR|
|grouping|METADATA_KEY|
|grouping|METADATA_VALUE|
|grouping|MINUTE|
|grouping|MONTH|
|grouping|SOURCE_ADDRESS|
|grouping|SOURCE_ADDRESS_COUNTRY|
|grouping|STATUS|
|grouping|STATUS_CODE|
|grouping|YEAR|
|grouping|ACCOUNT|

<h2 id="tocSmessage_format">message_format</h2>

<a id="schemamessage_format"></a>

```yaml
SMS

```

*message_format*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message_format|string|false|none|Filter results by message format.|

#### Enumerated Values

|Property|Value|
|---|---|
|message_format|SMS|
|message_format|TTS|

<h2 id="tocSmessage_type">message_type</h2>

<a id="schemamessage_type"></a>

```yaml
SENT_MESSAGES

```

*message_type*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message_type|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|message_type|SENT_MESSAGES|
|message_type|RECEIVED_MESSAGES|

<h2 id="tocSorder">order</h2>

<a id="schemaorder"></a>

```yaml
ASCENDING

```

*order*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|order|string|false|none|The value of the sort_direction field provided for this report|

#### Enumerated Values

|Property|Value|
|---|---|
|order|ASCENDING|
|order|DESCENDING|

<h2 id="tocSperiod">period</h2>

<a id="schemaperiod"></a>

```yaml
TODAY

```

*period*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|period|string|false|none|Automatically set a date range based on the period value. Can't be combined with start_date and end_date.|

#### Enumerated Values

|Property|Value|
|---|---|
|period|TODAY|
|period|YESTERDAY|
|period|THIS_WEEK|
|period|LAST_WEEK|
|period|THIS_MONTH|
|period|LAST_MONTH|
|period|LAST_7_DAYS|
|period|LAST_30_DAYS|

<h2 id="tocSreport_status">report_status</h2>

<a id="schemareport_status"></a>

```yaml
REQUESTED

```

*report_status*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|report_status|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|report_status|REQUESTED|
|report_status|RUNNING|
|report_status|CANCELLED|
|report_status|DONE|

<h2 id="tocSsort_by">sort_by</h2>

<a id="schemasort_by"></a>

```yaml
ACCOUNT

```

*sort_by*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|sort_by|string|false|none|Field to sort results set by|

#### Enumerated Values

|Property|Value|
|---|---|
|sort_by|ACCOUNT|
|sort_by|ACTION|
|sort_by|DESTINATION_ADDRESS|
|sort_by|DESTINATION_ADDRESS_COUNTRY|
|sort_by|FORMAT|
|sort_by|SOURCE_ADDRESS|
|sort_by|SOURCE_ADDRESS_COUNTRY|
|sort_by|TIMESTAMP|

<h2 id="tocSsort_direction">sort_direction</h2>

<a id="schemasort_direction"></a>

```yaml
ASCENDING

```

*sort_direction*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|sort_direction|string|false|none|Order to sort results by.|

#### Enumerated Values

|Property|Value|
|---|---|
|sort_direction|ASCENDING|
|sort_direction|DESCENDING|

<h2 id="tocSstatus">status</h2>

<a id="schemastatus"></a>

```yaml
CANCELLED

```

*status*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|string|false|none|Filter results by message status. Can't be combined with statuses.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|CANCELLED|
|status|DELIVERED|
|status|ENROUTE|
|status|EXPIRED|
|status|HELD|
|status|PROCESSED|
|status|PROCESSING|
|status|QUEUED|
|status|REJECTED|
|status|SCHEDULED|
|status|SUBMITTED|

<h2 id="tocSstatuses">statuses</h2>

<a id="schemastatuses"></a>

```yaml
CANCELLED

```

*statuses*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statuses|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|statuses|CANCELLED|
|statuses|DELIVERED|
|statuses|ENROUTE|
|statuses|EXPIRED|
|statuses|HELD|
|statuses|PROCESSED|
|statuses|PROCESSING|
|statuses|QUEUED|
|statuses|REJECTED|
|statuses|SCHEDULED|
|statuses|SUBMITTED|

<h2 id="tocSsummary">summary</h2>

<a id="schemasummary"></a>

```yaml
COUNT

```

*summary*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|summary|string|false|none|The value of the summary_by parameter provided for this report|

#### Enumerated Values

|Property|Value|
|---|---|
|summary|COUNT|
|summary|SUM|

<h2 id="tocSsummary_by">summary_by</h2>

<a id="schemasummary_by"></a>

```yaml
COUNT

```

*summary_by*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|summary_by|string|false|none|Function to apply when summarising results|

#### Enumerated Values

|Property|Value|
|---|---|
|summary_by|COUNT|

<h2 id="tocSsummary_field">summary_field</h2>

<a id="schemasummary_field"></a>

```yaml
UNITS

```

*summary_field*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|summary_field|string|false|none|The value of the summary_field parameter provided for this report|

#### Enumerated Values

|Property|Value|
|---|---|
|summary_field|UNITS|
|summary_field|MESSAGE_ID|

<h2 id="tocStype">type</h2>

<a id="schematype"></a>

```yaml
SUMMARY

```

*type*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|SUMMARY|
|type|DETAIL|

<h2 id="tocSview">View</h2>

<a id="schemaview"></a>

```yaml
dt: 2019-11-20T03:52:53.024Z
user_agent: Mozilla/5.0 (Windows NT...
ip: 127.0.0.1

```

*View*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|dt|string|false|none|none|
|user_agent|string|false|none|none|
|ip|string|false|none|none|

<h2 id="tocSshorturl">ShortUrl</h2>

<a id="schemashorturl"></a>

```yaml
click_count: 3
view_count: 2
message_id: 00000000-0000-0000-0000-000000000000
long_url: 'https://developers.messagemedia.com'
short_url: 'https://nxt.to/abc1234'
destination_number: 61491570157

```

*ShortUrl*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|click_count|number|false|none|none|
|view_count|number|false|none|none|
|message_id|string|false|none|none|
|long_url|string|false|none|none|
|short_url|string|false|none|none|
|destination_number|string|false|none|none|

<h2 id="tocSlogsdetailresult">LogsDetailResult</h2>

<a id="schemalogsdetailresult"></a>

```yaml
message_id: 00000000-0000-0000-0000-000000000000
long_url: 'https://developers.messagemedia.com'
short_url: 'https://nxt.to/abc1234'
destination_number: 61491570157
click_count: 3
view_count: 2
clicks:
  - dt: 2018-09-18T01:22:17.071Z
    user_agent: Mozilla/5.0 (Windows NT...
    ip: 127.0.0.1
views:
  - dt: 2018-09-18T01:22:17.071Z
    user_agent: Mozilla/5.0 (Windows NT...
    ip: 127.0.0.1
pagination:
  page: 1
  page_size: 100
  page_count: 3

```

*LogsDetailResult*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message_id|string|false|none|none|
|long_url|string|false|none|none|
|short_url|string|false|none|none|
|destination_number|string|false|none|none|
|click_count|number|false|none|none|
|view_count|number|false|none|none|
|clicks|[[Click](#schemaclick)]|false|none|none|
|views|[[View](#schemaview)]|false|none|none|
|pagination|[Pagination](#schemapagination)|false|none|none|

<h2 id="tocSlogsummaryresult">LogSummaryResult</h2>

<a id="schemalogsummaryresult"></a>

```yaml
total_clicks: 3
unique_clicks: 1
total_views: 2
unique_views: 1
short_urls_generated: 1
short_urls:
  - click_count: 3
    view_count: 2
    message_id: 00000000-0000-0000-0000-000000000000
    long_url: 'https://developers.messagemedia.com'
    short_url: 'https://nxt.to/abc1234'
    destination_number: 61491570157
pagination:
  page: 1
  page_size: 100
  page_count: 3

```

*LogSummaryResult*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|total_clicks|number|false|none|none|
|unique_clicks|number|false|none|none|
|total_views|number|false|none|none|
|unique_views|number|false|none|none|
|short_urls_generated|number|false|none|none|
|short_urls|[[ShortUrl](#schemashorturl)]|false|none|none|
|pagination|[Pagination](#schemapagination)|false|none|none|

<h2 id="tocSclick">Click</h2>

<a id="schemaclick"></a>

```yaml
dt: 2019-11-20T03:52:53.025Z
user_agent: Mozilla/5.0 (Windows NT...
ip: 127.0.0.1

```

*Click*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|dt|string|false|none|none|
|user_agent|string|false|none|none|
|ip|string|false|none|none|

<h2 id="tocScreatewebhookrequest">CreateWebhookrequest</h2>

<a id="schemacreatewebhookrequest"></a>

```yaml
url: 'http://webhook.com'
method: POST
encoding: JSON
headers:
  Account: DeveloperPortal7000
events:
  - ENROUTE_DR
  - DELIVERED_DR
template: '{"id":"$mtId","status":"$statusCode"}'

```

*CreateWebhookrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|url|string|true|none|none|
|method|string|true|none|none|
|encoding|string|true|none|none|
|headers|[Headers](#schemaheaders)|true|none|none|
|events|[string]|true|none|none|
|template|string|true|none|none|

<h2 id="tocSheaders">Headers</h2>

<a id="schemaheaders"></a>

```yaml
Account: DeveloperPortal7000

```

*Headers*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Account|string|true|none|none|

<h2 id="tocSupdatewebhookrequest">UpdateWebhookrequest</h2>

<a id="schemaupdatewebhookrequest"></a>

```yaml
url: 'https://myurl.com'
method: POST
encoding: FORM_ENCODED
events:
  - ENROUTE_DR
template: '{"id":"$mtId", "status":"$statusCode"}'

```

*UpdateWebhookrequest*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|url|string|true|none|none|
|method|string|true|none|none|
|encoding|string|true|none|none|
|events|[string]|true|none|none|
|template|string|true|none|none|

<h2 id="tocSupdatewebhook400response">UpdateWebhook400response</h2>

<a id="schemaupdatewebhook400response"></a>

```yaml
message: Something went wrong. Please try again later.

```

*UpdateWebhook400response*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message|string|true|none|none|

