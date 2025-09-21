---

Create A Discord Bot

A beginner-friendly guide and template for creating a simple Discord bot using Discord.js v14.


---

Table of Contents

- Introduction

- Prerequisites

- Project Setup

- Creating Your Discord Bot

- Bot Code

- Running Your Bot

- Adding Commands

- Project Structure

- Next Steps

- Resources



---

Introduction

This repository contains a simple Discord bot template built with Discord.js. It includes a basic command system and is easy to expand with more features.


---

Prerequisites

Node.js v18+ installed

A Discord account

A Discord server to test your bot

Basic knowledge of JavaScript



---

Project Setup

1. Clone the repository (or create your own folder)



git clone https://github.com/your-username/my-discord-bot.git
cd my-discord-bot

2. Initialize a Node.js project



npm init -y

3. Install dependencies



npm install discord.js dotenv

4. Create environment file .env



TOKEN=YOUR_BOT_TOKEN_HERE

PREFIX=!


---

Creating Your Discord Bot

1. Go to the Discord Developer Portal.


2. Click New Application, name it, then Create.


3. Go to the Bot tab → Add Bot → Yes, do it!


4. Copy the bot token and add it to your .env file.


5. Go to OAuth2 > URL Generator → select bot scope → Administrator permissions → copy the generated link.


6. Invite your bot to your server using the link.




---

Bot Code

Create index.js:

```require('dotenv').config();
const { Client, GatewayIntentBits } = require('discord.js');

const client = new Client({
    intents: [GatewayIntentBits.Guilds, GatewayIntentBits.GuildMessages, GatewayIntentBits.MessageContent],
});

const PREFIX = process.env.PREFIX || '!';

client.on('ready', () => {
    console.log(`Logged in as ${client.user.tag}`);
});

client.on('messageCreate', (message) => {
    if (message.author.bot) return;
    if (!message.content.startsWith(PREFIX)) return;

    const [command, ...args] = message.content.trim().substring(PREFIX.length).split(/\s+/);

    if (command === 'ping') {
        message.reply('Pong!');
    } else if (command === 'hello') {
        message.reply(`Hello, ${message.author.username}!`);
    }
});

client.login(process.env.TOKEN);```


---

Running Your Bot

1. Run your bot locally:



node index.js

2. Check your Discord server → your bot should be online.


3. Test commands:



!ping
!hello


---

Adding Commands

To expand your bot, create a commands folder and modularize commands:

my-discord-bot/
├── commands/
│   └── ping.js
├── index.js
└── .env

Example ping.js:

module.exports = {
    name: 'ping',
    description: 'Replies with Pong!',
    execute(message) {
        message.reply('Pong!');
    },
};

Then dynamically load commands in index.js.


---

Project Structure

my-discord-bot/
├── node_modules/
├── commands/
├── .env
├── index.js
├── package.json
└── README.md


---

Next Steps

Add slash commands

Add a help command

Add database support (MongoDB, SQLite)

Add more modules (moderation, fun commands, etc.)



---

Resources

Discord.js Guide

Discord Developer Portal

Node.js Documentation



---

If you want, I can also create the full repository template with all folders and starter files ready to upload to GitHub, so you can just push it and start coding.

Do you want me to do that?

