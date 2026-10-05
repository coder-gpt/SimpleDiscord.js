SimpleDiscord.js

<div align="center">SimpleDiscord.js

A lightweight Discord bot library for Node.js

Simple Discord bots without the complexity.

""npm" (https://img.shields.io/npm/v/simple-discord-bot.js?style=for-the-badge)" (https://www.npmjs.com/package/simple-discord-bot.js)
""npm downloads" (https://img.shields.io/npm/dm/simple-discord-bot.js?style=for-the-badge)" (https://www.npmjs.com/package/simple-discord-bot.js)
""license" (https://img.shields.io/npm/l/simple-discord-bot.js?style=for-the-badge)" (https://github.com/)

</div>---

✨ Features

SimpleDiscord.js is a lightweight Discord bot library designed to make building Discord bots simple.

Core

- Discord Gateway connection
- Discord API support
- Slash commands
- Command options
- Automatic command registration
- Command removal
- Messages
- Message replies
- Message editing
- Message deletion
- Permission checking

Components

- "ActionRowBuilder"
- "ButtonBuilder"
- "SelectMenuBuilder"

Embeds

- Titles
- Descriptions
- Colors
- URLs
- Footers
- Authors
- Thumbnails
- Images
- Timestamps
- Embed fields

Interactions

- Interaction replies
- Deferred replies
- Editing interaction replies
- Deleting interaction replies
- Button interactions
- Select menu interactions

Developer Utilities

- "client.isReady()"
- "client.uptime"
- "client.applicationId"
- "client.user"
- "DiscordAPIError"

---

📦 Installation

npm install simple-discord-bot.js

---

🚀 Quick Start

const {
  Client
} = require("simple-discord-bot.js")

const client = new Client()

const TOKEN = "YOUR_BOT_TOKEN"

client.command(
  "ping",
  async interaction => {
    await interaction.reply("Pong!")
  },
  {
    description: "Replies with Pong!"
  }
)

client.on("ready", () => {
  console.log(
    `Logged in as ${client.user.username}`
  )
})

client.login(TOKEN)

Commands registered with "client.command()" are automatically synchronized with Discord when the bot connects.

---

⚡ Slash Commands

client.command(
  "hello",
  async interaction => {
    await interaction.reply("Hello!")
  },
  {
    description: "Says hello!"
  }
)

---

📝 Command Options

client.command(
  "say",
  async interaction => {
    await interaction.reply(
      interaction.options.message
    )
  },
  {
    description: "Make the bot say something",

    options: [
      {
        type: 3,
        name: "message",
        description: "Message to send",
        required: true
      }
    ]
  }
)

---

🗑️ Command Management

Remove a command from Discord:

await client.removeCommand("hello")

Check whether a command exists:

client.hasCommand("hello")

Get a command:

const command =
  client.getCommand("hello")

---

🎨 Embeds

const {
  EmbedBuilder
} = require("simple-discord-bot.js")

client.command(
  "embed",
  async interaction => {
    const embed =
      new EmbedBuilder()
        .setTitle("Hello!")
        .setDescription(
          "This is an embed."
        )
        .setColor("#5865F2")
        .setTimestamp()

    await interaction.reply(embed)
  }
)

Embed Fields

const embed =
  new EmbedBuilder()
    .setTitle("User Information")
    .addField(
      "Username",
      "SimpleBot",
      true
    )
    .addField(
      "Status",
      "Online",
      true
    )

Multiple fields:

embed.addFields(
  {
    name: "Language",
    value: "JavaScript",
    inline: true
  },
  {
    name: "Library",
    value: "SimpleDiscord.js",
    inline: true
  }
)

---

🔘 Buttons

const {
  ButtonBuilder,
  ActionRowBuilder
} = require("simple-discord-bot.js")

client.command(
  "button",
  async interaction => {
    const button =
      new ButtonBuilder()
        .setCustomId("hello")
        .setLabel("Say Hello")
        .setStyle("primary")

    const row =
      new ActionRowBuilder()
        .addComponents(button)

    await interaction.reply({
      content: "Click the button!",
      components: [row]
    })
  }
)

Handle the button:

client.on(
  "interaction",
  async interaction => {
    if (
      interaction.type === "button" &&
      interaction.customId === "hello"
    ) {
      await interaction.reply("Hello!")
    }
  }
)

---

📋 Select Menus

const {
  SelectMenuBuilder,
  ActionRowBuilder
} = require("simple-discord-bot.js")

const menu =
  new SelectMenuBuilder()
    .setCustomId("color")
    .setPlaceholder(
      "Choose a color"
    )
    .addOptions(
      {
        label: "Red",
        value: "red"
      },
      {
        label: "Blue",
        value: "blue"
      },
      {
        label: "Green",
        value: "green"
      }
    )

const row =
  new ActionRowBuilder()
    .addComponents(menu)

await interaction.reply({
  content: "Choose a color:",
  components: [row]
})

Handle the menu:

client.on(
  "interaction",
  async interaction => {
    if (
      interaction.type === "selectMenu" &&
      interaction.customId === "color"
    ) {
      await interaction.reply(
        `Selected: ${interaction.values.join(", ")}`
      )
    }
  }
)

---

⏳ Deferred Replies

Useful when your bot needs more time before responding.

client.command(
  "loading",
  async interaction => {
    await interaction.deferReply()

    await new Promise(
      resolve =>
        setTimeout(resolve, 3000)
    )

    await interaction.editReply(
      "Finished!"
    )
  }
)

---

✏️ Edit Interaction Replies

await interaction.reply(
  "Original message"
)

await interaction.editReply(
  "Edited message"
)

---

🗑️ Delete Interaction Replies

await interaction.reply(
  "This will disappear."
)

await interaction.deleteReply()

---

🔐 Permissions

Check a member's Discord permissions:

const isAdmin =
  interaction.member.permissions.has(
    "Administrator"
)

if (!isAdmin) {
  await interaction.reply(
    "You need Administrator permission."
  )

  return
}

Other permissions can be checked:

interaction.member.permissions.has(
  "KickMembers"
)

interaction.member.permissions.has(
  "BanMembers"
)

interaction.member.permissions.has(
  "ManageMessages"
)

interaction.member.permissions.has(
  "SendMessages"
)

---

🛠️ Developer Utilities

Check whether the client is ready:

if (client.isReady()) {
  console.log("Bot is ready!")
}

Get uptime:

console.log(client.uptime)

Get the application ID:

console.log(client.applicationId)

Get the logged-in user:

console.log(client.user.username)

---

❌ API Errors

SimpleDiscord.js provides "DiscordAPIError" for Discord API failures.

const {
  DiscordAPIError
} = require("simple-discord-bot.js")

client.on(
  "error",
  error => {
    if (
      error instanceof DiscordAPIError
    ) {
      console.log(
        "Discord API Error"
      )

      console.log(
        "Code:",
        error.code
      )

      console.log(
        "Status:",
        error.status
      )

      console.log(
        "Method:",
        error.method
      )

      console.log(
        "Path:",
        error.path
      )

      console.log(
        "Message:",
        error.message
      )
    }
  }
)

---

💬 Messages

Listen for messages:

client.on(
  "message",
  async message => {
    console.log(
      message.content
    )
  }
)

Reply:

await message.reply(
  "Hello!"
)

Edit:

await message.edit(
  "Edited!"
)

Delete:

await message.delete()

---

🧱 Action Rows

Action rows contain Discord message components such as buttons and select menus.

const row =
  new ActionRowBuilder()
    .addComponents(
      button
    )

Components can also be replaced:

row.setComponents(
  button
)

---

📚 API Overview

Client

Client
├── login()
├── destroy()
├── command()
├── removeCommand()
├── getCommand()
├── hasCommand()
├── isReady()
├── uptime
├── user
└── applicationId

Builders

EmbedBuilder
ButtonBuilder
SelectMenuBuilder
ActionRowBuilder

---

🗺️ Roadmap

0.1.x — Core Foundation

- ✅ Discord Gateway connection
- ✅ Slash commands
- ✅ Command options
- ✅ Messages
- ✅ Message editing
- ✅ Message deletion
- ✅ Permissions
- ✅ Embeds
- ✅ Embed fields
- ✅ Buttons
- ✅ Select menus

0.2.x — More Discord Features

- ✅ Interaction improvements
- ✅ ActionRowBuilder
- ✅ Command management
- ✅ Automatic command registration
- ✅ API errors
- ✅ Developer utilities
- 🔄 Documentation and examples
- ⬜ More Discord API features

0.3.x — Developer Experience

- ⬜ More builder classes
- ⬜ Easier event handling
- ⬜ More developer utilities
- ⬜ Expanded documentation

1.0.0 — Stable Release

- ⬜ Stable API
- ⬜ Expanded Discord feature coverage
- ⬜ Production-ready library
- ⬜ Complete documentation

---

📄 License

MIT

---

<div align="center">Made with ❤️ using JavaScript.

</div>
