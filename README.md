SimpleDiscord.js

<div align="center">SimpleDiscord.js

A lightweight, developer-friendly Discord bot library for Node.js

Build Discord bots with a simple API, powerful builders, and minimal setup.

""npm" (https://img.shields.io/npm/v/simple-discord-bot.js?style=for-the-badge)" (https://www.npmjs.com/package/simple-discord-bot.js)
""npm downloads" (https://img.shields.io/npm/dm/simple-discord-bot.js?style=for-the-badge)" (https://www.npmjs.com/package/simple-discord-bot.js)
""license" (https://img.shields.io/npm/l/simple-discord-bot.js?style=for-the-badge)" (https://github.com/Frost-Dominus/SimpleDiscord.js/blob/main/LICENSE)
""Node.js" (https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=node.js&logoColor=white)" (https://nodejs.org/)

</div>---

📖 About

SimpleDiscord.js is a lightweight Discord bot library for Node.js.

It is designed to make Discord bot development easier without requiring a huge framework or complicated abstractions.

SimpleDiscord.js provides:

- A simple client API
- Automatic slash-command registration
- Discord Gateway connectivity
- Message handling
- Interaction handling
- Embeds
- Buttons
- Select menus
- Action rows
- Permission checking
- Developer utilities
- Structured Discord API errors

«SimpleDiscord.js is focused on keeping Discord bot development simple while still providing useful features for real projects.»

---

✨ Features

🤖 Bot Core

- Discord Gateway connection
- Discord REST API support
- Automatic authentication
- Automatic slash-command synchronization
- Command management
- Clean shutdown handling
- Ready/disconnect events

💬 Messages

- Receive messages
- Reply to messages
- Edit messages
- Delete messages
- Access message author information
- Access channel and guild information

⚡ Slash Commands

- Slash commands
- Command descriptions
- Command options
- Automatic registration
- Command removal
- Command lookup
- Command existence checking

🎨 Embeds

- Titles
- Descriptions
- Colors
- URLs
- Authors
- Footers
- Images
- Thumbnails
- Timestamps
- Fields
- Multiple fields

🧩 Components

- Buttons
- Select menus
- Action rows
- Component interactions
- Custom IDs
- Button styles
- Disabled components
- Select menu options

🔄 Interactions

- Interaction replies
- Deferred replies
- Edit replies
- Delete replies
- Interaction state tracking
- Button interactions
- Select menu interactions

🔐 Permissions

- Discord permission flags
- Permission checking
- Administrator handling
- BigInt-based permission values

🛠️ Developer Utilities

- "client.isReady()"
- "client.uptime"
- "client.user"
- "client.applicationId"
- "DiscordAPIError"

---

📦 Installation

Make sure you have Node.js installed.

npm install simple-discord-bot.js

Create your project:

mkdir my-discord-bot
cd my-discord-bot
npm init -y
npm install simple-discord-bot.js

Create:

my-discord-bot/
├── index.js
└── package.json

---

🤖 Creating Your Discord Bot

Before writing your bot code, you need to create a Discord application.

1. Open the Discord Developer Portal

Go to:

https://discord.com/developers/applications

Sign in with your Discord account.

---

2. Create an Application

Click:

New Application

Give your application a name.

For example:

SimpleBot

Then click Create.

---

3. Create the Bot

Open your application and select:

Bot

Then click:

Add Bot

Confirm the creation.

---

4. Get Your Bot Token

Inside the Bot page, find the token section.

Copy your bot token.

⚠️ Keep your token private

Never upload your token to:

- GitHub
- npm
- Discord
- Screenshots
- Public code
- Public paste sites

If your token becomes public, regenerate it immediately from the Discord Developer Portal.

In your code:

const TOKEN = "YOUR_BOT_TOKEN"

Replace "YOUR_BOT_TOKEN" with your actual token.

---

🔑 Enable Required Intents

SimpleDiscord.js uses Discord Gateway intents.

For message-based functionality, enable the required privileged intents in:

Developer Portal → Your Application → Bot → Privileged Gateway Intents

Depending on what your bot needs, you may need:

- Message Content Intent
- Server Members Intent
- Presence Intent

Only enable the intents your bot actually needs.

---

➕ Invite Your Bot

Go to:

Developer Portal → Your Application → Installation

Configure the installation options for your bot.

For a traditional bot installation, make sure your bot has the permissions required by your application.

Common permissions include:

- View Channels
- Send Messages
- Read Message History
- Embed Links
- Use Application Commands

Then use the generated installation/invite link to add the bot to your server.

---

🚀 Your First Bot

Create "index.js":

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

Start it:

node index.js

You should see:

Gateway connected
Logged in as SimpleBot

Now use:

/ping

Your bot should respond:

Pong!

---

⚡ Automatic Command Registration

One of the main features of SimpleDiscord.js is automatic slash-command synchronization.

You do not need to create a separate command array.

Simply define your commands:

client.command(
  "hello",
  async interaction => {
    await interaction.reply("Hello!")
  },
  {
    description: "Says hello!"
  }
)

SimpleDiscord.js automatically synchronizes your registered commands with Discord when the client becomes ready.

Before

You would need something like:

const commands = [
  {
    name: "hello",
    description: "Says hello!"
  }
]

await client.api.registerCommands(
  client.user.id,
  commands
)

With SimpleDiscord.js

Just:

client.command(
  "hello",
  async interaction => {
    await interaction.reply("Hello!")
  },
  {
    description: "Says hello!"
  }
)

Less code. Less maintenance.

---

⚡ Slash Commands

Create a command:

client.command(
  "hello",
  async interaction => {
    await interaction.reply(
      "Hello from SimpleDiscord.js!"
    )
  },
  {
    description: "Says hello!"
  }
)

---

📝 Command Options

Commands can define Discord options:

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

The user can then use:

/say message:Hello

---

🗑️ Command Management

Remove a command:

await client.removeCommand("hello")

This removes the command from the local command collection and Discord.

Check whether a command exists:

if (client.hasCommand("hello")) {
  console.log("Command exists!")
}

Get a command:

const command =
  client.getCommand("hello")

---

🎨 Embeds

Create an embed:

const {
  EmbedBuilder
} = require("simple-discord-bot.js")

client.command(
  "embed",
  async interaction => {
    const embed =
      new EmbedBuilder()
        .setTitle("SimpleDiscord.js")
        .setDescription(
          "This is an embed!"
        )
        .setColor("#5865F2")
        .setTimestamp()

    await interaction.reply(embed)
  },
  {
    description: "Send an embed"
  }
)

---

📋 Embed Fields

const embed =
  new EmbedBuilder()
    .setTitle("Bot Information")
    .addField(
      "Library",
      "SimpleDiscord.js",
      true
    )
    .addField(
      "Version",
      "0.2.0",
      true
    )
    .addField(
      "Status",
      "Online",
      true
    )

Add multiple fields:

embed.addFields(
  {
    name: "Language",
    value: "JavaScript",
    inline: true
  },
  {
    name: "Runtime",
    value: "Node.js",
    inline: true
  }
)

---

🔘 Buttons

Create a button:

const {
  ButtonBuilder,
  ActionRowBuilder
} = require("simple-discord-bot.js")

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

Handle the interaction:

client.on(
  "interaction",
  async interaction => {
    if (
      interaction.type === "button" &&
      interaction.customId === "hello"
    ) {
      await interaction.reply(
        "Hello from the button!"
      )
    }
  }
)

Button Styles

SimpleDiscord.js supports:

primary
secondary
success
danger
link

---

📋 Select Menus

Create a select menu:

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
        value: "red",
        description: "Choose red"
      },
      {
        label: "Blue",
        value: "blue",
        description: "Choose blue"
      },
      {
        label: "Green",
        value: "green",
        description: "Choose green"
      }
    )

const row =
  new ActionRowBuilder()
    .addComponents(menu)

await interaction.reply({
  content: "Choose a color:",
  components: [row]
})

Handle the selection:

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

🧱 Action Rows

Action rows organize Discord components.

const row =
  new ActionRowBuilder()
    .addComponents(
      button
    )

Replace all components:

row.setComponents(
  button
)

---

⏳ Deferred Replies

Use a deferred reply when your bot needs time to perform work.

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
  },
  {
    description: "Test a deferred reply"
  }
)

