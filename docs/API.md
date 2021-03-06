## Classes

<dl>
<dt><a href="#Database">Database</a></dt>
<dd><p>Database Module containing functions for-
Insertion and Deletion of Subscriptions for both, APN and other browsers
Updating User Notification Preferences
Fetching User Notification Preferences</p>
</dd>
<dt><a href="#Notifications">Notifications</a></dt>
<dd></dd>
<dt><a href="#OAuth">OAuth</a></dt>
<dd><p>Authenticates users via CERN OAuth 2.0.
Gathers user account details.</p>
</dd>
<dt><a href="#HttpServer">HttpServer</a></dt>
<dd><p>HTTPS server that handles OAuth and provides REST API.
Each request is authenticated with JWT token.</p>
</dd>
<dt><a href="#JwtToken">JwtToken</a></dt>
<dd><p>Provides JSON Web Token functionality such as token generation and verification.</p>
</dd>
<dt><a href="#Response">Response</a></dt>
<dd><p>WebSocket module that allows to create response to user request.
It&#39;s based on HTTP status codes.</p>
</dd>
<dt><a href="#WebSocket">WebSocket</a></dt>
<dd><p>It represents WebSocket server (RFC 6455).
In addition, it provides custom authentication with JWT tokens.</p>
</dd>
<dt><a href="#ZeroMQClient">ZeroMQClient</a></dt>
<dd><p>ZeroMQ client that communicates with Control Master prcess via one of two supported
socket patterns (sub and req).</p>
</dd>
</dl>

## Functions

<dl>
<dt><a href="#triggerPushMsg">triggerPushMsg(subscription, dataToSend)</a> ⇒ <code>promise</code></dt>
<dd><p>Sends push notifications to subscribed users</p>
</dd>
<dt><a href="#deleteSubscriptionFromDatabase">deleteSubscriptionFromDatabase(endpoint)</a> ⇒ <code>promise</code></dt>
<dd><p>Deletes user subscriptions from Database</p>
</dd>
<dt><a href="#getSubscriptions">getSubscriptions()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches subscriptions from Database</p>
</dd>
<dt><a href="#getAPNSubscriptions">getAPNSubscriptions()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches APN subscriptions from Database</p>
</dd>
<dt><a href="#formatSubscription">formatSubscription(sub)</a> ⇒ <code>object</code></dt>
<dd><p>Formats the subscription to a suitable format to be sent to &#39;web-push&#39; server</p>
</dd>
<dt><a href="#sendNotif">sendNotif()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches subscriptions from db then verifies them and sends notifications.</p>
</dd>
<dt><a href="#sendAPNNotif">sendAPNNotif()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches APN subscriptions from db then verifies them and sends notifications.</p>
</dd>
<dt><a href="#_create">_create()</a></dt>
<dd><p>Create widget instance</p>
</dd>
<dt><a href="#_connect">_connect()</a></dt>
<dd><p>Connect to Websocket endpoint and specyfies WebSocket event listeners</p>
</dd>
<dt><a href="#send">send(message)</a></dt>
<dd><p>Send message to WebSocket server</p>
</dd>
<dt><a href="#triggerPushMsg">triggerPushMsg(subscription, dataToSend)</a> ⇒ <code>promise</code></dt>
<dd><p>Sends push notifications to subscribed users</p>
</dd>
<dt><a href="#deleteSubscriptionFromDatabase">deleteSubscriptionFromDatabase(endpoint)</a> ⇒ <code>promise</code></dt>
<dd><p>Deletes user subscriptions from Database</p>
</dd>
<dt><a href="#getSubscriptions">getSubscriptions()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches subscriptions from Database</p>
</dd>
<dt><a href="#getAPNSubscriptions">getAPNSubscriptions()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches APN subscriptions from Database</p>
</dd>
<dt><a href="#formatSubscription">formatSubscription(sub)</a> ⇒ <code>object</code></dt>
<dd><p>Formats the subscription to a suitable format to be sent to &#39;web-push&#39; server</p>
</dd>
<dt><a href="#sendNotif">sendNotif()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches subscriptions from db then verifies them and sends notifications.</p>
</dd>
<dt><a href="#sendAPNNotif">sendAPNNotif()</a> ⇒ <code>promise</code></dt>
<dd><p>Fetches APN subscriptions from db then verifies them and sends notifications.</p>
</dd>
</dl>

