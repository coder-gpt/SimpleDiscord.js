simple-discord-bot.js

""npm version" (https://img.shields.io/npm/v/simple-discord-bot.js.svg)" (https://www.npmjs.com/package/simple-discord-bot.js)
""npm downloads" (https://img.shields.io/npm/dm/simple-discord-bot.js.svg)" (https://www.npmjs.com/package/simple-discord-bot.js)
""License" (https://img.shields.io/npm/l/simple-discord-bot.js.svg)" (https://www.npmjs.com/package/simple-discord-bot.js)
""Node.js" (https://img.shields.io/badge/Node.js-18%2B-brightgreen.svg)" (https://nodejs.org/)

A simple and lightweight Discord bot library for Node.js

Built to make Discord bot development easier while keeping the API simple and beginner friendly

---

✨ Features

- ⚡ Lightweight
- 🧩 Simple API
- 🤖 Discord bot support
- 💬 Message events
- ⚙️ Slash commands
- 📝 Slash command options
- 🎨 EmbedBuilder
- 🔐 Permission checking
- 💓 Gateway heartbeat
- 🛑 Clean bot shutdown
- 📦 Available through npm
- 🟢 Easy to learn

---

📦 Installation

Install the latest version with npm

npm install simple-discord-bot.js

---

🚀 Quick Start

Create a simple bot in just a few lines

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

Start your bot

node index.js

---

⚙️ Slash Commands

Create commands with "client.command()"

client.command("hello", interaction => {
  interaction.reply("Hello!")
}, {
  description: "Says hello"
})

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

The option can then be accessed with

interaction.options.message

---

🎨 Embeds

Create beautiful Discord embeds with "EmbedBuilder"

const { EmbedBuilder } = require("simple-discord-bot.js")

const embed = new EmbedBuilder()
  .setTitle("Hello")
  .setDescription("This is an embed!")
  .setColor("5865F2")
  .setFooter("Made with SimpleDiscord.js")
  .setTimestamp()

interaction.reply(embed)

Embed Methods

Title

.setTitle("Hello")

Description

.setDescription("This is my description")

Color

Hex colors are supported

.setColor("FF0000")

URL

.setURL("https://example.com")

Footer

.setFooter("Made with SimpleDiscord.js")

Footer Icon

.setFooter(
  "Made with SimpleDiscord.js",
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

---

💬 Messages

Listen for messages

client.on("message", message => {
  console.log(message.content)
})

Reply to messages

message.reply("Hello!")

---

📡 Events

SimpleDiscord.js currently supports:

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

🛠️ API

Client

const { Client } = require("simple-discord-bot.js")

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

📊 Current Status

SimpleDiscord.js is currently in early development

Current version:

0.1.2

The API may change as the library develops

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

📚 Why SimpleDiscord.js?

Discord libraries can become complicated when you're just starting

SimpleDiscord.js focuses on keeping things straightforward

Instead of learning a huge API you can start with:

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

📦 npm

Install the package from npm

npm install simple-discord-bot.js

---

🤝 Contributing

Contributions and suggestions are welcome

If you find a bug or have an idea for a feature you can open an issue or submit a pull request

---

📄 License

MIT License

---

Made with ❤️ and JavaScript

simple-discord-bot.js
