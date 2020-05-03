# Matrix App

The ixo configuration page for an app serves as a light client for initiating a connection with the third-party application, to obtain credentials and perform initial configuration of the app.  
After this, the user interaction is handed over to the official app client, where they continue to manage further configurations and admin functions.

### Connecting the client-server API

The user must register an account on the Matrix server at comms.ixo.world. If they already have an account, they must login into their account. \[For the MVP, we will use the standard username/password method. However, this will become burdensome for users who must set up multiple accounts for different entities. It also represents a security vulnerability. In future, authentication with the ixo.world Matrix server will use DID-Auth. The user will simply sign a message with their ixo Keysafe or ixo-Mobile wallet.\]

The ixo-webclient will post a Registration API call in the format:  
`curl` -XPOST -d '{"username":"example", "password":"wordpass", "auth": {"type":"m.login.dummy"}}' "[https://comms.ixo.world:8448/\_matrix/client/r0/register"\`](https://comms.ixo.world:8448/_matrix/client/r0/register%22%60)  
This should return:  
`{ "access_token": "QGV4YW1wbGU6bG9jYWxob3N0.AqdSzFmFYrLrTmteXc", "home_server": "ixo.world", "user_id": "@example:ixo.world" }`

After successful registration, the login call is:  
\`curl -XGET "[https://comms.ixo.world:8448/\_matrix/client/r0/login](https://comms.ixo.world:8448/_matrix/client/r0/login)"

{  
"flows": \[  
{  
"type": "m.login.password"  
}  
\]  
}

curl -XPOST -d '{"type":"m.login.password", "user":"example", "password":"wordpass"}' "[https://comms.ixo.world:8448/\_matrix/client/r0/login](https://comms.ixo.world:8448/_matrix/client/r0/login)"

{  
"access\_token": "QGV4YW1wbGU6bG9jYWxob3N0.vRDLTgxefmKWQEtgGd",  
"home\_server": "ixo.world",  
"user\_id": "[@example](https://github.com/example):ixo.world"  
}\`

This provides an access token for the user that will persist for all future communications. This should ideally be stored in the Cell Node \[See how\].

Now the user can start sending messages to the server that will create rooms and configure the room settings.

Matrix has the concept of a State message type that establishes the settings for a room, or changes these settings when the state is updated. We will collect the core set of room settings, such as the Topic of the room, using the ixo-webclient UI, to parse these messages.

An Entity may have several rooms, however the app in Control Panel will always bring the user to a default public or private room, depending on whether they are an authorised agent associated with the entity.

The admin should have a checkbox option to select whether to include both a public and/or private room.

To set up the public room we will use the DID of the current ixo entity as an alias, which will bind the room to this DID, in the format did.ixo.sdpfnsdgw09tobwjsdfjkdsfnkteer/public:

\`curl -XPOST -d '{"room\_alias\_name":"/public"}' "[https://comms.ixo.world:8448/\_matrix/client/r0/createRoom?access\_token=YOUR\_ACCESS\_TOKEN](https://comms.ixo.world:8448/_matrix/client/r0/createRoom?access_token=YOUR_ACCESS_TOKEN)"

{  
"room\_alias": "\#/public:ixo.world",  
"room\_id": "!asfLdzLnOdGRkdPZWu:localhost"  
}\`

The "room\_id" is a random identifier generated by the Matrix server.

Now, if the admin has selected to create a private room, we will automatically do this in a similar way with:  
`curl -XPOST -d '{"room_alias_name":"<DID>/private"}' **"https://comms.ixo.world:8448/_matrix/client/r0/createRoom?access_token=YOUR_ACCESS_TOKEN"`

To restrict this room so that only authorised agents can join the room by invitation, the following additional API messages are sent:

> > need to add the room setting message to be invite only

### States of the deployed app

There are 5 states of the deployed app, which is visible in the control panel for the relevant contexts:

* User is not signed in or not an authorised agent. "app\_state":"public"
* User is signed in as an authorised agent. "app\_state":"private"
* User is already a member of the public room \(holding an access token\). "app\_state":"public\_member"
* User is already a member of the private room \(holding an access token\). "app\_state":"private\_member"
* User is signed in as the entity controller. "app\_state":"admin" // this state can be ignored for MVP

The corresponding endpoints for each of these states are:

* "app\_state":"public": `curl -XPOST -d '{}' "https://comms.ixo.world:8448/_matrix/client/r0/join/%<DID>/public:comms.ixo.world?access_token=YOUR_ACCESS_TOKEN"` where the access token comes from the user having signed into Matrix via a modal.
* "app\_state":"private": \`curl -XPOST -d '{"user\_id":"@&lt;DID\(admin\)&gt;:comms.ixo.world"}' "[https://app.ixo.world:8448/\_matrix/client/r0/rooms/%](https://app.ixo.world:8448/_matrix/client/r0/rooms/%)&lt;DID\(entity\)/private&gt;:comms.ixo.world/invite?access\_token=YOUR\_ACCESS\_TOKEN"
* "app\_state":"public\_member": `https://riot.im/app/#/room/#<did>public:comms.ixo.world`
* "app\_state":"private\_member": `https://riot.im/app/#/room/#<did>private:comms.ixo.world`

### Dev resources

Matrix Client-Server API documentation [https://matrix.org/docs/guides/client-server-api](https://matrix.org/docs/guides/client-server-api)  
Demo app [https://jsfiddle.net/gh/get/jquery/1.8.3/matrix-org/matrix.org/tree/master/jekyll/\_posts/howtos/jsfiddles/example\_app](https://jsfiddle.net/gh/get/jquery/1.8.3/matrix-org/matrix.org/tree/master/jekyll/_posts/howtos/jsfiddles/example_app)
