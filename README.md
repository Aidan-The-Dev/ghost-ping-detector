# **Getting started**

The first step to initialize the module. You need to pass the normal discord paramaters and then our paramaters.

```js
const discord = require('discord.js')
const client = new discord.Client()

const ghostPing = require('ghost-ping-detector')

client.once('ready', () => {
    console.log('Ready')
    client.user.setActivity('for ghost pings', {type: 'WATCHING'})
})

client.on('messageDelete', async (message) => {
    await ghostPing.detector('messageDelete', message)
})

client.on('messageUpdate', async (oldMessage, newMessage) => {
    await ghostPing.detector('messageUpdate', oldMessage, newMessafe)
})

client.login(token)
```

# **Customisation**
Now that we have the detectors setup and runnings correctly we can start the customisation.

# **Getting started**

## Custom Embed

Replace any of the embed messages with what you want it to say!

```js
ghostPing.detector('messageDelete', message, {
    title: 'New Ghost Ping Detected',
    color: 'RANDOM',
    picture: 'https://i.imgur.com/k6pLhtU.png',
    footer: 'Don\'t ghost ping'
})
```

## Custom Channel

Replace `channelID` with your ghost ping log channel!

```js
ghostPing.detector('messageDelete', message, {
    channel: 'channelID'
})
```

## Custom Ignore Settings

You can even choose what users, permissions, channels, and roles that the bot ignores seperate every ID and permission by a comma!

```js
ghostPing.detector('messageDelete', message, {
    ignore: {
        users: ['userID1', 'userID2'],
        permissions: ['ADMINISTRATOR'],
        channels: ['channelID1', 'channelID2'],
        roles: ['roleID1', 'roleID2']
    }
})
```

## Example of everything put together

```js
ghostPing.detector('messageDelete', message, {
    title: 'New Ghost Ping Detected',
    color: 'RANDOM',
    picture: 'https://i.imgur.com/k6pLhtU.png',
    footer: 'Don\'t ghost ping'm
    channel: message.channel.id,
    ignore: {
        users: [],
        permissions: [],
        channels: [],
        roles: []
    }
})
```