<a name="Database"></a>

## Database
Database Module containing functions for-
Insertion and Deletion of Subscriptions for both, APN and other browsers
Updating User Notification Preferences
Fetching User Notification Preferences

**Kind**: global class  
**Author**: Anirudh Goel <anirudh.goel@cern.ch>  

* [Database](#Database)
    * [new Database(config)](#new_Database_new)
    * [.insertSubscription(sub)](#Database+insertSubscription) ⇒ <code>Promise</code>
    * [.deleteSubscription(endpoint)](#Database+deleteSubscription) ⇒ <code>Promise</code>
    * [.updatePreferences(data)](#Database+updatePreferences) ⇒ <code>Promise</code>
    * [.getPreferences(data)](#Database+getPreferences) ⇒ <code>Promise</code>
    * [.insertSubscriptionSafari(deviceToken)](#Database+insertSubscriptionSafari) ⇒ <code>Promise</code>
    * [.deleteSubscriptionSafari(deviceToken)](#Database+deleteSubscriptionSafari) ⇒ <code>Promise</code>
    * [.updatePreferencesSafari(data)](#Database+updatePreferencesSafari) ⇒ <code>Promise</code>
    * [.getPreferencesSafari(data)](#Database+getPreferencesSafari) ⇒ <code>Promise</code>

<a name="new_Database_new"></a>

### new Database(config)
Establishes connections with MySQL Database


| Param | Type | Description |
| --- | --- | --- |
| config | <code>object</code> | configuration object for db, see docs for more details |

<a name="Database+insertSubscription"></a>

### database.insertSubscription(sub) ⇒ <code>Promise</code>
Saves 'web-push' subscription object to Database

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| sub | <code>object</code> | Subscription Object |

<a name="Database+deleteSubscription"></a>

### database.deleteSubscription(endpoint) ⇒ <code>Promise</code>
Module for deleting subscriotion from MySQL database

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| endpoint | <code>string</code> | Subscription Endpoint |

<a name="Database+updatePreferences"></a>

### database.updatePreferences(data) ⇒ <code>Promise</code>
Module for updating user notification preferences in MySQL database

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>object</code> | Preferences Object |

<a name="Database+getPreferences"></a>

### database.getPreferences(data) ⇒ <code>Promise</code>
Module for fetching user notification preferences from MySQL database

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>object</code> | Object containing Endpoint |

<a name="Database+insertSubscriptionSafari"></a>

### database.insertSubscriptionSafari(deviceToken) ⇒ <code>Promise</code>
Save Safari subscription to MySQL database

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| deviceToken | <code>string</code> | Unique Device Identifier Token |

<a name="Database+deleteSubscriptionSafari"></a>

### database.deleteSubscriptionSafari(deviceToken) ⇒ <code>Promise</code>
Delete Safari subscriotion from MySQL database

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| deviceToken | <code>string</code> | Unique Device Identifier Token |

<a name="Database+updatePreferencesSafari"></a>

### database.updatePreferencesSafari(data) ⇒ <code>Promise</code>
Module for updating user notification preferences in MySQL database for APNs

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>object</code> | Object containing Device Token and preferences |

<a name="Database+getPreferencesSafari"></a>

### database.getPreferencesSafari(data) ⇒ <code>Promise</code>
Module for fetching user notification preferences from MySQL database for APNs

**Kind**: instance method of [<code>Database</code>](#Database)  
**Returns**: <code>Promise</code> - Promise  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>object</code> | Object containing Device Token |

<a name="Notifications"></a>

## Notifications
**Kind**: global class  

* [Notifications](#Notifications)
    * [new Notifications(server, config)](#new_Notifications_new)
    * [.saveSubscription(req, res)](#Notifications+saveSubscription)
    * [.updatePref(req, res)](#Notifications+updatePref)
    * [.getPref(req, res)](#Notifications+getPref)
    * [.deleteSubscription(req, res)](#Notifications+deleteSubscription)
    * [.safariPermission(res)](#Notifications+safariPermission)
    * [.safariSubscribe(req, res)](#Notifications+safariSubscribe)
    * [.safariUnsubscribe(req, res)](#Notifications+safariUnsubscribe)
    * [.getPrefSafari(req, res)](#Notifications+getPrefSafari)
    * [.updatePrefSafari(req, res)](#Notifications+updatePrefSafari)

<a name="new_Notifications_new"></a>

### new Notifications(server, config)
Sets up VAPID keys and specified REST API routes


| Param | Type | Description |
| --- | --- | --- |
| server | <code>object</code> | https server |
| config | <code>object</code> | configuration object (see documentation for the description of fields) |

<a name="Notifications+saveSubscription"></a>

### notifications.saveSubscription(req, res)
Receives User Subscription object from 'web-push' server
and saves it to Database

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="Notifications+updatePref"></a>

### notifications.updatePref(req, res)
Receives User Notification Preferences and updates it in Database

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="Notifications+getPref"></a>

### notifications.getPref(req, res)
Gets User Notification Preferences from Database
and passes it to browser

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="Notifications+deleteSubscription"></a>

### notifications.deleteSubscription(req, res)
Deletes user subscription from database

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="Notifications+safariPermission"></a>

### notifications.safariPermission(res)
When the user clicks on 'Allow' in notification prompt box,
a call is made to this function to receive a zipped push package.

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| res | <code>object</code> | response object |

<a name="Notifications+safariSubscribe"></a>

### notifications.safariSubscribe(req, res)
Receives Device Token from APN server
and saves it to Database

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="Notifications+safariUnsubscribe"></a>

### notifications.safariUnsubscribe(req, res)
When user removes/denies the notifications from Safari Preferences,
a call to this function is made.

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="Notifications+getPrefSafari"></a>

### notifications.getPrefSafari(req, res)
Gets User Notification Preferences for APNs from Database
and passes it to browser

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="Notifications+updatePrefSafari"></a>

### notifications.updatePrefSafari(req, res)
Receives User APNs Notification Preferences and updates it in Database

**Kind**: instance method of [<code>Notifications</code>](#Notifications)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | request object |
| res | <code>object</code> | response object |

<a name="OAuth"></a>

## OAuth
Authenticates users via CERN OAuth 2.0.
Gathers user account details.

**Kind**: global class  
**Author**: Adam Wegrzynek <adam.wegrzynek@cern.ch>  
**Todo**

- [ ] e-group authorization


* [OAuth](#OAuth)
    * [new OAuth(config)](#new_OAuth_new)
    * [.oAuthCallback(emitter, code)](#OAuth+oAuthCallback)
    * [.oAuthGetUserDetails(token, emitter)](#OAuth+oAuthGetUserDetails)

<a name="new_OAuth_new"></a>

### new OAuth(config)
Creates OAuth object based on id and secret stored in config file.


| Param | Type | Description |
| --- | --- | --- |
| config | <code>object</code> | configuration object (see docs for details) |

<a name="OAuth+oAuthCallback"></a>

### oAuth.oAuthCallback(emitter, code)
OAuth redirection callback (called by library).

**Kind**: instance method of [<code>OAuth</code>](#OAuth)  

| Param | Type | Description |
| --- | --- | --- |
| emitter | <code>object</code> |  |
| code | <code>number</code> | authorization code to request access token |

<a name="OAuth+oAuthGetUserDetails"></a>

### oAuth.oAuthGetUserDetails(token, emitter)
Queries user details using received access token.

**Kind**: instance method of [<code>OAuth</code>](#OAuth)  

| Param | Type | Description |
| --- | --- | --- |
| token | <code>string</code> | OAuth access token |
| emitter | <code>object</code> |  |

<a name="HttpServer"></a>

## HttpServer
HTTPS server that handles OAuth and provides REST API.
Each request is authenticated with JWT token.

**Kind**: global class  
**Author**: Adam Wegrzynek <adam.wegrzynek@cern.ch>  

* [HttpServer](#HttpServer)
    * [new HttpServer(httpConfig, jwtConfig, oAuthConfig)](#new_HttpServer_new)
    * [.server](#HttpServer+server) ⇒ <code>object</code>
    * [.passToTemplate(key, value)](#HttpServer+passToTemplate)
    * [.specifyRoutes()](#HttpServer+specifyRoutes)
    * [.post(path, callback)](#HttpServer+post)
    * [.postNoAuth(path, callback)](#HttpServer+postNoAuth)
    * [.deleteNoAuth(path, callback)](#HttpServer+deleteNoAuth)
    * [.enableHttpRedirect()](#HttpServer+enableHttpRedirect)
    * [.oAuthAuthorize(res)](#HttpServer+oAuthAuthorize)
    * [.oAuthCallback(req, res)](#HttpServer+oAuthCallback)
    * [.renderPage(page, data)](#HttpServer+renderPage) ⇒ <code>string</code>
    * [.jwtVerify(req, res, next)](#HttpServer+jwtVerify)
    * [.runs(req, res)](#HttpServer+runs)

<a name="new_HttpServer_new"></a>

### new HttpServer(httpConfig, jwtConfig, oAuthConfig)
Sets up the server, routes and binds HTTP and HTTPS sockets.


| Param | Type | Description |
| --- | --- | --- |
| httpConfig | <code>object</code> | configuration of HTTP server |
| jwtConfig | <code>object</code> | configuration of JWT |
| oAuthConfig | <code>object</code> | configuration of oAuth |

<a name="HttpServer+server"></a>

### httpServer.server ⇒ <code>object</code>
HTTPs server getter.

**Kind**: instance property of [<code>HttpServer</code>](#HttpServer)  
**Returns**: <code>object</code> - - HTTPs server  
<a name="HttpServer+passToTemplate"></a>

### httpServer.passToTemplate(key, value)
Passes key-value that can be used in template

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  

| Param | Type | Description |
| --- | --- | --- |
| key | <code>string</code> | allows to access value from temaplte |
| value | <code>string</code> |  |

<a name="HttpServer+specifyRoutes"></a>

### httpServer.specifyRoutes()
Specified routes and their callbacks.

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  
<a name="HttpServer+post"></a>

### httpServer.post(path, callback)
Adds POST route

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  

| Param | Type | Description |
| --- | --- | --- |
| path | <code>string</code> | path that the callback will be bound to |
| callback | <code>function</code> | function (that receives req and res parameters) |

<a name="HttpServer+postNoAuth"></a>

### httpServer.postNoAuth(path, callback)
Adds POST route without authentication

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  

| Param | Type | Description |
| --- | --- | --- |
| path | <code>string</code> | path that the callback will be bound to |
| callback | <code>function</code> | function (that receives req and res parameters) |

<a name="HttpServer+deleteNoAuth"></a>

### httpServer.deleteNoAuth(path, callback)
Adds DELETE route without authentication

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  

| Param | Type | Description |
| --- | --- | --- |
| path | <code>string</code> | path that the callback will be bound to |
| callback | <code>function</code> | function (that receives req and res parameters) |

<a name="HttpServer+enableHttpRedirect"></a>

### httpServer.enableHttpRedirect()
Redirects HTTP to HTTPS.

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  
<a name="HttpServer+oAuthAuthorize"></a>

### httpServer.oAuthAuthorize(res)
OAuth redirection.

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  

| Param | Type | Description |
| --- | --- | --- |
| res | <code>object</code> | HTTP response |

<a name="HttpServer+oAuthCallback"></a>

### httpServer.oAuthCallback(req, res)
OAuth callback if authentication succeeds.

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | HTTP request |
| res | <code>object</code> | HTTP response |

<a name="HttpServer+renderPage"></a>

### httpServer.renderPage(page, data) ⇒ <code>string</code>
Renders template using Mustache engine.

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  
**Returns**: <code>string</code> - - HTML page  

| Param | Type | Description |
| --- | --- | --- |
| page | <code>string</code> | template file path |
| data | <code>object</code> | data to fill the template with |

<a name="HttpServer+jwtVerify"></a>

### httpServer.jwtVerify(req, res, next)
Verifies JWT token synchronously.

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  
**Todo**

- [ ] use promises or generators to call it asynchronously!


| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | HTTP request |
| res | <code>object</code> | HTTP response |
| next | <code>function</code> | passes control to next matching route |

<a name="HttpServer+runs"></a>

### httpServer.runs(req, res)
For the test purposes.
Simply returns JSON encoded fixed run number.

**Kind**: instance method of [<code>HttpServer</code>](#HttpServer)  

| Param | Type | Description |
| --- | --- | --- |
| req | <code>object</code> | HTTP request |
| res | <code>object</code> | HTTP response |

<a name="JwtToken"></a>

## JwtToken
Provides JSON Web Token functionality such as token generation and verification.

**Kind**: global class  
**Author**: Adam Wegrzynek <adam.wegrzynek@cern.ch>  

* [JwtToken](#JwtToken)
    * [new JwtToken(config)](#new_JwtToken_new)
    * [.generateToken(personid, username, access)](#JwtToken+generateToken) ⇒ <code>object</code>
    * [.refreshToken(token)](#JwtToken+refreshToken) ⇒ <code>object</code>
    * [.verify(token)](#JwtToken+verify) ⇒ <code>object</code>

<a name="new_JwtToken_new"></a>

### new JwtToken(config)
Stores secret


| Param | Type | Description |
| --- | --- | --- |
| config | <code>object</code> | jwt cofiguration object |

<a name="JwtToken+generateToken"></a>

### jwtToken.generateToken(personid, username, access) ⇒ <code>object</code>
Generates encrypted token with user id and access level.
Sets expiration time and sings it using secret.

**Kind**: instance method of [<code>JwtToken</code>](#JwtToken)  
**Returns**: <code>object</code> - generated token  

| Param | Type | Description |
| --- | --- | --- |
| personid | <code>number</code> | CERN user id |
| username | <code>string</code> | CERN username |
| access | <code>number</code> | level of access |

<a name="JwtToken+refreshToken"></a>

### jwtToken.refreshToken(token) ⇒ <code>object</code>
When the token expires, this method allows to refresh it.
It skips expiration check and verifies (already expired) token based on maxAge parameter
(maxAge >> expiration).
Then it creates a new token using parameters of the old one and ships it to the user.
If maxAge timeouts, the user needs to re-login via OAuth.

**Kind**: instance method of [<code>JwtToken</code>](#JwtToken)  
**Returns**: <code>object</code> - new token or false in case of failure  

| Param | Type | Description |
| --- | --- | --- |
| token | <code>object</code> | expired token |

<a name="JwtToken+verify"></a>

### jwtToken.verify(token) ⇒ <code>object</code>
Decrypts user token to verify that is vaild.

**Kind**: instance method of [<code>JwtToken</code>](#JwtToken)  
**Returns**: <code>object</code> - whether operation was successful, if so decoded data are passed as well  

| Param | Type | Description |
| --- | --- | --- |
| token | <code>object</code> | token to be verified |

<a name="Response"></a>

## Response
WebSocket module that allows to create response to user request.
It's based on HTTP status codes.

**Kind**: global class  
**Author**: Adam Wegrzynek <adam.wegrzynek@cern.ch>  

* [Response](#Response)
    * [new Response(code)](#new_Response_new)
    * [.getcode](#Response+getcode) ⇒ <code>number</code>
    * [.getcommand](#Response+getcommand) ⇒ <code>string</code>
    * [.getbroadcast](#Response+getbroadcast) ⇒ <code>bool</code>
    * [.getpayload](#Response+getpayload) ⇒ <code>object</code>
    * [.json](#Response+json) ⇒ <code>object</code>
    * [._message(code)](#Response+_message) ⇒ <code>string</code>
    * [.command(command)](#Response+command) ⇒ <code>object</code>
    * [.broadcast()](#Response+broadcast) ⇒ <code>object</code>
    * [.payload(payload)](#Response+payload) ⇒ <code>object</code>

<a name="new_Response_new"></a>

### new Response(code)
Sets initial variables.


| Param | Type | Description |
| --- | --- | --- |
| code | <code>number</code> | response code (based on HTTP) |

<a name="Response+getcode"></a>

### response.getcode ⇒ <code>number</code>
**Kind**: instance property of [<code>Response</code>](#Response)  
**Returns**: <code>number</code> - code  
<a name="Response+getcommand"></a>

### response.getcommand ⇒ <code>string</code>
**Kind**: instance property of [<code>Response</code>](#Response)  
**Returns**: <code>string</code> - command  
<a name="Response+getbroadcast"></a>

### response.getbroadcast ⇒ <code>bool</code>
**Kind**: instance property of [<code>Response</code>](#Response)  
**Returns**: <code>bool</code> - broadcast flag  
<a name="Response+getpayload"></a>

### response.getpayload ⇒ <code>object</code>
**Kind**: instance property of [<code>Response</code>](#Response)  
**Returns**: <code>object</code> - payload  
<a name="Response+json"></a>

### response.json ⇒ <code>object</code>
Formats the reponse to object that is ready to be formatted into JSON.

**Kind**: instance property of [<code>Response</code>](#Response)  
**Returns**: <code>object</code> - response  
<a name="Response+_message"></a>

### response._message(code) ⇒ <code>string</code>
Provides HTTP message based on code.

**Kind**: instance method of [<code>Response</code>](#Response)  
**Returns**: <code>string</code> - message for given code  

| Param | Type |
| --- | --- |
| code | <code>number</code> | 

<a name="Response+command"></a>

### response.command(command) ⇒ <code>object</code>
Command setter.

**Kind**: instance method of [<code>Response</code>](#Response)  
**Returns**: <code>object</code> - 'this' to allow function call chaining  

| Param | Type | Description |
| --- | --- | --- |
| command | <code>string</code> | user request command |

<a name="Response+broadcast"></a>

### response.broadcast() ⇒ <code>object</code>
Set broadcast flag to true.

**Kind**: instance method of [<code>Response</code>](#Response)  
**Returns**: <code>object</code> - 'this' to allow function call chaining  
<a name="Response+payload"></a>

### response.payload(payload) ⇒ <code>object</code>
Payload setter.

**Kind**: instance method of [<code>Response</code>](#Response)  
**Returns**: <code>object</code> - 'this' to allow function call chaining  

| Param | Type |
| --- | --- |
| payload | <code>object</code> | 

<a name="WebSocket"></a>

## WebSocket
It represents WebSocket server (RFC 6455).
In addition, it provides custom authentication with JWT tokens.

**Kind**: global class  
**Author**: Adam Wegrzynek <adam.wegrzynek@cern.ch>  

* [WebSocket](#WebSocket)
    * [new WebSocket(httpsServer, jwtConfig)](#new_WebSocket_new)
    * [.bind(name, callback)](#WebSocket+bind)
    * [.onmessage(message)](#WebSocket+onmessage) ⇒ <code>object</code>
    * [.jwtVerify(token, refresh)](#WebSocket+jwtVerify) ⇒ <code>object</code>
    * [.onconnection(client, request)](#WebSocket+onconnection)
    * [.onclose(client)](#WebSocket+onclose)
    * [.broadcast(message)](#WebSocket+broadcast)

<a name="new_WebSocket_new"></a>

### new WebSocket(httpsServer, jwtConfig)
Starts up the server and binds event handler.


| Param | Type | Description |
| --- | --- | --- |
| httpsServer | <code>object</code> | HTTPS server |
| jwtConfig | <code>object</code> | configuration of jwt |

<a name="WebSocket+bind"></a>

### webSocket.bind(name, callback)
Binds callback to websocket message (depending on message name)
Message as an Object is passed to the callback

**Kind**: instance method of [<code>WebSocket</code>](#WebSocket)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | websocket message name |
| callback | <code>function</code> | callback function |

<a name="WebSocket+onmessage"></a>

### webSocket.onmessage(message) ⇒ <code>object</code>
Handles incoming text messages: verifies token and processes request/command.

**Kind**: instance method of [<code>WebSocket</code>](#WebSocket)  
**Returns**: <code>object</code> - message to be send back to the user  

| Param | Type |
| --- | --- |
| message | <code>object</code> | 

<a name="WebSocket+jwtVerify"></a>

### webSocket.jwtVerify(token, refresh) ⇒ <code>object</code>
Verifies token, if expired requests a new one.

**Kind**: instance method of [<code>WebSocket</code>](#WebSocket)  
**Returns**: <code>object</code> - includes either parsed token or response message  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| token | <code>object</code> |  | JWT token |
| refresh | <code>bool</code> | <code>true</code> | whether try to refresh token when expired or not |

<a name="WebSocket+onconnection"></a>

### webSocket.onconnection(client, request)
Handles client connection and message receiving.

**Kind**: instance method of [<code>WebSocket</code>](#WebSocket)  

| Param | Type | Description |
| --- | --- | --- |
| client | <code>object</code> | connected client |
| request | <code>object</code> | connection request (new in v3.0.0, client.upgradeReq replacement) |

<a name="WebSocket+onclose"></a>

### webSocket.onclose(client)
Handles client disconnection.

**Kind**: instance method of [<code>WebSocket</code>](#WebSocket)  

| Param | Type | Description |
| --- | --- | --- |
| client | <code>object</code> | disconnected client |

<a name="WebSocket+broadcast"></a>

### webSocket.broadcast(message)
Broadcasts the message to all connected clients.

**Kind**: instance method of [<code>WebSocket</code>](#WebSocket)  

| Param | Type |
| --- | --- |
| message | <code>string</code> | 

<a name="ZeroMQClient"></a>

## ZeroMQClient
ZeroMQ client that communicates with Control Master prcess via one of two supported
socket patterns (sub and req).

**Kind**: global class  
**Author**: Adam Wegrzynek <adam.wegrzynek@cern.ch>  

* [ZeroMQClient](#ZeroMQClient)
    * [new ZeroMQClient(ip, port, type)](#new_ZeroMQClient_new)
    * [.connect(endpoint)](#ZeroMQClient+connect)
    * [.disconnect(endpoint)](#ZeroMQClient+disconnect)
    * [.onmessage(message)](#ZeroMQClient+onmessage)
    * [.send(message)](#ZeroMQClient+send)

<a name="new_ZeroMQClient_new"></a>

### new ZeroMQClient(ip, port, type)
Connects to ZeroMQ socket and binds class methods to ZeroMQ events.


| Param | Type | Description |
| --- | --- | --- |
| ip | <code>string</code> | hostname |
| port | <code>number</code> | port number |
| type | <code>bool</code> | socket type, true = sub. false = req |

<a name="ZeroMQClient+connect"></a>

### zeroMQClient.connect(endpoint)
On-connect event handler.

**Kind**: instance method of [<code>ZeroMQClient</code>](#ZeroMQClient)  

| Param | Type |
| --- | --- |
| endpoint | <code>string</code> | 

<a name="ZeroMQClient+disconnect"></a>

### zeroMQClient.disconnect(endpoint)
On-disconnect event handler.

**Kind**: instance method of [<code>ZeroMQClient</code>](#ZeroMQClient)  

| Param | Type |
| --- | --- |
| endpoint | <code>string</code> | 

<a name="ZeroMQClient+onmessage"></a>

### zeroMQClient.onmessage(message)
On-message event handler.

**Kind**: instance method of [<code>ZeroMQClient</code>](#ZeroMQClient)  

| Param | Type |
| --- | --- |
| message | <code>string</code> | 

<a name="ZeroMQClient+send"></a>

### zeroMQClient.send(message)
Sends message via socket.

**Kind**: instance method of [<code>ZeroMQClient</code>](#ZeroMQClient)  

| Param | Type |
| --- | --- |
| message | <code>string</code> | 

<a name="triggerPushMsg"></a>

## triggerPushMsg(subscription, dataToSend) ⇒ <code>promise</code>
Sends push notifications to subscribed users

**Kind**: global function  
**Returns**: <code>promise</code> - webpush.sendNotification - Sends Notification  

| Param | Type | Description |
| --- | --- | --- |
| subscription | <code>object</code> | Subscription object with user endpoint |
| dataToSend | <code>string</code> | String message to be sent in notification |

<a name="deleteSubscriptionFromDatabase"></a>

## deleteSubscriptionFromDatabase(endpoint) ⇒ <code>promise</code>
Deletes user subscriptions from Database

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| endpoint | <code>string</code> | URL to identify each user |

<a name="getSubscriptions"></a>

## getSubscriptions() ⇒ <code>promise</code>
Fetches subscriptions from Database

**Kind**: global function  
<a name="getAPNSubscriptions"></a>

## getAPNSubscriptions() ⇒ <code>promise</code>
Fetches APN subscriptions from Database

**Kind**: global function  
<a name="formatSubscription"></a>

## formatSubscription(sub) ⇒ <code>object</code>
Formats the subscription to a suitable format to be sent to 'web-push' server

**Kind**: global function  
**Returns**: <code>object</code> - formattedSubscription - Subscription object reformatted  

| Param | Type | Description |
| --- | --- | --- |
| sub | <code>object</code> | Subscription object fetched from Database |

<a name="sendNotif"></a>

## sendNotif() ⇒ <code>promise</code>
Fetches subscriptions from db then verifies them and sends notifications.

**Kind**: global function  
<a name="sendAPNNotif"></a>

## sendAPNNotif() ⇒ <code>promise</code>
Fetches APN subscriptions from db then verifies them and sends notifications.

**Kind**: global function  
<a name="_create"></a>

## _create()
Create widget instance

**Kind**: global function  
<a name="_connect"></a>

## _connect()
Connect to Websocket endpoint and specyfies WebSocket event listeners

**Kind**: global function  
<a name="send"></a>

## send(message)
Send message to WebSocket server

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| message | <code>object</code> | message to be sent |

<a name="triggerPushMsg"></a>

## triggerPushMsg(subscription, dataToSend) ⇒ <code>promise</code>
Sends push notifications to subscribed users

**Kind**: global function  
**Returns**: <code>promise</code> - webpush.sendNotification - Sends Notification  

| Param | Type | Description |
| --- | --- | --- |
| subscription | <code>object</code> | Subscription object with user endpoint |
| dataToSend | <code>string</code> | String message to be sent in notification |

<a name="deleteSubscriptionFromDatabase"></a>

## deleteSubscriptionFromDatabase(endpoint) ⇒ <code>promise</code>
Deletes user subscriptions from Database

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| endpoint | <code>string</code> | URL to identify each user |

<a name="getSubscriptions"></a>

## getSubscriptions() ⇒ <code>promise</code>
Fetches subscriptions from Database

**Kind**: global function  
<a name="getAPNSubscriptions"></a>

## getAPNSubscriptions() ⇒ <code>promise</code>
Fetches APN subscriptions from Database

**Kind**: global function  
<a name="formatSubscription"></a>

## formatSubscription(sub) ⇒ <code>object</code>
Formats the subscription to a suitable format to be sent to 'web-push' server

**Kind**: global function  
**Returns**: <code>object</code> - formattedSubscription - Subscription object reformatted  

| Param | Type | Description |
| --- | --- | --- |
| sub | <code>object</code> | Subscription object fetched from Database |

<a name="sendNotif"></a>

## sendNotif() ⇒ <code>promise</code>
Fetches subscriptions from db then verifies them and sends notifications.

**Kind**: global function  
<a name="sendAPNNotif"></a>

## sendAPNNotif() ⇒ <code>promise</code>
Fetches APN subscriptions from db then verifies them and sends notifications.

**Kind**: global function  
