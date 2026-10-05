<div align="center"><img src="assets/file_000000003e4082079abfdbd37db63419.png" width="180" alt="simple-discord-bot.js logo">simple-discord-bot.js

A simple and lightweight Discord bot library for Node.js

""npm version" (https://img.shields.io/npm/v/simple-discord-bot.js?style=for-the-badge)" (https://www.npmjs.com/package/simple-discord-bot.js)
""npm downloads" (https://img.shields.io/npm/dm/simple-discord-bot.js?style=for-the-badge)" (https://www.npmjs.com/package/simple-discord-bot.js)
""license" (https://img.shields.io/npm/l/simple-discord-bot.js?style=for-the-badge)" (https://github.com/YOUR_USERNAME/simple-discord-bot.js/blob/main/LICENSE)
""Node.js" (https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=node.js&logoColor=white)" (https://nodejs.org/)

Simple • Lightweight • Beginner Friendly

</div>---

🚀 Features

- ⚡ Lightweight Discord bot library
- 🧩 Simple beginner friendly API
- 🤖 Discord Gateway support
- ⚙️ Slash commands
- 📝 Slash command options
- 🎨 EmbedBuilder
- 🔐 Permission checking
- 💬 Message events
- 💓 Gateway heartbeat
- 🛑 Clean shutdown
- 📦 Available through npm

---

📦 Installation

Install the package using npm

npm install simple-discord-bot.js

---

🚀 Quick Start

Create your first bot

const {
  Client
} = require("simple-discord-bot.js")

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

Start your bot

node index.js

---

⚙️ Slash Commands

Creating a slash command is simple

client.command("hello", interaction => {
  interaction.reply("Hello!")
}, {
  description: "Says hello"
})

Commands are automatically stored by the client and can be registered with Discord

await client.api.registerCommands(
  client.user.id,
  [...client.commands.values()].map(command => command.command)
)

---

🧩 Command Options

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

Access the option using

interaction.options.message

---

🎨 Embeds

Create Discord embeds using "EmbedBuilder"

const {
  EmbedBuilder
} = require("simple-discord-bot.js")

const embed = new EmbedBuilder()
  .setTitle("Hello")
  .setDescription("This is an embed!")
  .setColor("5865F2")
  .setTimestamp()

interaction.reply(embed)

Embed Methods

Title

.setTitle("Hello")

Description

.setDescription("This is my description")

Color

.setColor("5865F2")

Hex colors are supported

.setColor("FF0000")

URL

.setURL("https://example.com")

Footer

.setFooter("Made with simple-discord-bot.js")

Footer Icon

.setFooter(
  "Made with simple-discord-bot.js",
  "https://example.com/icon.png"
)

Author

.setAuthor("SimpleBot")

Author Icon

.setAuthor(
  "SimpleBot",
  "https://example.com/icon.png"
)

Thumbnail

.setThumbnail("https://example.com/image.png")

Image

.setImage("https://example.com/image.png")

Timestamp

.setTimestamp()

---

🔐 Permissions

Check Discord permissions easily

client.command("admin", interaction => {
  if (!interaction.member?.permissions.has("Administrator")) {
    return interaction.reply("You need Administrator")
  }

  interaction.reply("You have Administrator permission!")
}, {
  description: "Administrator only command"
})

Supported permission checking includes Discord permission flags such as

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

💬 Messages

Listen for messages

client.on("message", message => {
  console.log(message.content)
})

Reply to a message

message.reply("Hello!")

---

📡 Events

SimpleDiscord.js currently supports

Event| Description
"ready"| Bot is ready
"message"| A message was created
"error"| Gateway error
"disconnect"| Bot disconnected

Example

client.on("ready", () => {
  console.log("Bot is online!")
})

---

🤖 Client

Create a client

const {
  Client
} = require("simple-discord-bot.js")

const client = new Client()

"client.login(token)"

Connect your bot to Discord

client.login("YOUR_BOT_TOKEN")

"client.command(name, handler, options)"

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

"client.destroy()"

Disconnect the bot

client.destroy()

---

📡 API

The library includes a simple Discord API wrapper

client.api

Register slash commands

await client.api.registerCommands(
  client.user.id,
  commands
)

---

🛑 Clean Shutdown

SimpleDiscord.js handles "Ctrl + C" automatically

Stopping bot...

The gateway connection is closed cleanly before the process exits

---

📊 Current Version

0.1.2

SimpleDiscord.js is currently in early development

The API may change as new features are added

---

🗺️ Roadmap

✅ Completed

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

🚧 Planned

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

📚 Why simple-discord-bot.js?

Discord bot libraries can become complicated when you're just starting

simple-discord-bot.js focuses on keeping Discord bot development simple

const {
  Client
} = require("simple-discord-bot.js")

const client = new Client()

client.command("ping", interaction => {
  interaction.reply("Pong!")
})

client.login("YOUR_BOT_TOKEN")

Simple

Lightweight

Beginner Friendly

---

📦 npm

Install the latest version

npm install simple-discord-bot.js

View the package on npm

""npm" (https://img.shields.io/badge/npm-simple--discord--bot.js-red?style=for-the-badge&logo=npm)" (https://www.npmjs.com/package/simple-discord-bot.js)

---

🤝 Contributing

Contributions and suggestions are welcome

If you find a bug or have an idea for a feature you can open an issue or submit a pull request

---

📄 License

This project is licensed under the MIT License

---

<div align="center">simple-discord-bot.js

A simple Discord bot library for Node.js

</div>
