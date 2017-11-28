---
title: Termin3 API v1.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2
---

# Termin3 API v1.0

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Termin3 API is HTTP-based RESTful API that allows you to seamlessly integrate Termin3 Appointments System with other applications. Build and Grow your applications easly with Termin3 API.

Base URLs:

* <a href="/">/</a>



 License: MIT

# Authentication


* API Key
    - Parameter Name: **access_token**, in: query. 



# Appointments

## AppointmentsApiRead

> Code samples

```shell
# You can also use wget
curl -X GET //organizations/{org_db}/appointments/available?date_from=string&date_to=string \
  -H 'Accept: text/html'

```

```http
GET //organizations/{org_db}/appointments/available?date_from=string&date_to=string HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//organizations/{org_db}/appointments/available',
  method: 'get',
  data: '?date_from=string&date_to=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//organizations/{org_db}/appointments/available?date_from=string&date_to=string',
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
  'Accept' => 'text/html'
}

result = RestClient.get '//organizations/{org_db}/appointments/available',
  params: {
  'date_from' => 'string',
'date_to' => 'string'
}, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('//organizations/{org_db}/appointments/available', params={
  'date_from': 'string',  'date_to': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//organizations/{org_db}/appointments/available?date_from=string&date_to=string");
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

`GET /organizations/{org_db}/appointments/available`

All available appointments for organization.

<h3 id="AppointmentsApiRead-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
org_db|path|string|true|Organization database name
date_from|query|string|true|Starting date for appointments. If undefined then it is - forever.
date_to|query|string|true|Ending date for appointments. If undefined then it is + forever.


> Example responses

```json
[
  {
    "status": "step_1",
    "time_start": "2017-11-28T15:27:45Z",
    "time_end": "2017-11-28T15:27:45Z",
    "sms_reminder": "2017-11-28T15:27:45Z",
    "note": "string",
    "id_client": "string",
    "id_service": "string",
    "staff": [
      {
        "id_staff": "string",
        "occupation": "technician"
      }
    ],
    "id_recurring_meta": "string",
    "freq": "once",
    "recurring_state": "no_recurring",
    "recurring_exception_date": "2017-11-28T15:27:45Z",
    "recurring_dates": [
      "2017-11-28T15:27:45Z"
    ],
    "booking_info": {
      "client_name": "string",
      "client_phone_number": "string"
    },
    "payment_info": {
      "termin_ind_paid": 0,
      "termin_paid_ammount": 0,
      "termin_paid_currency_code": "string",
      "termin_paid_quantity": 0,
      "termin_paid_type": "string",
      "service_ind_free": 0,
      "service_price": 0,
      "service_currency_code": "string"
    },
    "_id": "string",
    "_rev": "string",
    "type": "user",
    "time_create": "2017-11-28T15:27:45Z",
    "time_update": "2017-11-28T15:27:45Z",
    "time_delete": "2017-11-28T15:27:45Z",
    "user_create": "string",
    "user_update": "string",
    "user_delete": "string",
    "db_origin": "string"
  }
]
```
```json
"string"
```
<h3 id="AppointmentsApiRead-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<h3 id="AppointmentsApiRead-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[object]|false|No description
» status|string|false|Termin status codes:<br> <b>step 1</b>: Should choose service (skipped)<br> <b>step 2</b>: Should choose time <br> <b>step 3</b>: Should choose client <br> <b>confirmed</b>: Confirmed appointment <br> <b>canceled</b>: Appointment that have been canceled <br> <b>noshow</b>: Client didn't show up when scheduled <br> <b>available</b>: Available on portal for booking <br> <b>pending</b> Client booked this appointment and now vaiting for owner to confirm
» time_start|string(date-time)|false|Date and time when appointment starts
» time_end|string(date-time)|false|Date and time when appointment ends
» sms_reminder|string(date-time)|false|Deprecated
» note|string|false|Note about the appointment
» id_client|string|false|Reference to Client document ID
» id_service|string|false|Reference to Service document ID
» id_recurring_meta|string|false|Reference to Recurring Meta document ID
» freq|string|false|Cached recurring frequency codes: <br> <b>once</b> <br> <b>daily</b> <br> <b>weekly</b> <br> <b>monthly</b> <br> <b>yearly</b> <br> <b>custom</b>
» recurring_state|string|false|Cached meta data describing termin object in context of recurring appointments: <br> <b>no_recurring</b>: single, no recurring appointment <br> <b>original</b>: first appointment in the recurring sequence <br> <b>exception</b>: appointment that is exception from recurring sequence <br> <b>virtual</b>: recurring appointment that is not first in the sequence. These are not saved in the database.
» recurring_exception_date|string(date-time)|false|If appointment is recurring exception this is the original date when appointment was part of the sequence
» booking_info|object|false|Booking information left by the client on Termin3 portal
»» client_name|string|false|Client name that was enetered by client on portal
»» client_phone_number|string|false|Client phone number that was enetered by client on portal
» payment_info|object|false|Payment info
»» termin_ind_paid|number(double)|false|If appointment is payed (1: payed, 0: not payed)
»» termin_paid_ammount|number(double)|false|Payed ammount
»» termin_paid_currency_code|string|false|Currency code
»» termin_paid_quantity|number(double)|false|(not used at this moment)
»» termin_paid_type|string|false|(not used at this moment)
»» service_ind_free|number(double)|false|Indicator if appointment is free of charge (1: true, 0: false)
»» service_price|number(double)|false|Service price to be payed
»» service_currency_code|string|false|Service price currency code
» _id|string|false|Database record identifier
» _rev|string|false|Database record revision
» type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
» time_create|string(date-time)|false|Date and time when record was created
» time_update|string(date-time)|false|Date and time when record was updated
» time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
» user_create|string|false|User ID who created record.
» user_update|string|false|User ID who updated record.
» user_delete|string|false|User ID who deleted record.
» db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.
» staff|[object]|false|Staff occupied on this appointment
»» id_staff|string|false|Reference to Staff document ID
»» occupation|string|false|Staff occupation code for particular appointment: technician, doctor, employee...
» recurring_dates|[string(date-time)]|false|Cached dates when recurring appointments should occur. <br> This field appears for original recurring termin documents. <br> It is used for performance optimization.



<h3 id="AppointmentsApiRead-responseschema">Response Schema</h3>

Status Code **500**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

## AppointmentsApiUpdate

> Code samples

```shell
# You can also use wget
curl -X PUT //organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string \
  -H 'Accept: text/html'

```

```http
PUT //organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//organizations/{org_db}/appointments/available/{id}',
  method: 'put',
  data: '?name=string&phone_number=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string',
{
  method: 'PUT',

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
  'Accept' => 'text/html'
}

