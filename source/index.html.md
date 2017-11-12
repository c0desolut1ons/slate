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

* <a href="http://localhost:33301">http://localhost:33301</a>



 License: MIT

# Authentication


* API Key
    - Parameter Name: **access_token**, in: query. 



# Appointments

## AppointmentsApiRead

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:33301/organizations/{org_db}/appointments/available?date_from=string&date_to=string \
  -H 'Accept: text/html'

```

```http
GET http://localhost:33301/organizations/{org_db}/appointments/available?date_from=string&date_to=string HTTP/1.1
Host: localhost:33301

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: 'http://localhost:33301/organizations/{org_db}/appointments/available',
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

fetch('http://localhost:33301/organizations/{org_db}/appointments/available?date_from=string&date_to=string',
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

result = RestClient.get 'http://localhost:33301/organizations/{org_db}/appointments/available',
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

r = requests.get('http://localhost:33301/organizations/{org_db}/appointments/available', params={
  'date_from': 'string',  'date_to': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://localhost:33301/organizations/{org_db}/appointments/available?date_from=string&date_to=string");
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
date_from|query|string|true|Pocetni datum od koga trazimo termine ukljucujuci i njega. Ako je izostavljen onda je - beskonacno
date_to|query|string|true|Krajnji datum do koga trazimo termine ukljucujuci i njega. Ako je izostavljen onda je + beskonacno


> Example responses

```json
[
  {
    "status": "string",
    "time_start": "2017-11-12T15:24:11Z",
    "time_end": "2017-11-12T15:24:11Z",
    "sms_reminder": "2017-11-12T15:24:11Z",
    "note": "string",
    "id_client": "string",
    "id_service": "string",
    "staff": [
      {
        "id_staff": "string",
        "occupation": "string"
      }
    ],
    "freq": "string",
    "id_recurring_meta": "string",
    "recurring_state": "string",
    "recurring_exception_date": "2017-11-12T15:24:11Z",
    "recurring_dates": [
      "2017-11-12T15:24:11Z"
    ],
    "booking_info": {
      "client_name": "string",
      "client_phone_number": "string"
    },
    "_id": "string",
    "_rev": "string",
    "type": "string",
    "time_create": "2017-11-12T15:24:11Z",
    "time_update": "2017-11-12T15:24:11Z",
    "time_delete": "2017-11-12T15:24:11Z",
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
» status|string|false|Termin status codes:<br> <b>step 1</b>: choose service<br> <b>step 2</b>: choose time <br> <b>step 3</b>: choose client <br> <b>confirmed</b>: Confirmed appointment <br> <b>canceled</b>: Appointment that have been canceled <br> <b>noshow</b>: Client didn't show up when scheduled
» time_start|string(date-time)|false|Date and time when appointment starts
» time_end|string(date-time)|false|Date and time when appointment ends
» sms_reminder|string(date-time)|false|Deprecated
» note|string|false|Note about the appointment
» id_client|string|false|Reference to Client document ID
» id_service|string|false|Reference to Service document ID
» freq|string|false|Recurring frequency code: <br> <b>once</b> <br> <b>daily</b> <br> <b>weekly</b> <br> <b>monthly</b> <br> <b>yearly</b> <br> <b>custom</b>
» id_recurring_meta|string|false|Reference to Recurring Meta document ID
» recurring_state|string|false|Meta data describing termin object in context of recurring appointments: <br> <b>no_recurring</b>: single, no recurring appointment <br> <b>original</b>: first appointment in the recurring sequence <br> <b>exception</b>: appointment that is exception from recurring sequence <br> <b>virtual</b>: recurring appointment that is not first in the sequence. These are not saved in the database.
» recurring_exception_date|string(date-time)|false|If appointment is recurring exception this is the original date when appointment was part of the sequence
» booking_info|object|false|Booking information left by the client on Termin3 portal
»» client_name|string|false|Client name that was enetered by client on portal
»» client_phone_number|string|false|Client phone number that was enetered by client on portal
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
»» occupation|string|false|Staff occupation for particular appointment: technician, doctor, employee...
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
curl -X PUT http://localhost:33301/organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string \
  -H 'Accept: text/html'

```

```http
PUT http://localhost:33301/organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string HTTP/1.1
Host: localhost:33301

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: 'http://localhost:33301/organizations/{org_db}/appointments/available/{id}',
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

fetch('http://localhost:33301/organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string',
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

result = RestClient.put 'http://localhost:33301/organizations/{org_db}/appointments/available/{id}',
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

r = requests.put('http://localhost:33301/organizations/{org_db}/appointments/available/{id}', params={
  'name': 'string',  'phone_number': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://localhost:33301/organizations/{org_db}/appointments/available/{id}?name=string&phone_number=string");
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
id|path|string|true|Document ID termina koji azuriramo
name|query|string|true|Ime klijenta koje upisujemo u termin
phone_number|query|string|true|Broj telefona klijenta koje upisujemo u termin


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

# Domain

## DomainApiRead

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:33301/domains/{name} \
  -H 'Accept: text/html'

```

```http
GET http://localhost:33301/domains/{name} HTTP/1.1
Host: localhost:33301

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: 'http://localhost:33301/domains/{name}',
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

fetch('http://localhost:33301/domains/{name}',
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

result = RestClient.get 'http://localhost:33301/domains/{name}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('http://localhost:33301/domains/{name}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://localhost:33301/domains/{name}");
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
  "time_created": "2017-11-12T15:24:11Z",
  "is_available": true,
  "is_public": true
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



<h3 id="DomainApiRead-responseschema">Response Schema</h3>

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
curl -X GET http://localhost:33301/organizations/{org_db} \
  -H 'Accept: application/json'

```

```http
GET http://localhost:33301/organizations/{org_db} HTTP/1.1
Host: localhost:33301

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'http://localhost:33301/organizations/{org_db}',
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

fetch('http://localhost:33301/organizations/{org_db}',
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

result = RestClient.get 'http://localhost:33301/organizations/{org_db}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('http://localhost:33301/organizations/{org_db}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://localhost:33301/organizations/{org_db}");
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

Dohvatanje ID dokumenta organizacije

<h3 id="OrganizationApiRead-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
org_db|path|string|true|


> Example responses

```json
{}
```
<h3 id="OrganizationApiRead-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|object

<aside class="success">
This operation does not require authentication
</aside>

# Services

## OrganizationApiGetServices

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:33301/organizations/{org_db}/services \
  -H 'Accept: application/json'

```

```http
GET http://localhost:33301/organizations/{org_db}/services HTTP/1.1
Host: localhost:33301

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'http://localhost:33301/organizations/{org_db}/services',
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

fetch('http://localhost:33301/organizations/{org_db}/services',
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

result = RestClient.get 'http://localhost:33301/organizations/{org_db}/services',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('http://localhost:33301/organizations/{org_db}/services', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://localhost:33301/organizations/{org_db}/services");
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

<h3 id="OrganizationApiGetServices-parameters">Parameters</h3>

Parameter|In|Type|Required|Description
---|---|---|---|---|
org_db|path|string|true|


> Example responses

```json
{}
```
<h3 id="OrganizationApiGetServices-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|object

<aside class="success">
This operation does not require authentication
</aside>

# Register/login

## RegisterApiCreate

> Code samples

```shell
# You can also use wget
curl -X POST http://localhost:33301/register?name=string&pass=string&email_primary=string&email_secondary=string \
  -H 'Accept: application/json'

```

```http
POST http://localhost:33301/register?name=string&pass=string&email_primary=string&email_secondary=string HTTP/1.1
Host: localhost:33301

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'http://localhost:33301/register',
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

fetch('http://localhost:33301/register?name=string&pass=string&email_primary=string&email_secondary=string',
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

result = RestClient.post 'http://localhost:33301/register',
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

r = requests.post('http://localhost:33301/register', params={
  'name': 'string',  'pass': 'string',  'email_primary': 'string',  'email_secondary': 'string'
}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://localhost:33301/register?name=string&pass=string&email_primary=string&email_secondary=string");
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

## StatsApiRead

> Code samples

```shell
# You can also use wget
curl -X GET http://localhost:33301/stats/org_count \
  -H 'Accept: text/html'

```

```http
GET http://localhost:33301/stats/org_count HTTP/1.1
Host: localhost:33301

Accept: text/html

```

```javascript
var headers = {
  'Accept':'text/html'

};

$.ajax({
  url: 'http://localhost:33301/stats/org_count',
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

fetch('http://localhost:33301/stats/org_count',
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

result = RestClient.get 'http://localhost:33301/stats/org_count',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'text/html'
}

r = requests.get('http://localhost:33301/stats/org_count', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("http://localhost:33301/stats/org_count");
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

`GET /stats/org_count`

Counting organizations

> Example responses

<h3 id="StatsApiRead-responses">Responses</h3>

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ok|number(double)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|string

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## StaffOnTermin

<a name="schemastaffontermin"></a>

```json
{
  "id_staff": "string",
  "occupation": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id_staff|string|true|Reference to Staff document ID
occupation|string|true|Staff occupation for particular appointment: technician, doctor, employee...



## BookingInfo

<a name="schemabookinginfo"></a>

```json
{
  "client_name": "string",
  "client_phone_number": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
client_name|string|true|Client name that was enetered by client on portal
client_phone_number|string|true|Client phone number that was enetered by client on portal



## TerminDbModel

<a name="schematermindbmodel"></a>

```json
{
  "status": "string",
  "time_start": "2017-11-12T15:24:11Z",
  "time_end": "2017-11-12T15:24:11Z",
  "sms_reminder": "2017-11-12T15:24:11Z",
  "note": "string",
  "id_client": "string",
  "id_service": "string",
  "staff": [
    {
      "id_staff": "string",
      "occupation": "string"
    }
  ],
  "freq": "string",
  "id_recurring_meta": "string",
  "recurring_state": "string",
  "recurring_exception_date": "2017-11-12T15:24:11Z",
  "recurring_dates": [
    "2017-11-12T15:24:11Z"
  ],
  "booking_info": {
    "client_name": "string",
    "client_phone_number": "string"
  },
  "_id": "string",
  "_rev": "string",
  "type": "string",
  "time_create": "2017-11-12T15:24:11Z",
  "time_update": "2017-11-12T15:24:11Z",
  "time_delete": "2017-11-12T15:24:11Z",
  "user_create": "string",
  "user_update": "string",
  "user_delete": "string",
  "db_origin": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
status|string|true|Termin status codes:<br> <b>step 1</b>: choose service<br> <b>step 2</b>: choose time <br> <b>step 3</b>: choose client <br> <b>confirmed</b>: Confirmed appointment <br> <b>canceled</b>: Appointment that have been canceled <br> <b>noshow</b>: Client didn't show up when scheduled
time_start|string(date-time)|true|Date and time when appointment starts
time_end|string(date-time)|true|Date and time when appointment ends
sms_reminder|string(date-time)|true|Deprecated
note|string|true|Note about the appointment
id_client|string|true|Reference to Client document ID
id_service|string|true|Reference to Service document ID
freq|string|true|Recurring frequency code: <br> <b>once</b> <br> <b>daily</b> <br> <b>weekly</b> <br> <b>monthly</b> <br> <b>yearly</b> <br> <b>custom</b>
id_recurring_meta|string|true|Reference to Recurring Meta document ID
recurring_state|string|true|Meta data describing termin object in context of recurring appointments: <br> <b>no_recurring</b>: single, no recurring appointment <br> <b>original</b>: first appointment in the recurring sequence <br> <b>exception</b>: appointment that is exception from recurring sequence <br> <b>virtual</b>: recurring appointment that is not first in the sequence. These are not saved in the database.
recurring_exception_date|string(date-time)|true|If appointment is recurring exception this is the original date when appointment was part of the sequence
booking_info|object|true|Booking information left by the client on Termin3 portal
» client_name|string|false|Client name that was enetered by client on portal
» client_phone_number|string|false|Client phone number that was enetered by client on portal
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
» occupation|string|false|Staff occupation for particular appointment: technician, doctor, employee...
recurring_dates|[string(date-time)]|false|Cached dates when recurring appointments should occur. <br> This field appears for original recurring termin documents. <br> It is used for performance optimization.



## DocumentChangedResponseApiModel

<a name="schemadocumentchangedresponseapimodel"></a>

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



## DomainInfoDbModel

<a name="schemadomaininfodbmodel"></a>

```json
{
  "domain_name": "string",
  "org_db": "string",
  "time_created": "2017-11-12T15:24:11Z",
  "is_available": true,
  "is_public": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
domain_name|string|true|Domain name
org_db|string|true|Organization database name
time_created|string(date-time)|false|Date and time when domain was created
is_available|boolean|true|Is domain available. If not then it is already reserved by someone else.
is_public|boolean|true|Is domain public, meaning if reserved domain has been publicly released.





