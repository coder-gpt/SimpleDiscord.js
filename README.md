<div align="center"><img src="assets/file_000000003e4082079abfdbd37db63419.png" width="180" alt="simple-discord-bot.js"><h1>simple-discord-bot.js</h1><p>A simple and lightweight Discord bot library for Node.js</p><p>
  <a href="https://www.npmjs.com/package/simple-discord-bot.js">
    <img src="https://img.shields.io/npm/v/simple-discord-bot.js?style=for-the-badge" alt="npm version">
  </a>
  <a href="https://www.npmjs.com/package/simple-discord-bot.js">
    <img src="https://img.shields.io/npm/dm/simple-discord-bot.js?style=for-the-badge" alt="npm downloads">
  </a>
  <a href="https://github.com/YOUR_USERNAME/simple-discord-bot.js/blob/main/LICENSE">
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
- Simple API
- Discord Gateway support
- Slash commands
- Command options
- EmbedBuilder
- Permission checking
- Message events
- Gateway heartbeat
- Clean shutdown
- npm package support

Installation

npm install simple-discord-bot.js

Quick Start

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

Slash Commands

client.command("hello", interaction => {
  interaction.reply("Hello!")
}, {
  description: "Says hello"
})

Command Options

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

Access options with:

interaction.options.message

Embeds

const { EmbedBuilder } = require("simple-discord-bot.js")

const embed = new EmbedBuilder()
  .setTitle("Hello")
  .setDescription("This is an embed!")
  .setColor("5865F2")
  .setFooter("Made with simple-discord-bot.js")
  .setTimestamp()

interaction.reply(embed)

Embed Methods

.setTitle("Hello")
.setDescription("Description")
.setColor("5865F2")
.setURL("https://example.com")
.setFooter("Footer")
.setAuthor("Author")
.setThumbnail("https://example.com/image.png")
.setImage("https://example.com/image.png")
.setTimestamp()

Permissions

client.command("admin", interaction => {
  if (!interaction.member?.permissions.has("Administrator")) {
    return interaction.reply("You need Administrator")
  }

  interaction.reply("You have Administrator permission!")
}, {
  description: "Administrator only command"
})

Messages

Listen for messages:

client.on("message", message => {
  console.log(message.content)
})

Reply to messages:

message.reply("Hello!")

Events

Event| Description
"ready"| Bot is ready
"message"| A message was created
"error"| Gateway error
"disconnect"| Bot disconnected

Client

Create a client:

const { Client } = require("simple-discord-bot.js")

const client = new Client()

Login:

client.login("YOUR_BOT_TOKEN")

Create a command:

client.command(
  "ping",
  interaction => {
    interaction.reply("Pong!")
  },
  {
    description: "Replies with Pong!"
  }
)

Disconnect:

client.destroy()

Current Version

0.1.2

SimpleDiscord.js is currently in early development.

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
- [ ] Automatic reconnection
- [ ] Gateway resume support
- [ ] More Discord API features

Contributing

Contributions and suggestions are welcome.

Feel free to open an issue or submit a pull request.

License

MIT License

<div align="center">simple-discord-bot.js

</div>
