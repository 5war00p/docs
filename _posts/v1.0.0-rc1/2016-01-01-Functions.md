---
layout: post
title: "Functions"
date: 2016-01-01 00:00:00 -0400
categories: v1.0.0-rc1
---
# Functions

## Contents

- [client.getChannels()](#clientgetchannels) - Get the current channels.
- [client.getOptions()](#clientgetoptions) - Get the current options.
- [client.getUsername()](#clientgetusername) - Get the current username.
- [client.isMod()](#clientismod) - Is a mod on a channel.
- [client.readyState()](#clientreadystate) - Get the current state of the socket.

## client.getChannels()

Get the current channels. (_Array_)

~~~ javascript
console.log(client.getChannels());
~~~

## client.getOptions()

Get the current options. (_Object_)

~~~ javascript
console.log(client.getOptions());
~~~

## client.getUsername()

Get the current username. (_String_)

~~~ javascript
console.log(client.getUsername());
~~~

## client.isMod()

**NOT RECOMMENDED**

Function to check if user is a mod on a channel. (_Boolean_)

**Important**: Might not be accurate.

**Parameters:**

- ``channel``: _String_ - Channel name
- ``username``: _String_ - Username

~~~ javascript
if (client.isMod("#schmoopiie", "bob")) {
    // Do something..
}
~~~

**RECOMMENDED**

Everytime you receive a message on Twitch, you receive the user data which contain the user-type.
Read more about user-type on the [Twitch API documentation](https://github.com/justintv/Twitch-API/blob/master/IRC.md#privmsg).

~~~ javascript
client.on("chat", function (channel, user, message, self) {
    // Username is a mod or username is the broadcaster..
    if (user["user-type"] === "mod" || user.username === channel.replace("#", "")) {
        // User is a mod.
    }
});
~~~

## client.readyState()

Get the current state of the socket. (_String_)

~~~ javascript
// Returns one of the following states: "CONNECTING", "OPEN", "CLOSING" or "CLOSED".
console.log(client.readyState());
~~~