---

✏️ Edit Replies

await interaction.reply(
  "Original response"
)

await interaction.editReply(
  "Updated response"
)

---

🗑️ Delete Replies

await interaction.reply(
  "This message will be deleted."
)

await interaction.deleteReply()

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
  "Edited message!"
)

Delete:

await message.delete()

---

🔐 Permissions

SimpleDiscord.js provides Discord permission checking through "Permissions".

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

Other examples:

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

Administrators automatically pass permission checks.

---

🛠️ Developer Utilities

Check Ready State

if (client.isReady()) {
  console.log("Bot is ready!")
}

Get Uptime

console.log(
  client.uptime
)

The value is returned in milliseconds.

Get the Bot User

console.log(
  client.user.username
)

Get Application ID

console.log(
  client.applicationId
)

---

❌ Error Handling

SimpleDiscord.js provides a structured "DiscordAPIError".

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

A typical error can provide:

DiscordAPIError
├── message
├── code
├── status
├── method
├── path
└── errors

This makes Discord API problems much easier to diagnose.

---

🧹 Clean Shutdown

SimpleDiscord.js supports clean shutdown handling.

client.destroy()

This closes the Gateway connection and resets the client's ready state.

---

📚 API Reference

Client

Property / Method| Description
"login(token)"| Connect to Discord
"destroy()"| Shut down the client
"command()"| Create a slash command
"removeCommand()"| Remove a slash command
"getCommand()"| Get a registered command
"hasCommand()"| Check for a command
"isReady()"| Check connection state
"uptime"| Client uptime in milliseconds
"user"| Logged-in Discord user
"applicationId"| Discord application ID

