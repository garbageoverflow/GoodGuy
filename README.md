<center>

# GoodGuy

</center>

> GoodGuy is a discord bot that deletes messages that contain bad words and also alerts the user.

<a href="https://discord.com/api/oauth2/authorize?client_id=707139128663212045&permissions=0&scope=bot">

![invite](https://img.shields.io/badge/Invite-Discord-blueviolet)

</a>

# Do it yourself
It's not hard, if you already have some basic knowledge about [discord.js](discord.js.org).

##### Install Discord.js
I am using npm so here is the code
```
npm install discord.js
```
##### Getting started
Like in any other discord app you have some necessary code to get it up and runnings
```javascript
const Discord = require('discord.js');
const client = new Discord.Client();
const {token} = require('./config.json')

client.once('ready', () => {
	console.log('Ready!');
});

client.on('message', message => {
  // here goes the code
})

client.login(`${token}`);
```
##### The `config.json` file
The config file is where you keep necessary info for the bot.
```json
{
  "token": "your-token-goes-here"
}
```

##### Detecting bad words
First we create a `constant` where we store all the bad words, you can also put every all the bad words in a `json` file and then require it by using `require('./badwords.json')`
```javascript
for (var i = 0; i < words.length; i++) {
  if (message.content.includes(words[i])) {
    message.delete();
    message.author.send(embed);
  }
}
```

Now, your code should look something like this:
```javascript
const Discord = require('discord.js');
const client = new Discord.Client();
const {token} = require('./config.json')

var words = [] //here go all the bad words, you find them in another file

client.once('ready', () => {
	console.log('Ready!');
});

client.on('message', message => {
	for (var i = 0; i < words.length; i++) {
		if (message.content.includes(words[i])) {
			message.delete();
			message.author.send(embed);
		}
	}
});

client.login(`${token}`);
```
##### Alerting the user
You must explain why he's message was deleted, so let's make an [embed](discordjs.guide/popular-topics/embeds.html).\n
You can't customize the embed as you want.

```javascript
var embed = new Discord.MessageEmbed()
	.setTitle('Hey,')
	.setThumbnail('https://github.com/garbageoverflow/GoodGuy/icon.png')
	.setDescription('If you wonder why your message was deleted,\n this bot deletes all messages that have inapropriat/bad words.')
	.setFooter('GoodGuy')
```

#### Congrats you made a simple bot that will make your discord server a friendlier place.

<center>

![froggy](https://media1.tenor.com/images/36b8bdc5eb3d572d9bdfb7c36fd7df1c/tenor.gif)

</center>