result = RestClient.put '//organizations/{org_db}/appointments/available/{id}',
  params: {
  'name' => 'string',
'phone_number' => 'string'
}, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.put('//organizations/{org_db}/appointments/available/{id}', params={
  'name': 'string',  'phone_number': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string");
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

`PUT /organizations/{org_db}/appointments/available/{id}`

Update of available appointment.

<h3 id="AppointmentsApiUpdate-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
org_db|path|string|true|Organization database name
id|path|string|true|Document ID for update
name|query|string|true|Client full name
phone_number|query|string|true|Client phone number


> Example responses

```json
{
  "id": "string",
  "ok": true,
  "rev": "string"
}
```
```json
"string"
```
```json
"string"
```
<h3 id="AppointmentsApiUpdate-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad request|string
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<h3 id="AppointmentsApiUpdate-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
id|string|false|Changed document ID
ok|boolean|false|Operation status
rev|string|false|New document revision MVCC token



<h3 id="AppointmentsApiUpdate-responseschema">Response Schema</h3>

Status Code **400**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<h3 id="AppointmentsApiUpdate-responseschema">Response Schema</h3>

Status Code **500**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

# Domains

## DomainApiRead

> Code samples

```shell
# You can also use wget
curl -X GET //domains/{name} \
  -H 'Accept: text/html'

```

```http
GET //domains/{name} HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//domains/{name}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//domains/{name}',
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
  'Accept' => 'text/html'
}

result = RestClient.get '//domains/{name}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('//domains/{name}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//domains/{name}");
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

`GET /domains/{name}`

Domain {name} info. <br> Can be used to check if domain {name} is occupied.

<h3 id="DomainApiRead-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
name|path|string|true|


> Example responses

```json
{
  "domain_name": "string",
  "org_db": "string",
  "time_created": "2017-11-28T15:27:45Z",
  "is_available": true,
  "is_public": true,
  "days_ahead": 0
}
```
```json
"string"
```
<h3 id="DomainApiRead-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<h3 id="DomainApiRead-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
domain_name|string|false|Domain name
org_db|string|false|Organization database name
time_created|string(date-time)|false|Date and time when domain was created
is_available|boolean|false|Is domain available. If not then it is already reserved by someone else.
is_public|boolean|false|Is domain public, meaning if reserved domain has been publicly released.
days_ahead|number(double)|false|Days ahead shown on portal



<h3 id="DomainApiRead-responseschema">Response Schema</h3>

Status Code **500**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

## DomainApiReserve

> Code samples

```shell
# You can also use wget
curl -X POST //domains/{name}?org_db=string&org_id=string \
  -H 'Accept: text/html'

```

```http
POST //domains/{name}?org_db=string&org_id=string HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//domains/{name}',
  method: 'post',
  data: '?org_db=string&org_id=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//domains/{name}?org_db=string&org_id=string',
{
  method: 'POST',

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
  'Accept' => 'text/html'
}

result = RestClient.post '//domains/{name}',
  params: {
  'org_db' => 'string',
'org_id' => 'string'
}, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.post('//domains/{name}', params={
  'org_db': 'string',  'org_id': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//domains/{name}?org_db=string&org_id=string");
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

`POST /domains/{name}`

Reservation of domain for organization

<h3 id="DomainApiReserve-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
name|path|string|true|
org_db|query|string|true|Organization database name
org_id|query|string|true|Organization document id


> Example responses

```json
{
  "id": "string",
  "ok": true,
  "rev": "string"
}
```
```json
"string"
```
```json
"string"
```
```json
"string"
```
<h3 id="DomainApiReserve-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|string
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad request|string
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<h3 id="DomainApiReserve-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
id|string|false|Changed document ID
ok|boolean|false|Operation status
rev|string|false|New document revision MVCC token



<h3 id="DomainApiReserve-responseschema">Response Schema</h3>

Status Code **201**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<h3 id="DomainApiReserve-responseschema">Response Schema</h3>

Status Code **400**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<h3 id="DomainApiReserve-responseschema">Response Schema</h3>

Status Code **500**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

# Organizations

## OrganizationApiRead

> Code samples

```shell
# You can also use wget
curl -X GET //organizations/{org_db} \
  -H 'Accept: text/html'

```

```http
GET //organizations/{org_db} HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//organizations/{org_db}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//organizations/{org_db}',
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
  'Accept' => 'text/html'
}

result = RestClient.get '//organizations/{org_db}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('//organizations/{org_db}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//organizations/{org_db}");
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

`GET /organizations/{org_db}`

Fetching original organization data - from organiziation database (always update)

<h3 id="OrganizationApiRead-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
org_db|path|string|true|Organization database name


> Example responses

```json
{
  "db": "string",
  "db_owner": "string",
  "name": "string",
  "business": "string",
  "working_hours_from": "string",
  "working_hours_to": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
```json
"string"
```
<h3 id="OrganizationApiRead-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<h3 id="OrganizationApiRead-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
db|string|false|Organization database name
db_owner|string|false|User database name
name|string|false|Organization name
business|string|false|Business category
working_hours_from|string|false|Working hours starting time. Example: 08:00
working_hours_to|string|false|Working hours ending time. Example: 23:00
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<h3 id="OrganizationApiRead-responseschema">Response Schema</h3>

Status Code **500**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

## Termin3ApiOrgDbRead

> Code samples

```shell
# You can also use wget
curl -X GET //termin3/organizations/{org_db} \
  -H 'Accept: text/html'

```

```http
GET //termin3/organizations/{org_db} HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//termin3/organizations/{org_db}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//termin3/organizations/{org_db}',
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
  'Accept' => 'text/html'
}

result = RestClient.get '//termin3/organizations/{org_db}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('//termin3/organizations/{org_db}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//termin3/organizations/{org_db}");
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

`GET /termin3/organizations/{org_db}`

Fetching organization data from termin3 database. This is not the same as from org database.

<h3 id="Termin3ApiOrgDbRead-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
org_db|path|string|true|Organization database name


> Example responses

```json
{
  "db_org": "string",
  "id_org": "string",
  "db_owner_initial": "string",
  "name_initial": "string",
  "business_initial": "string",
  "working_hours_from_initial": "string",
  "working_hours_to_initial": "string",
  "stats": {
    "doc_count": {
      "CommonDbModelDocumentType": 0,
      "by_day": {
        "CommonDbModelDocumentType": {
          "Date": 0
        }
      },
      "total": 0,
      "processed": 0,
      "ok": true
    },
    "doc_created_min": {
      "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
      "global": "2017-11-28T15:27:45Z"
    },
    "doc_created_max": {
      "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
      "global": "2017-11-28T15:27:45Z"
    },
    "staff": {
      "admin": {
        "db": "string",
        "email": "string",
        "name": "string"
      }
    },
    "reminder": {
      "ReminderDbModelStatusCodes": 0,
      "fail_reason": {
        "ReminderDbModelErrorCodes": 0
      }
    },
    "last_run": "2017-11-28T15:27:45Z",
    "termin3_code": "string",
    "termin3_version": "string",
    "termin_last_date": "2017-11-28T15:27:45Z",
    "termins_in_future": 0
  },
  "portal": {
    "domain_name": "string",
    "org_db": "string",
    "time_created": "2017-11-28T15:27:45Z",
    "is_available": true,
    "is_public": true,
    "days_ahead": 0
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
```json
"string"
```
<h3 id="Termin3ApiOrgDbRead-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<h3 id="Termin3ApiOrgDbRead-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
db_org|string|false|Organization database name
id_org|string|false|Original org document ID that exists in db_org database
db_owner_initial|string|false|User database name (at time of org document creation)
name_initial|string|false|Organization name (at time of org document creation)
business_initial|string|false|Business category (at time of org document creation)
working_hours_from_initial|string|false|Working hours starting time (at time of org document creation). Example: 08:00
working_hours_to_initial|string|false|Working hours ending time (at time of org document creation). Example: 23:00
stats|object|false|BI statistics for organization
» doc_count|object|false|No description
»» CommonDbModelDocumentType|number(double)|false|Number of documents for each document type
»» by_day|object|false|Number of documents by document type grouped by dates when they were created
»»» CommonDbModelDocumentType|object|false|No description
»»»» Date|number(double)|false|No description
»» total|number(double)|false|Total number of documents processed by BI for this organization
»» processed|number(double)|false|Current number of processed documents by BI
»» ok|boolean|false|BI counting has finished
» doc_created_min|object|false|Minimum date and time of document creation by document type
»» CommonDbModelDocumentType|string(date-time)|false|No description
»» global|string(date-time)|false|Date and time of first document creation
» doc_created_max|object|false|Maximum date and time of document creation by document type
»» CommonDbModelDocumentType|string(date-time)|false|No description
»» global|string(date-time)|false|Date and time of last document creation
» staff|object|false|Staff stats
»» admin|object|false|No description
»»» db|string|false|Staff user db
»»» email|string|false|Staff username as email
»»» name|string|false|Staff name
» reminder|object|false|Reminder stats
»» ReminderDbModelStatusCodes|number(double)|false|Number of reminders with particular status
»» fail_reason|object|false|Number of reminders by fail reasons
»»» ReminderDbModelErrorCodes|number(double)|false|No description
» last_run|string(date-time)|false|Date and time when BI was run last
» termin3_code|string|false|Latest used Termin3 Android application code
» termin3_version|string|false|Latest used Termin3 Android application version
» termin_last_date|string(date-time)|false|Date when starts the last appointment in organization database
» termins_in_future|number(double)|false|Number of appointments scheduled in future
portal|object|false|Portal info
» domain_name|string|false|Domain name
» org_db|string|false|Organization database name
» time_created|string(date-time)|false|Date and time when domain was created
» is_available|boolean|false|Is domain available. If not then it is already reserved by someone else.
» is_public|boolean|false|Is domain public, meaning if reserved domain has been publicly released.
» days_ahead|number(double)|false|Days ahead shown on portal
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<h3 id="Termin3ApiOrgDbRead-responseschema">Response Schema</h3>

Status Code **500**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

# Services

## OrganizationApiGetServices

> Code samples

```shell
# You can also use wget
curl -X GET //organizations/{org_db}/services \
  -H 'Accept: text/html'

```

```http
GET //organizations/{org_db}/services HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//organizations/{org_db}/services',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//organizations/{org_db}/services',
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
  'Accept' => 'text/html'
}

result = RestClient.get '//organizations/{org_db}/services',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('//organizations/{org_db}/services', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//organizations/{org_db}/services");
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

`GET /organizations/{org_db}/services`

Fetching organization services

<h3 id="OrganizationApiGetServices-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
org_db|path|string|true|Organization database name


> Example responses

```json
[
  {
    "duration_min": 0,
    "color": "string",
    "shortcut": "string",
    "name": "string",
    "payment_info": {
      "service_ind_free": 0,
      "service_price": 0,
      "service_currency_code": "string"
    },
    "is_available_on_portal": true,
    "is_default": true,
    "_id": "string",
    "_rev": "string",
    "type": "user",
    "time_create": "2017-11-28T15:27:45Z",
    "time_update": "2017-11-28T15:27:45Z",
    "time_delete": "2017-11-28T15:27:45Z",
    "user_create": "string",
    "user_update": "string",
    "user_delete": "string",
    "db_origin": "string"
  }
]
```
```json
"string"
```
<h3 id="OrganizationApiGetServices-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<h3 id="OrganizationApiGetServices-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[object]|false|No description
» duration_min|number(double)|false|Service duration in minutes
» color|string|false|Service RGB hex color
» shortcut|string|false|Shortcut used for displaying service with maximum of two letters
» name|string|false|Service name
» payment_info|object|false|Payment info
»» service_ind_free|number(double)|false|Indicator if appointment is free of charge (1: true, 0: false)
»» service_price|number(double)|false|Service price to be payed
»» service_currency_code|string|false|Service price currency code
» is_available_on_portal|boolean|false|If available on portal
» is_default|boolean|false|If this is default service
» _id|string|false|Database record identifier
» _rev|string|false|Database record revision
» type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
» time_create|string(date-time)|false|Date and time when record was created
» time_update|string(date-time)|false|Date and time when record was updated
» time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
» user_create|string|false|User ID who created record.
» user_update|string|false|User ID who updated record.
» user_delete|string|false|User ID who deleted record.
» db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<h3 id="OrganizationApiGetServices-responseschema">Response Schema</h3>

Status Code **500**

Name|Type|Required|Description
---|---|---|---|---|
simple|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

# Register/login

## RegisterApiCreate

> Code samples

```shell
# You can also use wget
curl -X POST //register?name=string&pass=string&email_primary=string&email_secondary=string \
  -H 'Accept: application/json'

```

```http
POST //register?name=string&pass=string&email_primary=string&email_secondary=string HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//register',
  method: 'post',
  data: '?name=string&pass=string&email_primary=string&email_secondary=string',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//register?name=string&pass=string&email_primary=string&email_secondary=string',
{
  method: 'POST',

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

result = RestClient.post '//register',
  params: {
  'name' => 'string',
'pass' => 'string',
'email_primary' => 'string',
'email_secondary' => 'string'
}, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.post('//register', params={
  'name': 'string',  'pass': 'string',  'email_primary': 'string',  'email_secondary': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//register?name=string&pass=string&email_primary=string&email_secondary=string");
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

`POST /register`

<h3 id="RegisterApiCreate-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
name|query|string|true|Obavezno
pass|query|string|true|Obavezno
email_primary|query|string|true|Obavezno
email_secondary|query|string|true|Opciono


> Example responses

```json
{}
```
<h3 id="RegisterApiCreate-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|object

<aside class="success">
This operation does not require authentication
</aside>

# Stats

## Termin3ApiStatsOrgCount

> Code samples

```shell
# You can also use wget
curl -X GET //termin3/stats/org_count \
  -H 'Accept: text/html'

```

```http
GET //termin3/stats/org_count HTTP/1.1
Host: null

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: '//termin3/stats/org_count',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'text/html'

};

fetch('//termin3/stats/org_count',
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
  'Accept' => 'text/html'
}

result = RestClient.get '//termin3/stats/org_count',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('//termin3/stats/org_count', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//termin3/stats/org_count");
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

`GET /termin3/stats/org_count`

Maximum index number of organizations in termin3 db

> Example responses

<h3 id="Termin3ApiStatsOrgCount-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|number(double)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Termin3-API-default">Default</h1>

## EmptyApiClient

> Code samples

```shell
# You can also use wget
curl -X GET //_/client \
  -H 'Accept: application/json'

```

```http
GET //_/client HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/client',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/client',
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

result = RestClient.get '//_/client',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/client', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/client");
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

`GET /_/client`

> Example responses

```json
{
  "name": "string",
  "phone_mobile": "string",
  "origin": "device",
  "id_origin": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiClient-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiClient-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
name|string|false|Client full name
phone_mobile|string|false|Client mobile number
origin|string|false|Client origin codes:<br> <b>device</b>: These client documents are stored localy on devices <br> <b>couchdb</b>: Clients that are stored in Termin3 couchdb database
id_origin|string|false|DEPRECATED<br> If client document belongs to other database then we store the ID from that database. This is not usable at this moment. Device clients are stored localy
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiDevice

> Code samples

```shell
# You can also use wget
curl -X GET //_/device \
  -H 'Accept: application/json'

```

```http
GET //_/device HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/device',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/device',
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

result = RestClient.get '//_/device',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/device', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/device");
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

`GET /_/device`

> Example responses

```json
{
  "id_user": "string",
  "imei": "string",
  "android_id": "string",
  "os_version": "string",
  "termin3_version": "string",
  "termin3_code": "string",
  "locale_language": "string",
  "locale_country": "string",
  "locale_display_language": "string",
  "locale_display_country": "string",
  "timezone_id": "string",
  "timezone_display_name": "string",
  "build_brand": "string",
  "build_manufacturer": "string",
  "build_model": "string",
  "build_serial": "string",
  "feature_telephony": true,
  "feature_location": true,
  "settings": {
    "pref_contacts_read_allowed": true,
    "pref_incoming_phone_read": true,
    "pref_draw_on_top_allowed": true,
    "pref_send_sms_allowed": true,
    "pref_draw_on_top": "Keep floating menu always on top",
    "pref_extend_working_hours": true,
    "pref_week_start_day": "Saturday",
    "pref_active_user_language": "string",
    "pref_time_format": "24H",
    "pref_send_sms_in_roaming_allowed": true,
    "pref_default_currency": "string",
    "_id": "string",
    "_rev": "string",
    "type": "user",
    "time_create": "2017-11-28T15:27:45Z",
    "time_update": "2017-11-28T15:27:45Z",
    "time_delete": "2017-11-28T15:27:45Z",
    "user_create": "string",
    "user_update": "string",
    "user_delete": "string",
    "db_origin": "string"
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiDevice-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiDevice-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
id_user|string|false|User using device document ID
imei|string|false|Device IMEI number
android_id|string|false|Android ID
os_version|string|false|Android OS version
termin3_version|string|false|Termin3 app version
termin3_code|string|false|Termin3 app code
locale_language|string|false|Language on device
locale_country|string|false|Language locale country
locale_display_language|string|false|Display language
locale_display_country|string|false|Locale display country
timezone_id|string|false|Timezone ID used on device
timezone_display_name|string|false|Timezone display name
build_brand|string|false|Device brand
build_manufacturer|string|false|Manufacturer
build_model|string|false|Device model
build_serial|string|false|Device serial number
feature_telephony|boolean|false|Can make phone calls
feature_location|boolean|false|Can use location services
settings|object|false|Settings used on this device
» pref_contacts_read_allowed|boolean|false|Allowed reading contacts permission
» pref_incoming_phone_read|boolean|false|Allowed phone permission
» pref_draw_on_top_allowed|boolean|false|Allowed draw on top permission
» pref_send_sms_allowed|boolean|false|Allowed sending SMS permission
» pref_draw_on_top|string|false|Type of draw on top: <br> <b>Keep floating menu always on top</b>, <b>Keep floating menu during call only</b>, <b>Disable floating menu</b>
» pref_extend_working_hours|boolean|false|Show extended working hours (0-24) on termin panel
» pref_week_start_day|string|false|Preffered week start day for termin panel: <br> <b>Saturday</b>, <b>Sunday</b>, <b>Monday</b>
» pref_active_user_language|string|false|Active user language
» pref_time_format|string|false|Time format: <br> <b>24H</b>, <b>AM/PM</b>
» pref_send_sms_in_roaming_allowed|boolean|false|Sending SMS while in roaming allowed
» pref_default_currency|string|false|Default currency
» _id|string|false|Database record identifier
» _rev|string|false|Database record revision
» type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
» time_create|string(date-time)|false|Date and time when record was created
» time_update|string(date-time)|false|Date and time when record was updated
» time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
» user_create|string|false|User ID who created record.
» user_update|string|false|User ID who updated record.
» user_delete|string|false|User ID who deleted record.
» db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiLicence

> Code samples

```shell
# You can also use wget
curl -X GET //_/licence \
  -H 'Accept: application/json'

```

```http
GET //_/licence HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/licence',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/licence',
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

result = RestClient.get '//_/licence',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/licence', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/licence");
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

`GET /_/licence`

> Example responses

```json
{
  "date_expiration": "2017-11-28T15:27:45Z",
  "date_start": "2017-11-28T15:27:45Z",
  "activated": true,
  "db_org": "string",
  "appointments_per_month_limit": 0,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiLicence-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiLicence-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
date_expiration|string(date-time)|false|Date when licence expires
date_start|string(date-time)|false|Date when licence becomes active
activated|boolean|false|Is licence activated
db_org|string|false|Refference to organization database name that licence is for
appointments_per_month_limit|number(double)|false|Number of maximum allowed appointments per month
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiMessageTemplate

> Code samples

```shell
# You can also use wget
curl -X GET //_/messageTemplate \
  -H 'Accept: application/json'

```

```http
GET //_/messageTemplate HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/messageTemplate',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/messageTemplate',
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

result = RestClient.get '//_/messageTemplate',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/messageTemplate', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/messageTemplate");
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

`GET /_/messageTemplate`

> Example responses

```json
{
  "name": "string",
  "template": "string",
  "default": true,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiMessageTemplate-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiMessageTemplate-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
name|string|false|Template name
template|string|false|Template content: text and codes that are replaced when creating reminder
default|boolean|false|Is template default
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiOrg

> Code samples

```shell
# You can also use wget
curl -X GET //_/org \
  -H 'Accept: application/json'

```

```http
GET //_/org HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/org',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/org',
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

result = RestClient.get '//_/org',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/org', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/org");
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

`GET /_/org`

> Example responses

```json
{
  "db": "string",
  "db_owner": "string",
  "name": "string",
  "business": "string",
  "working_hours_from": "string",
  "working_hours_to": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiOrg-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiOrg-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
db|string|false|Organization database name
db_owner|string|false|User database name
name|string|false|Organization name
business|string|false|Business category
working_hours_from|string|false|Working hours starting time. Example: 08:00
working_hours_to|string|false|Working hours ending time. Example: 23:00
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiOrgTermin3

> Code samples

```shell
# You can also use wget
curl -X GET //_/orgTermin3 \
  -H 'Accept: application/json'

```

```http
GET //_/orgTermin3 HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/orgTermin3',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/orgTermin3',
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

result = RestClient.get '//_/orgTermin3',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/orgTermin3', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/orgTermin3");
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

`GET /_/orgTermin3`

> Example responses

```json
{
  "db_org": "string",
  "id_org": "string",
  "db_owner_initial": "string",
  "name_initial": "string",
  "business_initial": "string",
  "working_hours_from_initial": "string",
  "working_hours_to_initial": "string",
  "stats": {
    "doc_count": {
      "CommonDbModelDocumentType": 0,
      "by_day": {
        "CommonDbModelDocumentType": {
          "Date": 0
        }
      },
      "total": 0,
      "processed": 0,
      "ok": true
    },
    "doc_created_min": {
      "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
      "global": "2017-11-28T15:27:45Z"
    },
    "doc_created_max": {
      "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
      "global": "2017-11-28T15:27:45Z"
    },
    "staff": {
      "admin": {
        "db": "string",
        "email": "string",
        "name": "string"
      }
    },
    "reminder": {
      "ReminderDbModelStatusCodes": 0,
      "fail_reason": {
        "ReminderDbModelErrorCodes": 0
      }
    },
    "last_run": "2017-11-28T15:27:45Z",
    "termin3_code": "string",
    "termin3_version": "string",
    "termin_last_date": "2017-11-28T15:27:45Z",
    "termins_in_future": 0
  },
  "portal": {
    "domain_name": "string",
    "org_db": "string",
    "time_created": "2017-11-28T15:27:45Z",
    "is_available": true,
    "is_public": true,
    "days_ahead": 0
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiOrgTermin3-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiOrgTermin3-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
db_org|string|false|Organization database name
id_org|string|false|Original org document ID that exists in db_org database
db_owner_initial|string|false|User database name (at time of org document creation)
name_initial|string|false|Organization name (at time of org document creation)
business_initial|string|false|Business category (at time of org document creation)
working_hours_from_initial|string|false|Working hours starting time (at time of org document creation). Example: 08:00
working_hours_to_initial|string|false|Working hours ending time (at time of org document creation). Example: 23:00
stats|object|false|BI statistics for organization
» doc_count|object|false|No description
»» CommonDbModelDocumentType|number(double)|false|Number of documents for each document type
»» by_day|object|false|Number of documents by document type grouped by dates when they were created
»»» CommonDbModelDocumentType|object|false|No description
»»»» Date|number(double)|false|No description
»» total|number(double)|false|Total number of documents processed by BI for this organization
»» processed|number(double)|false|Current number of processed documents by BI
»» ok|boolean|false|BI counting has finished
» doc_created_min|object|false|Minimum date and time of document creation by document type
»» CommonDbModelDocumentType|string(date-time)|false|No description
»» global|string(date-time)|false|Date and time of first document creation
» doc_created_max|object|false|Maximum date and time of document creation by document type
»» CommonDbModelDocumentType|string(date-time)|false|No description
»» global|string(date-time)|false|Date and time of last document creation
» staff|object|false|Staff stats
»» admin|object|false|No description
»»» db|string|false|Staff user db
»»» email|string|false|Staff username as email
»»» name|string|false|Staff name
» reminder|object|false|Reminder stats
»» ReminderDbModelStatusCodes|number(double)|false|Number of reminders with particular status
»» fail_reason|object|false|Number of reminders by fail reasons
»»» ReminderDbModelErrorCodes|number(double)|false|No description
» last_run|string(date-time)|false|Date and time when BI was run last
» termin3_code|string|false|Latest used Termin3 Android application code
» termin3_version|string|false|Latest used Termin3 Android application version
» termin_last_date|string(date-time)|false|Date when starts the last appointment in organization database
» termins_in_future|number(double)|false|Number of appointments scheduled in future
portal|object|false|Portal info
» domain_name|string|false|Domain name
» org_db|string|false|Organization database name
» time_created|string(date-time)|false|Date and time when domain was created
» is_available|boolean|false|Is domain available. If not then it is already reserved by someone else.
» is_public|boolean|false|Is domain public, meaning if reserved domain has been publicly released.
» days_ahead|number(double)|false|Days ahead shown on portal
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiRecurringMeta

> Code samples

```shell
# You can also use wget
curl -X GET //_/recurringMeta \
  -H 'Accept: application/json'

```

```http
GET //_/recurringMeta HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/recurringMeta',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/recurringMeta',
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

result = RestClient.get '//_/recurringMeta',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/recurringMeta', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/recurringMeta");
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

`GET /_/recurringMeta`

> Example responses

```json
{
  "id_termin_original": "string",
  "start_date": "2017-11-28T15:27:45Z",
  "end_date": "2017-11-28T15:27:45Z",
  "freq": "once",
  "until_type": "counter",
  "until_counter": 0,
  "custom_days": 0,
  "custom_weeks": 0,
  "custom_months": 0,
  "cached_until": "2017-11-28T15:27:45Z",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiRecurringMeta-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiRecurringMeta-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
id_termin_original|string|false|Original appointment ID that is recurring
start_date|string(date-time)|false|Sequence starting date
end_date|string(date-time)|false|Sequence ending date
freq|string|false|Recurring frequency codes: <br> <b>once</b>, <b>daily</b>, <b>weekly</b>, <b>monthly</b>, <b>yearly</b>, <b>custom</b>
until_type|string|false|The way recurring sequence stops: <br> <b>counter</b>: After number of occurences <br> <b>until_date</b>: When date is reached (including it) <br> <b>forever</b>: Never ending sequence
until_counter|number(double)|false|Number of occurences if until_type is counter
custom_days|number(double)|false|Number of days added if until_type is custom
custom_weeks|number(double)|false|Number of weeks added if until_type is custom
custom_months|number(double)|false|Number of months added if until_type is custom
cached_until|string(date-time)|false|Occurence dates are cached in original appointment. They are cached from the beggining until this date
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiReminder

> Code samples

```shell
# You can also use wget
curl -X GET //_/reminder \
  -H 'Accept: application/json'

```

```http
GET //_/reminder HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/reminder',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/reminder',
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

result = RestClient.get '//_/reminder',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/reminder', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/reminder");
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

`GET /_/reminder`

> Example responses

```json
{
  "reminder_type": "sms",
  "reminder_status": "not_set",
  "error_code": "wrong_device",
  "before_type": "none",
  "custom_before_min": 0,
  "custom_before_hours": 0,
  "custom_before_days": 0,
  "recurring": true,
  "id_termin": "string",
  "id_recurring_meta": "string",
  "id_recurring_date": "2017-11-28T15:27:45Z",
  "recurring_termin_next_date": "2017-11-28T15:27:45Z",
  "recipient_type": "client",
  "id_client": "string",
  "id_staff": "string",
  "scheduled_time": "2017-11-28T15:27:45Z",
  "id_device": "string",
  "recipient_phone": "string",
  "id_message_template": "string",
  "message": "string",
  "snap_termin_time": "2017-11-28T15:27:45Z",
  "snap_termin_end_time": "2017-11-28T15:27:45Z",
  "snap_recipient_name": "string",
  "snap_org_name": "string",
  "snap_staff_name": "string",
  "snap_staff_phone": "string",
  "snap_service_name": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiReminder-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiReminder-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
reminder_type|string|false|Reminder type codes: <br> <b>sms</b>: SMS reminder <br> <b>email</b>: Email message reminder <br> <b>device</b>: Push notification for device
reminder_status|string|false|Reminder status codes: <br> <b>not_set</b>: Reminder document exists but it is not set yet <br> <b>scheduled</b>: Final state for a reminder that was once scheduled and for some reason needs to be canceled <br> <b>canceled</b>: Final state for a reminder that was once scheduled and for some reason needs to be canceled <br> <b>sending</b>: When scheduled time occurs reminder sending process starts by marking its status as sending <br> <b>sent</b>: Final state for sent reminders <br> <b>failed</b>: Final state for failed reminders
error_code|string|false|Failed reminder error codes: <br> <b>wrong_device</b>: Sms not scheduled from device that tried sending <br> <b>termin_missing</b>: Appointment missing for a reminder <br> <b>termin_canceled</b>: Reminder not sent for canceled appointments <br> <b>time_frame</b>: Scheduled time missed for sending <br> <b>no_phone</b>: Phone number is missing <br> <b>no_message</b>: Message is missing <br> <b>permission_missing</b>: Automatic reminders not allowed in Settings <br> <b>roaming_disabled</b>: SMS roaming not allowed in Settings <br> <b>sms_sent_generic_failure</b>: Generic failure <br> <b>sms_sent_no_service</b>: No service <br> <b>sms_sent_null_pdu</b>: Null PDU <br> <b>sms_sent_radio_off</b>: Radio off <br> <b>sms_sent_unexpected</b>: Unexpected error <br> <b>sms_delivery_fail</b>: Message sent but not delivered
before_type|string|false|Time before appointment that reminder is scheduled for sending <br> <b>none</b>: Not scheduled <br> <b>at_time</b>: On appointment start time <br> <b>immediately</b>: Immediately send reminder <br> <b>hour_before_1</b>: One hour before appointment <br> <b>day_before_1</b>: One day before appointment <br> <b>custom_before</b>: On custom time before appointment
custom_before_min|number(double)|false|When custom before_type is choosen, minutes before the appointment
custom_before_hours|number(double)|false|When custom before_type is choosen, hours before the appointment
custom_before_days|number(double)|false|When custom before_type is choosen, days before the appointment
recurring|boolean|false|True if reminder is recurring
id_termin|string|false|Refference to appointment ID
id_recurring_meta|string|false|Reference to recurring meta data
id_recurring_date|string(date-time)|false|Reference to particular appointment in the sequence of recurring appointments. Date is for appointment starting date.
recurring_termin_next_date|string(date-time)|false|If reminder is recurring this is the next date when recurring appointment will occur
recipient_type|string|false|Recipient type codes: <br> <b>client</b>: Reminder for client <br> <b>staff</b>: Reminder for staff
id_client|string|false|Refference to recipient client document if client receives the reminder (not used at this moment)
id_staff|string|false|Refference to recipient staff document if staff receives the reminder (not used at this moment)
scheduled_time|string(date-time)|false|Scheduled date and time for a reminder to be sent
id_device|string|false|Refference to a device document that will be used for sending SMS reminder
recipient_phone|string|false|Recipient phone number
id_message_template|string|false|Refference to message template that will be used
message|string|false|Raw message as it will be sent
snap_termin_time|string(date-time)|false|Cached appointment start date and time
snap_termin_end_time|string(date-time)|false|Cached appointment end date and time
snap_recipient_name|string|false|Cached recipient name
snap_org_name|string|false|Cached organization name
snap_staff_name|string|false|Cached staff name
snap_staff_phone|string|false|Cached staff phone number
snap_service_name|string|false|Cached service name
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiService

> Code samples

```shell
# You can also use wget
curl -X GET //_/service \
  -H 'Accept: application/json'

```

```http
GET //_/service HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/service',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/service',
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

result = RestClient.get '//_/service',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/service', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/service");
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

`GET /_/service`

> Example responses

```json
{
  "duration_min": 0,
  "color": "string",
  "shortcut": "string",
  "name": "string",
  "payment_info": {
    "service_ind_free": 0,
    "service_price": 0,
    "service_currency_code": "string"
  },
  "is_available_on_portal": true,
  "is_default": true,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiService-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiService-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
duration_min|number(double)|false|Service duration in minutes
color|string|false|Service RGB hex color
shortcut|string|false|Shortcut used for displaying service with maximum of two letters
name|string|false|Service name
payment_info|object|false|Payment info
» service_ind_free|number(double)|false|Indicator if appointment is free of charge (1: true, 0: false)
» service_price|number(double)|false|Service price to be payed
» service_currency_code|string|false|Service price currency code
is_available_on_portal|boolean|false|If available on portal
is_default|boolean|false|If this is default service
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiSettings

> Code samples

```shell
# You can also use wget
curl -X GET //_/settings \
  -H 'Accept: application/json'

```

```http
GET //_/settings HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/settings',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/settings',
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

result = RestClient.get '//_/settings',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/settings', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/settings");
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

`GET /_/settings`

> Example responses

```json
{
  "pref_contacts_read_allowed": true,
  "pref_incoming_phone_read": true,
  "pref_draw_on_top_allowed": true,
  "pref_send_sms_allowed": true,
  "pref_draw_on_top": "Keep floating menu always on top",
  "pref_extend_working_hours": true,
  "pref_week_start_day": "Saturday",
  "pref_active_user_language": "string",
  "pref_time_format": "24H",
  "pref_send_sms_in_roaming_allowed": true,
  "pref_default_currency": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiSettings-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiSettings-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
pref_contacts_read_allowed|boolean|false|Allowed reading contacts permission
pref_incoming_phone_read|boolean|false|Allowed phone permission
pref_draw_on_top_allowed|boolean|false|Allowed draw on top permission
pref_send_sms_allowed|boolean|false|Allowed sending SMS permission
pref_draw_on_top|string|false|Type of draw on top: <br> <b>Keep floating menu always on top</b>, <b>Keep floating menu during call only</b>, <b>Disable floating menu</b>
pref_extend_working_hours|boolean|false|Show extended working hours (0-24) on termin panel
pref_week_start_day|string|false|Preffered week start day for termin panel: <br> <b>Saturday</b>, <b>Sunday</b>, <b>Monday</b>
pref_active_user_language|string|false|Active user language
pref_time_format|string|false|Time format: <br> <b>24H</b>, <b>AM/PM</b>
pref_send_sms_in_roaming_allowed|boolean|false|Sending SMS while in roaming allowed
pref_default_currency|string|false|Default currency
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiStaff

> Code samples

```shell
# You can also use wget
curl -X GET //_/staff \
  -H 'Accept: application/json'

```

```http
GET //_/staff HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/staff',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/staff',
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

result = RestClient.get '//_/staff',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/staff', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/staff");
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

`GET /_/staff`

> Example responses

```json
{
  "db_user": "string",
  "id_user": "string",
  "role_in_org": "string",
  "out_of_office": [
    {
      "time_create": "2017-11-28T15:27:45Z",
      "dates": [
        "2017-11-28T15:27:45Z"
      ],
      "description": "string",
      "freq": "once"
    }
  ],
  "is_available_on_portal": true,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiStaff-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiStaff-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
db_user|string|false|Staff is a user that has it's own database. This is that database name
id_user|string|false|User ID
role_in_org|string|false|Role in organization (not used yet)
is_available_on_portal|boolean|false|If available on portal
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.
out_of_office|[object]|false|Out of office days
» time_create|string(date-time)|false|Time when out of office record was created
» description|string|false|Out of office record description
» freq|string|false|Out of office record frequency code: <br> <b>once</b>, <b>yearly</b>
» dates|[string(date-time)]|false|Dates when staff is out of office



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiTermin

> Code samples

```shell
# You can also use wget
curl -X GET //_/termin \
  -H 'Accept: application/json'

```

```http
GET //_/termin HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/termin',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/termin',
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

result = RestClient.get '//_/termin',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/termin', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/termin");
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

`GET /_/termin`

> Example responses

```json
{
  "status": "step_1",
  "time_start": "2017-11-28T15:27:45Z",
  "time_end": "2017-11-28T15:27:45Z",
  "sms_reminder": "2017-11-28T15:27:45Z",
  "note": "string",
  "id_client": "string",
  "id_service": "string",
  "staff": [
    {
      "id_staff": "string",
      "occupation": "technician"
    }
  ],
  "id_recurring_meta": "string",
  "freq": "once",
  "recurring_state": "no_recurring",
  "recurring_exception_date": "2017-11-28T15:27:45Z",
  "recurring_dates": [
    "2017-11-28T15:27:45Z"
  ],
  "booking_info": {
    "client_name": "string",
    "client_phone_number": "string"
  },
  "payment_info": {
    "termin_ind_paid": 0,
    "termin_paid_ammount": 0,
    "termin_paid_currency_code": "string",
    "termin_paid_quantity": 0,
    "termin_paid_type": "string",
    "service_ind_free": 0,
    "service_price": 0,
    "service_currency_code": "string"
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiTermin-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiTermin-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
status|string|false|Termin status codes:<br> <b>step 1</b>: Should choose service (skipped)<br> <b>step 2</b>: Should choose time <br> <b>step 3</b>: Should choose client <br> <b>confirmed</b>: Confirmed appointment <br> <b>canceled</b>: Appointment that have been canceled <br> <b>noshow</b>: Client didn't show up when scheduled <br> <b>available</b>: Available on portal for booking <br> <b>pending</b> Client booked this appointment and now vaiting for owner to confirm
time_start|string(date-time)|false|Date and time when appointment starts
time_end|string(date-time)|false|Date and time when appointment ends
sms_reminder|string(date-time)|false|Deprecated
note|string|false|Note about the appointment
id_client|string|false|Reference to Client document ID
id_service|string|false|Reference to Service document ID
id_recurring_meta|string|false|Reference to Recurring Meta document ID
freq|string|false|Cached recurring frequency codes: <br> <b>once</b> <br> <b>daily</b> <br> <b>weekly</b> <br> <b>monthly</b> <br> <b>yearly</b> <br> <b>custom</b>
recurring_state|string|false|Cached meta data describing termin object in context of recurring appointments: <br> <b>no_recurring</b>: single, no recurring appointment <br> <b>original</b>: first appointment in the recurring sequence <br> <b>exception</b>: appointment that is exception from recurring sequence <br> <b>virtual</b>: recurring appointment that is not first in the sequence. These are not saved in the database.
recurring_exception_date|string(date-time)|false|If appointment is recurring exception this is the original date when appointment was part of the sequence
booking_info|object|false|Booking information left by the client on Termin3 portal
» client_name|string|false|Client name that was enetered by client on portal
» client_phone_number|string|false|Client phone number that was enetered by client on portal
payment_info|object|false|Payment info
» termin_ind_paid|number(double)|false|If appointment is payed (1: payed, 0: not payed)
» termin_paid_ammount|number(double)|false|Payed ammount
» termin_paid_currency_code|string|false|Currency code
» termin_paid_quantity|number(double)|false|(not used at this moment)
» termin_paid_type|string|false|(not used at this moment)
» service_ind_free|number(double)|false|Indicator if appointment is free of charge (1: true, 0: false)
» service_price|number(double)|false|Service price to be payed
» service_currency_code|string|false|Service price currency code
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.
staff|[object]|false|Staff occupied on this appointment
» id_staff|string|false|Reference to Staff document ID
» occupation|string|false|Staff occupation code for particular appointment: technician, doctor, employee...
recurring_dates|[string(date-time)]|false|Cached dates when recurring appointments should occur. <br> This field appears for original recurring termin documents. <br> It is used for performance optimization.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiUser

> Code samples

```shell
# You can also use wget
curl -X GET //_/user \
  -H 'Accept: application/json'

```

```http
GET //_/user HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/user',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/user',
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

result = RestClient.get '//_/user',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/user', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/user");
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

`GET /_/user`

> Example responses

```json
{
  "username": "string",
  "name": "string",
  "email_secondary": "string",
  "occupation": "string",
  "phone": "string",
  "position": "string",
  "db": "string",
  "db_org_current": "string",
  "info": {
    "user_entered_app": true,
    "last_active_time": "2017-11-28T15:27:45Z",
    "termins_created": 0,
    "services_created": 0,
    "reminders_created": 0,
    "recurring_created": 0,
    "clients_created": 0,
    "review_asked_time": "2017-11-28T15:27:45Z",
    "review_clicked": true,
    "review_ask_never": true
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiUser-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiUser-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
username|string|false|Username as email
name|string|false|Full name
email_secondary|string|false|Backup email
occupation|string|false|Occupation
phone|string|false|Phone number
position|string|false|Position in organization
db|string|false|User database name
db_org_current|string|false|Oragnization database name of curently used organization
info|object|false|Termin3 android application user activity
» user_entered_app|boolean|false|User has entered the Termin3 Android app
» last_active_time|string(date-time)|false|Last active date and time
» termins_created|number(double)|false|Total number of created appointments in current organization
» services_created|number(double)|false|Total number of services created in current organization
» reminders_created|number(double)|false|Total number of reminders created in current organization
» recurring_created|number(double)|false|Total number of recurring meta data created in current organization
» clients_created|number(double)|false|Total number of clients created in current organization
» review_asked_time|string(date-time)|false|Last date and time user has been asked to leave review on Google Play Store
» review_clicked|boolean|false|If user has clicked to leave a review
» review_ask_never|boolean|false|If user has clicked not to be bothered again with ask review
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

## EmptyApiUserTermin3

> Code samples

```shell
# You can also use wget
curl -X GET //_/userTermin3 \
  -H 'Accept: application/json'

```

```http
GET //_/userTermin3 HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '//_/userTermin3',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('//_/userTermin3',
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

result = RestClient.get '//_/userTermin3',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('//_/userTermin3', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("//_/userTermin3");
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

`GET /_/userTermin3`

> Example responses

```json
{
  "username": "string",
  "name_initial": "string",
  "id_user": "string",
  "db_name": "string",
  "active": true,
  "email_primary": "string",
  "email_primary_confirmation_key": "string",
  "email_primary_confirmed": "string",
  "email_primary_sent_time": "2017-11-28T15:27:45Z",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
}
```
<h3 id="EmptyApiUserTermin3-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|Inline

<h3 id="EmptyApiUserTermin3-responseschema">Response Schema</h3>

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
username|string|false|Username as email
name_initial|string|false|Full name as entered for the first time
id_user|string|false|User database document ID
db_name|string|false|User database name
active|boolean|false|If user is active
email_primary|string|false|email
email_primary_confirmation_key|string|false|Confirmation key used for email confirmation
email_primary_confirmed|string|false|User has confirmed its email
email_primary_sent_time|string(date-time)|false|Date and time confirmation email has been sent
_id|string|false|Database record identifier
_rev|string|false|Database record revision
type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|false|Date and time when record was created
time_update|string(date-time)|false|Date and time when record was updated
time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|false|User ID who created record.
user_update|string|false|User ID who updated record.
user_delete|string|false|User ID who deleted record.
db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.



<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## TerminDbModel

<a name="schematermindbmodel"></a>

```json
{
  "status": "step_1",
  "time_start": "2017-11-28T15:27:45Z",
  "time_end": "2017-11-28T15:27:45Z",
  "sms_reminder": "2017-11-28T15:27:45Z",
  "note": "string",
  "id_client": "string",
  "id_service": "string",
  "staff": [
    {
      "id_staff": "string",
      "occupation": "technician"
    }
  ],
  "id_recurring_meta": "string",
  "freq": "once",
  "recurring_state": "no_recurring",
  "recurring_exception_date": "2017-11-28T15:27:45Z",
  "recurring_dates": [
    "2017-11-28T15:27:45Z"
  ],
  "booking_info": {
    "client_name": "string",
    "client_phone_number": "string"
  },
  "payment_info": {
    "termin_ind_paid": 0,
    "termin_paid_ammount": 0,
    "termin_paid_currency_code": "string",
    "termin_paid_quantity": 0,
    "termin_paid_type": "string",
    "service_ind_free": 0,
    "service_price": 0,
    "service_currency_code": "string"
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
status|string|true|Termin status codes:<br> <b>step 1</b>: Should choose service (skipped)<br> <b>step 2</b>: Should choose time <br> <b>step 3</b>: Should choose client <br> <b>confirmed</b>: Confirmed appointment <br> <b>canceled</b>: Appointment that have been canceled <br> <b>noshow</b>: Client didn't show up when scheduled <br> <b>available</b>: Available on portal for booking <br> <b>pending</b> Client booked this appointment and now vaiting for owner to confirm
time_start|string(date-time)|true|Date and time when appointment starts
time_end|string(date-time)|true|Date and time when appointment ends
sms_reminder|string(date-time)|true|Deprecated
note|string|true|Note about the appointment
id_client|string|true|Reference to Client document ID
id_service|string|true|Reference to Service document ID
id_recurring_meta|string|true|Reference to Recurring Meta document ID
freq|string|true|Cached recurring frequency codes: <br> <b>once</b> <br> <b>daily</b> <br> <b>weekly</b> <br> <b>monthly</b> <br> <b>yearly</b> <br> <b>custom</b>
recurring_state|string|true|Cached meta data describing termin object in context of recurring appointments: <br> <b>no_recurring</b>: single, no recurring appointment <br> <b>original</b>: first appointment in the recurring sequence <br> <b>exception</b>: appointment that is exception from recurring sequence <br> <b>virtual</b>: recurring appointment that is not first in the sequence. These are not saved in the database.
recurring_exception_date|string(date-time)|true|If appointment is recurring exception this is the original date when appointment was part of the sequence
booking_info|object|true|Booking information left by the client on Termin3 portal
» client_name|string|false|Client name that was enetered by client on portal
» client_phone_number|string|false|Client phone number that was enetered by client on portal
payment_info|object|true|Payment info
» termin_ind_paid|number(double)|false|If appointment is payed (1: payed, 0: not payed)
» termin_paid_ammount|number(double)|false|Payed ammount
» termin_paid_currency_code|string|false|Currency code
» termin_paid_quantity|number(double)|false|(not used at this moment)
» termin_paid_type|string|false|(not used at this moment)
» service_ind_free|number(double)|false|Indicator if appointment is free of charge (1: true, 0: false)
» service_price|number(double)|false|Service price to be payed
» service_currency_code|string|false|Service price currency code
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.
staff|[object]|false|Staff occupied on this appointment
» id_staff|string|false|Reference to Staff document ID
» occupation|string|false|Staff occupation code for particular appointment: technician, doctor, employee...
recurring_dates|[string(date-time)]|false|Cached dates when recurring appointments should occur. <br> This field appears for original recurring termin documents. <br> It is used for performance optimization.


#### Enumerated Values

|Property|Value|
|---|---|
status|step_1|
status|step_2|
status|step_3|
status|confirmed|
status|canceled|
status|noshow|
status|available|
status|pending|
freq|once|
freq|daily|
freq|weekly|
freq|monthly|
freq|yearly|
freq|custom|
recurring_state|no_recurring|
recurring_state|original|
recurring_state|exception|
recurring_state|virtual|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|
» occupation|technician|
» occupation|doctor|
» occupation|employee|


## InsertResponseApiModel

<a name="schemainsertresponseapimodel"></a>

```json
{
  "id": "string",
  "ok": true,
  "rev": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|true|Changed document ID
ok|boolean|true|Operation status
rev|string|true|New document revision MVCC token



## OrgTermin3PortalDbModel

<a name="schemaorgtermin3portaldbmodel"></a>

```json
{
  "domain_name": "string",
  "org_db": "string",
  "time_created": "2017-11-28T15:27:45Z",
  "is_available": true,
  "is_public": true,
  "days_ahead": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
domain_name|string|false|Domain name
org_db|string|false|Organization database name
time_created|string(date-time)|false|Date and time when domain was created
is_available|boolean|false|Is domain available. If not then it is already reserved by someone else.
is_public|boolean|false|Is domain public, meaning if reserved domain has been publicly released.
days_ahead|number(double)|false|Days ahead shown on portal



## OrgDbModel

<a name="schemaorgdbmodel"></a>

```json
{
  "db": "string",
  "db_owner": "string",
  "name": "string",
  "business": "string",
  "working_hours_from": "string",
  "working_hours_to": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
db|string|true|Organization database name
db_owner|string|true|User database name
name|string|true|Organization name
business|string|true|Business category
working_hours_from|string|true|Working hours starting time. Example: 08:00
working_hours_to|string|true|Working hours ending time. Example: 23:00
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## ServiceDbModel

<a name="schemaservicedbmodel"></a>

```json
{
  "duration_min": 0,
  "color": "string",
  "shortcut": "string",
  "name": "string",
  "payment_info": {
    "service_ind_free": 0,
    "service_price": 0,
    "service_currency_code": "string"
  },
  "is_available_on_portal": true,
  "is_default": true,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
duration_min|number(double)|true|Service duration in minutes
color|string|true|Service RGB hex color
shortcut|string|true|Shortcut used for displaying service with maximum of two letters
name|string|true|Service name
payment_info|object|true|Payment info
» service_ind_free|number(double)|false|Indicator if appointment is free of charge (1: true, 0: false)
» service_price|number(double)|false|Service price to be payed
» service_currency_code|string|false|Service price currency code
is_available_on_portal|boolean|false|If available on portal
is_default|boolean|false|If this is default service
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## OrgTermin3DbModelStats

<a name="schemaorgtermin3dbmodelstats"></a>

```json
{
  "doc_count": {
    "CommonDbModelDocumentType": 0,
    "by_day": {
      "CommonDbModelDocumentType": {
        "Date": 0
      }
    },
    "total": 0,
    "processed": 0,
    "ok": true
  },
  "doc_created_min": {
    "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
    "global": "2017-11-28T15:27:45Z"
  },
  "doc_created_max": {
    "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
    "global": "2017-11-28T15:27:45Z"
  },
  "staff": {
    "admin": {
      "db": "string",
      "email": "string",
      "name": "string"
    }
  },
  "reminder": {
    "ReminderDbModelStatusCodes": 0,
    "fail_reason": {
      "ReminderDbModelErrorCodes": 0
    }
  },
  "last_run": "2017-11-28T15:27:45Z",
  "termin3_code": "string",
  "termin3_version": "string",
  "termin_last_date": "2017-11-28T15:27:45Z",
  "termins_in_future": 0
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
doc_count|object|true|No description
» CommonDbModelDocumentType|number(double)|false|Number of documents for each document type
» by_day|object|false|Number of documents by document type grouped by dates when they were created
»» CommonDbModelDocumentType|object|false|No description
»»» Date|number(double)|false|No description
» total|number(double)|false|Total number of documents processed by BI for this organization
» processed|number(double)|false|Current number of processed documents by BI
» ok|boolean|false|BI counting has finished
doc_created_min|object|true|Minimum date and time of document creation by document type
» CommonDbModelDocumentType|string(date-time)|false|No description
» global|string(date-time)|false|Date and time of first document creation
doc_created_max|object|true|Maximum date and time of document creation by document type
» CommonDbModelDocumentType|string(date-time)|false|No description
» global|string(date-time)|false|Date and time of last document creation
staff|object|true|Staff stats
» admin|object|false|No description
»» db|string|false|Staff user db
»» email|string|false|Staff username as email
»» name|string|false|Staff name
reminder|object|true|Reminder stats
» ReminderDbModelStatusCodes|number(double)|false|Number of reminders with particular status
» fail_reason|object|false|Number of reminders by fail reasons
»» ReminderDbModelErrorCodes|number(double)|false|No description
last_run|string(date-time)|true|Date and time when BI was run last
termin3_code|string|true|Latest used Termin3 Android application code
termin3_version|string|true|Latest used Termin3 Android application version
termin_last_date|string(date-time)|true|Date when starts the last appointment in organization database
termins_in_future|number(double)|true|Number of appointments scheduled in future



## OrgTermin3DbModel

<a name="schemaorgtermin3dbmodel"></a>

```json
{
  "db_org": "string",
  "id_org": "string",
  "db_owner_initial": "string",
  "name_initial": "string",
  "business_initial": "string",
  "working_hours_from_initial": "string",
  "working_hours_to_initial": "string",
  "stats": {
    "doc_count": {
      "CommonDbModelDocumentType": 0,
      "by_day": {
        "CommonDbModelDocumentType": {
          "Date": 0
        }
      },
      "total": 0,
      "processed": 0,
      "ok": true
    },
    "doc_created_min": {
      "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
      "global": "2017-11-28T15:27:45Z"
    },
    "doc_created_max": {
      "CommonDbModelDocumentType": "2017-11-28T15:27:45Z",
      "global": "2017-11-28T15:27:45Z"
    },
    "staff": {
      "admin": {
        "db": "string",
        "email": "string",
        "name": "string"
      }
    },
    "reminder": {
      "ReminderDbModelStatusCodes": 0,
      "fail_reason": {
        "ReminderDbModelErrorCodes": 0
      }
    },
    "last_run": "2017-11-28T15:27:45Z",
    "termin3_code": "string",
    "termin3_version": "string",
    "termin_last_date": "2017-11-28T15:27:45Z",
    "termins_in_future": 0
  },
  "portal": {
    "domain_name": "string",
    "org_db": "string",
    "time_created": "2017-11-28T15:27:45Z",
    "is_available": true,
    "is_public": true,
    "days_ahead": 0
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
db_org|string|true|Organization database name
id_org|string|true|Original org document ID that exists in db_org database
db_owner_initial|string|true|User database name (at time of org document creation)
name_initial|string|true|Organization name (at time of org document creation)
business_initial|string|true|Business category (at time of org document creation)
working_hours_from_initial|string|true|Working hours starting time (at time of org document creation). Example: 08:00
working_hours_to_initial|string|true|Working hours ending time (at time of org document creation). Example: 23:00
stats|object|true|BI statistics for organization
» doc_count|object|false|No description
»» CommonDbModelDocumentType|number(double)|false|Number of documents for each document type
»» by_day|object|false|Number of documents by document type grouped by dates when they were created
»»» CommonDbModelDocumentType|object|false|No description
»»»» Date|number(double)|false|No description
»» total|number(double)|false|Total number of documents processed by BI for this organization
»» processed|number(double)|false|Current number of processed documents by BI
»» ok|boolean|false|BI counting has finished
» doc_created_min|object|false|Minimum date and time of document creation by document type
»» CommonDbModelDocumentType|string(date-time)|false|No description
»» global|string(date-time)|false|Date and time of first document creation
» doc_created_max|object|false|Maximum date and time of document creation by document type
»» CommonDbModelDocumentType|string(date-time)|false|No description
»» global|string(date-time)|false|Date and time of last document creation
» staff|object|false|Staff stats
»» admin|object|false|No description
»»» db|string|false|Staff user db
»»» email|string|false|Staff username as email
»»» name|string|false|Staff name
» reminder|object|false|Reminder stats
»» ReminderDbModelStatusCodes|number(double)|false|Number of reminders with particular status
»» fail_reason|object|false|Number of reminders by fail reasons
»»» ReminderDbModelErrorCodes|number(double)|false|No description
» last_run|string(date-time)|false|Date and time when BI was run last
» termin3_code|string|false|Latest used Termin3 Android application code
» termin3_version|string|false|Latest used Termin3 Android application version
» termin_last_date|string(date-time)|false|Date when starts the last appointment in organization database
» termins_in_future|number(double)|false|Number of appointments scheduled in future
portal|object|true|Portal info
» domain_name|string|false|Domain name
» org_db|string|false|Organization database name
» time_created|string(date-time)|false|Date and time when domain was created
» is_available|boolean|false|Is domain available. If not then it is already reserved by someone else.
» is_public|boolean|false|Is domain public, meaning if reserved domain has been publicly released.
» days_ahead|number(double)|false|Days ahead shown on portal
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## ClientDbModel

<a name="schemaclientdbmodel"></a>

```json
{
  "name": "string",
  "phone_mobile": "string",
  "origin": "device",
  "id_origin": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
name|string|true|Client full name
phone_mobile|string|true|Client mobile number
origin|string|true|Client origin codes:<br> <b>device</b>: These client documents are stored localy on devices <br> <b>couchdb</b>: Clients that are stored in Termin3 couchdb database
id_origin|string|true|DEPRECATED<br> If client document belongs to other database then we store the ID from that database. This is not usable at this moment. Device clients are stored localy
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
origin|device|
origin|couchdb|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## SettingsDbModel

<a name="schemasettingsdbmodel"></a>

```json
{
  "pref_contacts_read_allowed": true,
  "pref_incoming_phone_read": true,
  "pref_draw_on_top_allowed": true,
  "pref_send_sms_allowed": true,
  "pref_draw_on_top": "Keep floating menu always on top",
  "pref_extend_working_hours": true,
  "pref_week_start_day": "Saturday",
  "pref_active_user_language": "string",
  "pref_time_format": "24H",
  "pref_send_sms_in_roaming_allowed": true,
  "pref_default_currency": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
pref_contacts_read_allowed|boolean|true|Allowed reading contacts permission
pref_incoming_phone_read|boolean|true|Allowed phone permission
pref_draw_on_top_allowed|boolean|true|Allowed draw on top permission
pref_send_sms_allowed|boolean|true|Allowed sending SMS permission
pref_draw_on_top|string|true|Type of draw on top: <br> <b>Keep floating menu always on top</b>, <b>Keep floating menu during call only</b>, <b>Disable floating menu</b>
pref_extend_working_hours|boolean|true|Show extended working hours (0-24) on termin panel
pref_week_start_day|string|true|Preffered week start day for termin panel: <br> <b>Saturday</b>, <b>Sunday</b>, <b>Monday</b>
pref_active_user_language|string|true|Active user language
pref_time_format|string|true|Time format: <br> <b>24H</b>, <b>AM/PM</b>
pref_send_sms_in_roaming_allowed|boolean|true|Sending SMS while in roaming allowed
pref_default_currency|string|true|Default currency
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
pref_draw_on_top|Keep floating menu always on top|
pref_draw_on_top|Keep floating menu during call only|
pref_draw_on_top|Disable floating menu|
pref_week_start_day|Saturday|
pref_week_start_day|Sunday|
pref_week_start_day|Monday|
pref_time_format|24H|
pref_time_format|AM/PM|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## DeviceDbModel

<a name="schemadevicedbmodel"></a>

```json
{
  "id_user": "string",
  "imei": "string",
  "android_id": "string",
  "os_version": "string",
  "termin3_version": "string",
  "termin3_code": "string",
  "locale_language": "string",
  "locale_country": "string",
  "locale_display_language": "string",
  "locale_display_country": "string",
  "timezone_id": "string",
  "timezone_display_name": "string",
  "build_brand": "string",
  "build_manufacturer": "string",
  "build_model": "string",
  "build_serial": "string",
  "feature_telephony": true,
  "feature_location": true,
  "settings": {
    "pref_contacts_read_allowed": true,
    "pref_incoming_phone_read": true,
    "pref_draw_on_top_allowed": true,
    "pref_send_sms_allowed": true,
    "pref_draw_on_top": "Keep floating menu always on top",
    "pref_extend_working_hours": true,
    "pref_week_start_day": "Saturday",
    "pref_active_user_language": "string",
    "pref_time_format": "24H",
    "pref_send_sms_in_roaming_allowed": true,
    "pref_default_currency": "string",
    "_id": "string",
    "_rev": "string",
    "type": "user",
    "time_create": "2017-11-28T15:27:45Z",
    "time_update": "2017-11-28T15:27:45Z",
    "time_delete": "2017-11-28T15:27:45Z",
    "user_create": "string",
    "user_update": "string",
    "user_delete": "string",
    "db_origin": "string"
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id_user|string|true|User using device document ID
imei|string|true|Device IMEI number
android_id|string|true|Android ID
os_version|string|true|Android OS version
termin3_version|string|true|Termin3 app version
termin3_code|string|true|Termin3 app code
locale_language|string|true|Language on device
locale_country|string|true|Language locale country
locale_display_language|string|true|Display language
locale_display_country|string|true|Locale display country
timezone_id|string|true|Timezone ID used on device
timezone_display_name|string|true|Timezone display name
build_brand|string|true|Device brand
build_manufacturer|string|true|Manufacturer
build_model|string|true|Device model
build_serial|string|true|Device serial number
feature_telephony|boolean|true|Can make phone calls
feature_location|boolean|true|Can use location services
settings|object|true|Settings used on this device
» pref_contacts_read_allowed|boolean|false|Allowed reading contacts permission
» pref_incoming_phone_read|boolean|false|Allowed phone permission
» pref_draw_on_top_allowed|boolean|false|Allowed draw on top permission
» pref_send_sms_allowed|boolean|false|Allowed sending SMS permission
» pref_draw_on_top|string|false|Type of draw on top: <br> <b>Keep floating menu always on top</b>, <b>Keep floating menu during call only</b>, <b>Disable floating menu</b>
» pref_extend_working_hours|boolean|false|Show extended working hours (0-24) on termin panel
» pref_week_start_day|string|false|Preffered week start day for termin panel: <br> <b>Saturday</b>, <b>Sunday</b>, <b>Monday</b>
» pref_active_user_language|string|false|Active user language
» pref_time_format|string|false|Time format: <br> <b>24H</b>, <b>AM/PM</b>
» pref_send_sms_in_roaming_allowed|boolean|false|Sending SMS while in roaming allowed
» pref_default_currency|string|false|Default currency
» _id|string|false|Database record identifier
» _rev|string|false|Database record revision
» type|string|false|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
» time_create|string(date-time)|false|Date and time when record was created
» time_update|string(date-time)|false|Date and time when record was updated
» time_delete|string(date-time)|false|Date and time when record was deleted. Deleted records are not removed from database.
» user_create|string|false|User ID who created record.
» user_update|string|false|User ID who updated record.
» user_delete|string|false|User ID who deleted record.
» db_origin|string|false|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
» pref_draw_on_top|Keep floating menu always on top|
» pref_draw_on_top|Keep floating menu during call only|
» pref_draw_on_top|Disable floating menu|
» pref_week_start_day|Saturday|
» pref_week_start_day|Sunday|
» pref_week_start_day|Monday|
» pref_time_format|24H|
» pref_time_format|AM/PM|
» type|user|
» type|org|
» type|staff|
» type|client|
» type|licence|
» type|service|
» type|device|
» type|termin|
» type|recurring_meta|
» type|reminder|
» type|message_template|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## LicenceDbModel

<a name="schemalicencedbmodel"></a>

```json
{
  "date_expiration": "2017-11-28T15:27:45Z",
  "date_start": "2017-11-28T15:27:45Z",
  "activated": true,
  "db_org": "string",
  "appointments_per_month_limit": 0,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
date_expiration|string(date-time)|true|Date when licence expires
date_start|string(date-time)|true|Date when licence becomes active
activated|boolean|true|Is licence activated
db_org|string|true|Refference to organization database name that licence is for
appointments_per_month_limit|number(double)|false|Number of maximum allowed appointments per month
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## MessageTemplateDbModel

<a name="schemamessagetemplatedbmodel"></a>

```json
{
  "name": "string",
  "template": "string",
  "default": true,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
name|string|true|Template name
template|string|true|Template content: text and codes that are replaced when creating reminder
default|boolean|true|Is template default
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## RecurringMetaDbModel

<a name="schemarecurringmetadbmodel"></a>

```json
{
  "id_termin_original": "string",
  "start_date": "2017-11-28T15:27:45Z",
  "end_date": "2017-11-28T15:27:45Z",
  "freq": "once",
  "until_type": "counter",
  "until_counter": 0,
  "custom_days": 0,
  "custom_weeks": 0,
  "custom_months": 0,
  "cached_until": "2017-11-28T15:27:45Z",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id_termin_original|string|true|Original appointment ID that is recurring
start_date|string(date-time)|true|Sequence starting date
end_date|string(date-time)|true|Sequence ending date
freq|string|true|Recurring frequency codes: <br> <b>once</b>, <b>daily</b>, <b>weekly</b>, <b>monthly</b>, <b>yearly</b>, <b>custom</b>
until_type|string|true|The way recurring sequence stops: <br> <b>counter</b>: After number of occurences <br> <b>until_date</b>: When date is reached (including it) <br> <b>forever</b>: Never ending sequence
until_counter|number(double)|true|Number of occurences if until_type is counter
custom_days|number(double)|true|Number of days added if until_type is custom
custom_weeks|number(double)|true|Number of weeks added if until_type is custom
custom_months|number(double)|true|Number of months added if until_type is custom
cached_until|string(date-time)|true|Occurence dates are cached in original appointment. They are cached from the beggining until this date
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
freq|once|
freq|daily|
freq|weekly|
freq|monthly|
freq|yearly|
freq|custom|
until_type|counter|
until_type|until_date|
until_type|forever|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## ReminderDbModel

<a name="schemareminderdbmodel"></a>

```json
{
  "reminder_type": "sms",
  "reminder_status": "not_set",
  "error_code": "wrong_device",
  "before_type": "none",
  "custom_before_min": 0,
  "custom_before_hours": 0,
  "custom_before_days": 0,
  "recurring": true,
  "id_termin": "string",
  "id_recurring_meta": "string",
  "id_recurring_date": "2017-11-28T15:27:45Z",
  "recurring_termin_next_date": "2017-11-28T15:27:45Z",
  "recipient_type": "client",
  "id_client": "string",
  "id_staff": "string",
  "scheduled_time": "2017-11-28T15:27:45Z",
  "id_device": "string",
  "recipient_phone": "string",
  "id_message_template": "string",
  "message": "string",
  "snap_termin_time": "2017-11-28T15:27:45Z",
  "snap_termin_end_time": "2017-11-28T15:27:45Z",
  "snap_recipient_name": "string",
  "snap_org_name": "string",
  "snap_staff_name": "string",
  "snap_staff_phone": "string",
  "snap_service_name": "string",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
reminder_type|string|true|Reminder type codes: <br> <b>sms</b>: SMS reminder <br> <b>email</b>: Email message reminder <br> <b>device</b>: Push notification for device
reminder_status|string|true|Reminder status codes: <br> <b>not_set</b>: Reminder document exists but it is not set yet <br> <b>scheduled</b>: Final state for a reminder that was once scheduled and for some reason needs to be canceled <br> <b>canceled</b>: Final state for a reminder that was once scheduled and for some reason needs to be canceled <br> <b>sending</b>: When scheduled time occurs reminder sending process starts by marking its status as sending <br> <b>sent</b>: Final state for sent reminders <br> <b>failed</b>: Final state for failed reminders
error_code|string|true|Failed reminder error codes: <br> <b>wrong_device</b>: Sms not scheduled from device that tried sending <br> <b>termin_missing</b>: Appointment missing for a reminder <br> <b>termin_canceled</b>: Reminder not sent for canceled appointments <br> <b>time_frame</b>: Scheduled time missed for sending <br> <b>no_phone</b>: Phone number is missing <br> <b>no_message</b>: Message is missing <br> <b>permission_missing</b>: Automatic reminders not allowed in Settings <br> <b>roaming_disabled</b>: SMS roaming not allowed in Settings <br> <b>sms_sent_generic_failure</b>: Generic failure <br> <b>sms_sent_no_service</b>: No service <br> <b>sms_sent_null_pdu</b>: Null PDU <br> <b>sms_sent_radio_off</b>: Radio off <br> <b>sms_sent_unexpected</b>: Unexpected error <br> <b>sms_delivery_fail</b>: Message sent but not delivered
before_type|string|true|Time before appointment that reminder is scheduled for sending <br> <b>none</b>: Not scheduled <br> <b>at_time</b>: On appointment start time <br> <b>immediately</b>: Immediately send reminder <br> <b>hour_before_1</b>: One hour before appointment <br> <b>day_before_1</b>: One day before appointment <br> <b>custom_before</b>: On custom time before appointment
custom_before_min|number(double)|true|When custom before_type is choosen, minutes before the appointment
custom_before_hours|number(double)|true|When custom before_type is choosen, hours before the appointment
custom_before_days|number(double)|true|When custom before_type is choosen, days before the appointment
recurring|boolean|true|True if reminder is recurring
id_termin|string|true|Refference to appointment ID
id_recurring_meta|string|true|Reference to recurring meta data
id_recurring_date|string(date-time)|true|Reference to particular appointment in the sequence of recurring appointments. Date is for appointment starting date.
recurring_termin_next_date|string(date-time)|true|If reminder is recurring this is the next date when recurring appointment will occur
recipient_type|string|true|Recipient type codes: <br> <b>client</b>: Reminder for client <br> <b>staff</b>: Reminder for staff
id_client|string|true|Refference to recipient client document if client receives the reminder (not used at this moment)
id_staff|string|true|Refference to recipient staff document if staff receives the reminder (not used at this moment)
scheduled_time|string(date-time)|true|Scheduled date and time for a reminder to be sent
id_device|string|true|Refference to a device document that will be used for sending SMS reminder
recipient_phone|string|true|Recipient phone number
id_message_template|string|true|Refference to message template that will be used
message|string|true|Raw message as it will be sent
snap_termin_time|string(date-time)|true|Cached appointment start date and time
snap_termin_end_time|string(date-time)|true|Cached appointment end date and time
snap_recipient_name|string|true|Cached recipient name
snap_org_name|string|true|Cached organization name
snap_staff_name|string|true|Cached staff name
snap_staff_phone|string|true|Cached staff phone number
snap_service_name|string|true|Cached service name
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
reminder_type|sms|
reminder_type|email|
reminder_type|device|
reminder_status|not_set|
reminder_status|scheduled|
reminder_status|canceled|
reminder_status|sending|
reminder_status|sent|
reminder_status|failed|
error_code|wrong_device|
error_code|termin_missing|
error_code|termin_canceled|
error_code|time_frame|
error_code|no_phone|
error_code|no_message|
error_code|permission_missing|
error_code|roaming_disabled|
error_code|sms_sent_generic_failure|
error_code|sms_sent_no_service|
error_code|sms_sent_null_pdu|
error_code|sms_sent_radio_off|
error_code|sms_sent_unexpected|
error_code|sms_delivery_fail|
before_type|none|
before_type|at_time|
before_type|immediately|
before_type|hour_before_1|
before_type|day_before_1|
before_type|custom_before|
recipient_type|client|
recipient_type|staff|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## StaffDbModel

<a name="schemastaffdbmodel"></a>

```json
{
  "db_user": "string",
  "id_user": "string",
  "role_in_org": "string",
  "out_of_office": [
    {
      "time_create": "2017-11-28T15:27:45Z",
      "dates": [
        "2017-11-28T15:27:45Z"
      ],
      "description": "string",
      "freq": "once"
    }
  ],
  "is_available_on_portal": true,
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
db_user|string|true|Staff is a user that has it's own database. This is that database name
id_user|string|true|User ID
role_in_org|string|true|Role in organization (not used yet)
is_available_on_portal|boolean|false|If available on portal
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.
out_of_office|[object]|false|Out of office days
» time_create|string(date-time)|false|Time when out of office record was created
» description|string|false|Out of office record description
» freq|string|false|Out of office record frequency code: <br> <b>once</b>, <b>yearly</b>
» dates|[string(date-time)]|false|Dates when staff is out of office


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|
» freq|once|
» freq|yearly|


## UserDbModel

<a name="schemauserdbmodel"></a>

```json
{
  "username": "string",
  "name": "string",
  "email_secondary": "string",
  "occupation": "string",
  "phone": "string",
  "position": "string",
  "db": "string",
  "db_org_current": "string",
  "info": {
    "user_entered_app": true,
    "last_active_time": "2017-11-28T15:27:45Z",
    "termins_created": 0,
    "services_created": 0,
    "reminders_created": 0,
    "recurring_created": 0,
    "clients_created": 0,
    "review_asked_time": "2017-11-28T15:27:45Z",
    "review_clicked": true,
    "review_ask_never": true
  },
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
username|string|true|Username as email
name|string|true|Full name
email_secondary|string|true|Backup email
occupation|string|true|Occupation
phone|string|true|Phone number
position|string|true|Position in organization
db|string|true|User database name
db_org_current|string|true|Oragnization database name of curently used organization
info|object|true|Termin3 android application user activity
» user_entered_app|boolean|false|User has entered the Termin3 Android app
» last_active_time|string(date-time)|false|Last active date and time
» termins_created|number(double)|false|Total number of created appointments in current organization
» services_created|number(double)|false|Total number of services created in current organization
» reminders_created|number(double)|false|Total number of reminders created in current organization
» recurring_created|number(double)|false|Total number of recurring meta data created in current organization
» clients_created|number(double)|false|Total number of clients created in current organization
» review_asked_time|string(date-time)|false|Last date and time user has been asked to leave review on Google Play Store
» review_clicked|boolean|false|If user has clicked to leave a review
» review_ask_never|boolean|false|If user has clicked not to be bothered again with ask review
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|


## UserTermin3DbModel

<a name="schemausertermin3dbmodel"></a>

```json
{
  "username": "string",
  "name_initial": "string",
  "id_user": "string",
  "db_name": "string",
  "active": true,
  "email_primary": "string",
  "email_primary_confirmation_key": "string",
  "email_primary_confirmed": "string",
  "email_primary_sent_time": "2017-11-28T15:27:45Z",
  "_id": "string",
  "_rev": "string",
  "type": "user",
  "time_create": "2017-11-28T15:27:45Z",
  "time_update": "2017-11-28T15:27:45Z",
  "time_delete": "2017-11-28T15:27:45Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
username|string|true|Username as email
name_initial|string|true|Full name as entered for the first time
id_user|string|true|User database document ID
db_name|string|true|User database name
active|boolean|true|If user is active
email_primary|string|true|email
email_primary_confirmation_key|string|true|Confirmation key used for email confirmation
email_primary_confirmed|string|true|User has confirmed its email
email_primary_sent_time|string(date-time)|true|Date and time confirmation email has been sent
_id|string|true|Database record identifier
_rev|string|true|Database record revision
type|string|true|Database record type. Determines the type of database record <br> System types: <b>user</b>, <b>org</b> <br> Termin3 types: <b>staff</b>, <b>client</b>, <b>licence</b>, <b>service</b>, <b>device</b>, <b>termin</b>, <b>recurring_meta</b>, <b>reminder</b>, <b>message_template</b>
time_create|string(date-time)|true|Date and time when record was created
time_update|string(date-time)|true|Date and time when record was updated
time_delete|string(date-time)|true|Date and time when record was deleted. Deleted records are not removed from database.
user_create|string|true|User ID who created record.
user_update|string|true|User ID who updated record.
user_delete|string|true|User ID who deleted record.
db_origin|string|true|Name of organization database where document was originally created. It can be moved to other database via replication. That is whay we need origin.


#### Enumerated Values

|Property|Value|
|---|---|
type|user|
type|org|
type|staff|
type|client|
type|licence|
type|service|
type|device|
type|termin|
type|recurring_meta|
type|reminder|
type|message_template|




