<div align="center"><img src="assets/file_000000003e4082079abfdbd37db63419.png" width="180" alt="simple-discord-bot.js"><h1>simple-discord-bot.js</h1><p>A simple and lightweight Discord bot library for Node.js</p><p>
  <a href="https://www.npmjs.com/package/simple-discord-bot.js">
    <img src="https://img.shields.io/npm/v/simple-discord-bot.js?style=for-the-badge" alt="npm version">
  </a>
  <a href="https://www.npmjs.com/package/simple-discord-bot.js">
    <img src="https://img.shields.io/npm/dm/simple-discord-bot.js?style=for-the-badge" alt="npm downloads">
  </a>
  <a href="https://img.shields.io/npm/l/simple-discord-bot.js">
    <img src="https://img.shields.io/npm/l/simple-discord-bot.js?style=for-the-badge" alt="license">
  </a>
  <img src="https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js">
</p><p>
  <strong>Simple</strong> ·
  <strong>Lightweight</strong> ·
  <strong>Beginner Friendly</strong>
</p></div>---

Features

- Lightweight Discord bot library
- Simple and beginner friendly API
- Discord Gateway support
- Slash commands
- Slash command options
- EmbedBuilder
- Permission checking
- Message events
- Gateway heartbeat
- Clean shutdown
- Available through npm

---

Installation

Install the package with npm

npm install simple-discord-bot.js

---

Quick Start

Create a simple Discord bot

const { Client } = require("simple-discord-bot.js")

const client = new Client()

client.command("ping", interaction => {
  interaction.reply("Pong!")
}, {
  description: "Replies with Pong!"
})

client.on("ready", () => {
  console.log("Bot is online!")
})

client.login("YOUR_BOT_TOKEN")

Start your bot with

node index.js

---

Slash Commands

Create slash commands with "client.command()"

client.command("hello", interaction => {
  interaction.reply("Hello!")
}, {
  description: "Says hello"
})

---

Command Options

Commands can have options

client.command("say", interaction => {
  interaction.reply(interaction.options.message)
}, {
  description: "Make the bot say something",
  options: [
    {
      name: "message",
      description: "The message to send",
      type: 3,
      required: true
    }
  ]
})

Access an option with

interaction.options.message

---

Embeds

Create embeds with "EmbedBuilder"

const { EmbedBuilder } = require("simple-discord-bot.js")

const embed = new EmbedBuilder()
  .setTitle("Hello")
  .setDescription("This is an embed!")
  .setColor("5865F2")
  .setFooter("Made with simple-discord-bot.js")
  .setTimestamp()

interaction.reply(embed)

Embed Methods

Title

embed.setTitle("Hello")

Description

embed.setDescription("This is my description")

Color

embed.setColor("5865F2")

Hex colors are supported

embed.setColor("FF0000")

URL

embed.setURL("https://example.com")

Footer

embed.setFooter("Made with simple-discord-bot.js")

Footer Icon

embed.setFooter(
  "Made with simple-discord-bot.js",
  "https://example.com/icon.png"
)

Author

embed.setAuthor("SimpleBot")

Author Icon

embed.setAuthor(
  "SimpleBot",
  "https://example.com/icon.png"
)

Thumbnail

embed.setThumbnail(
  "https://example.com/image.png"
)

Image

embed.setImage(
  "https://example.com/image.png"
)

Timestamp

embed.setTimestamp()

---

Permissions

Check Discord permissions with "interaction.member.permissions"

client.command("admin", interaction => {
  if (!interaction.member?.permissions.has("Administrator")) {
    return interaction.reply("You need Administrator")
  }

  interaction.reply("You have Administrator permission!")
}, {
  description: "Administrator only command"
})

Example supported permissions include

Administrator
ManageGuild
ManageChannels
ManageMessages
SendMessages
KickMembers
BanMembers
ManageRoles
ManageWebhooks
ViewChannel
ReadMessageHistory

---

Messages

Listen for messages

client.on("message", message => {
  console.log(message.content)
})

Reply to messages

message.reply("Hello!")

---

Events

Event| Description
"ready"| Bot is ready
"message"| A message was created
"error"| A gateway error occurred
"disconnect"| Bot disconnected

Example

client.on("ready", () => {
  console.log("Bot is online!")
})

---

Client

Create a client

const { Client } = require("simple-discord-bot.js")

const client = new Client()

Login

Connect your bot to Discord

client.login("YOUR_BOT_TOKEN")

Commands

Create a slash command

client.command(
  "ping",
  interaction => {
    interaction.reply("Pong!")
  },
  {
    description: "Replies with Pong!"
  }
)

Destroy

Disconnect the bot

client.destroy()

---

API

Access the Discord API wrapper through "client.api"

client.api

Register slash commands

await client.api.registerCommands(
  client.user.id,
  commands
)

---

Clean Shutdown

SimpleDiscord.js handles "Ctrl + C" automatically

Stopping bot...

The gateway connection is closed cleanly before the process exits.

---

SimpleDiscord.js is currently in early development.

The API may change as the library continues to develop.

---

Roadmap

Completed

- [x] Discord Gateway connection
- [x] Gateway heartbeat
- [x] Bot login
- [x] Clean shutdown
- [x] Ready event
- [x] Message events
- [x] Message replies
- [x] Slash commands
- [x] Slash command options
- [x] Permission checking
- [x] EmbedBuilder
- [x] npm publishing

Planned

- [ ] Embed fields
- [ ] Buttons
- [ ] Select menus
- [ ] More interaction types
- [ ] Channel objects
- [ ] Guild objects
- [ ] User objects
- [ ] Message editing
- [ ] Message deletion
- [ ] More permission helpers
- [ ] Better error handling
- [ ] Automatic reconnection
- [ ] Gateway resume support
- [ ] More Discord API features

---

Why simple-discord-bot.js?

Discord bot development can become complicated when you're just starting.

simple-discord-bot.js focuses on keeping the API simple and easy to understand.

A basic bot can be created with just a few lines

const { Client } = require("simple-discord-bot.js")

const client = new Client()

client.command("ping", interaction => {
  interaction.reply("Pong!")
})

client.login("YOUR_BOT_TOKEN")

Simple

Lightweight

Beginner friendly

---

npm

Install the latest version

npm install simple-discord-bot.js

<a href="https://www.npmjs.com/package/simple-discord-bot.js">
  <img src="https://img.shields.io/badge/npm-simple--discord--bot.js-red?style=for-the-badge&logo=npm" alt="npm">
</a>---

Contributing

Contributions and suggestions are welcome.

If you find a bug or have an idea for a feature, open an issue or submit a pull request.

---

License

MIT License

---

<div align="center"><img src="assets/file_000000003e4082079abfdbd37db63419.png" width="80" alt="simple-discord-bot.js"><strong>simple-discord-bot.js</strong>

<p>A simple Discord bot library for Node.js</p></div>
