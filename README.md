# Custom Voice Channels Bot
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)


A Discord bot that lets users easily create, customize, and manage temporary voice channels on demand. Built with Discord.js in Node.js, it's perfect for communities that want flexible and user-controlled voice chat spaces.

<p align="center">
  <img src="https://i.imgur.com/Mhorgh2.gif" alt="Bot" />
</p>

## Features
*  **Persistent Customization.** User-defined settings like channel names and other preferences are saved and automatically restored—even if the channel is deleted or the bot restarts.
* **No External Database Needed.** Powered by Quick.db, the bot runs with built-in lightweight storage—no need for a separate database server.

## Prerequisites
* [Node.js and npm](https://nodejs.org/en)
* [git](https://git-scm.com/downloads) (or download repository manually)

## Setup guide
* Clone the repository (``git clone https://github.com/outdrifted/custom-voice-channels-bot``)
* Navigate to the repo (``cd Elixir-Bot``)
* Install all required NPM packages (``npm i``)
* Configuration files:
    * Edit guilds.json based on your guild. Template:
        ```
        {
            "guild_id": {
                "enabled": true,
                "roles": {
                    "blacklist": "role_id"
                },
                "vc": {
                    "channel": "role_id",
                    "category": "role_id"
                }
            }
        }
        ```
        * Replace `guild_id` with your guild ID.
        * `enabled` enables/disables the bot in a specific guild.
        * `roles.blacklist` is the ID of the role, that is not permitted to create voice channels.
        * `vc.channel` is the channel that a user joins to create a voice channel.
        * `vc.category` is the category the channel specified above is in.
    * In the bot's root directory, create a `.env` file. Contents: (note: if you don't have a bot token, see the "Create bot" section to [create a bot](https://discord.com/developers/applications))
        ```
        # Credentials (get from Discord Developers portal)
        BOT_TOKEN=

        # Bot user ID
        BOT_CLIENT_ID=

        # Bot owner user ID
        OWNER_ID=

        # Repeated channel creation cooldown (in seconds)
        VC_COOLDOWN=20
        ```
    * `deploy-commands.js` is used to register slash commands. The bot doesn't have any commands except for /ping, so it's not necessary to run it.
    * Run the bot: ``node bot.js``. On sucessful launch, you should see "Ready! Logged in as ..." in the terminal.
#### Optional:
* Install pm2 (``npm install pm2@latest -g``). This package allows your bot to run on system startup and automatically restarts it if it crashes:
    * While in the bot's directory, run it with: ``pm2 start bot.js``
    * Create startup script: ``pm2 startup``
    * Freeze process list: ``pm2 save``

## Create bot
Follow [this](https://discordjs.guide/preparations/setting-up-a-bot-application.html#creating-your-bot) tutorial to setup a bot account.