Builders

Builder| Purpose
"EmbedBuilder"| Create embeds
"ButtonBuilder"| Create buttons
"SelectMenuBuilder"| Create select menus
"ActionRowBuilder"| Organize components

---

🗂️ Recommended Project Structure

A simple project:

my-discord-bot/
├── index.js
├── package.json
├── package-lock.json
└── node_modules/

For a larger bot:

my-discord-bot/
├── index.js
├── package.json
├── commands/
│   ├── ping.js
│   ├── user.js
│   └── help.js
├── events/
│   ├── ready.js
│   └── interaction.js
└── utils/
    └── helpers.js

---

🧪 Testing

Before deploying your bot, test:

- [ ] Gateway connection
- [ ] Ready event
- [ ] Slash commands
- [ ] Command options
- [ ] Automatic command synchronization
- [ ] Command removal
- [ ] Messages
- [ ] Message editing
- [ ] Message deletion
- [ ] Embeds
- [ ] Embed fields
- [ ] Buttons
- [ ] Select menus
- [ ] Deferred replies
- [ ] Edited interaction replies
- [ ] Deleted interaction replies
- [ ] Permissions
- [ ] API error handling
- [ ] Client uptime
- [ ] Clean shutdown

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
- ✅ Component interactions

0.2.x — More Discord Features

- ✅ Interaction improvements
- ✅ ActionRowBuilder
- ✅ Command management
- ✅ Automatic command registration
- ✅ API error handling
- ✅ Developer utilities
- ✅ Documentation
- ⬜ More Discord API features

0.3.x — Developer Experience

- ⬜ More builder classes
- ⬜ Easier event handling
- ⬜ Improved command system
- ⬜ More developer utilities
- ⬜ Expanded documentation
- ⬜ Improved TypeScript support

1.0.0 — Stable Release

- ⬜ Stable API
- ⬜ Expanded Discord feature coverage
- ⬜ Production-ready release
- ⬜ Complete documentation
- ⬜ Long-term API stability

---

🧑‍💻 Contributing

Contributions, bug reports, feature requests, and improvements are welcome.

Before submitting a pull request:

1. Test your changes.
2. Keep the API simple.
3. Avoid breaking existing functionality.
4. Update documentation when adding features.
5. Include useful examples when appropriate.

---

🐛 Reporting Issues

If you encounter a bug, please provide:

- SimpleDiscord.js version
- Node.js version
- Operating system
- Relevant code
- Error message
- Steps to reproduce the issue

Never include your Discord bot token in an issue.

---

📜 License

SimpleDiscord.js is released under the MIT License.

See the ""LICENSE"" (LICENSE) file for the complete license text.

---

❤️ Support

If SimpleDiscord.js is useful to you:

⭐ Star the repository

🐛 Report bugs

💡 Suggest features

🔧 Contribute improvements

📦 Use it in your Discord projects

---

<div align="center">Simple Discord bots. Simple API. SimpleDiscord.js.

Made with ❤️ using JavaScript.

</div>
