# Reminder Bot / RBot
_A daily reminder bot for GroupMe_

Set a reminder for your whole group every day at a specific time.
[todo screen shot of "don't forget to log", "it's tea time", "don't forget, meeting is TONIGHT at 6:00!"]

## Available Commands
View the [full list](todo link) of available commands. The following are the recommended variations:
### Set up the bot
- Hey bot, set name to `X`
 - Hey bot, change name to X
- Hey bot, set reminder to `X`
 - Hey bot, set message to X
### Configure the bot
- Hey bot, set reminder time to `X`
 - Hey bot, set [remind/reminder/message] to [everyday, weekdays, weekends, M/T/W/Th/F/S] <- w/ spaces too
 - M/Mo/Monday/Mondays ... T/Th/R/Thursday/Thursdays
- Hey bot, set reminder time to weekdays
### Activate the bot
- Hey bot, activate
 - Hey bot, activate the reminder
 - Hey bot, enable
 - Hey bot, enable the reminder
### Preset the bot
- Hey bot, use the [user defined] preset
 - Hey bot, use the running preset
- Hey bot, save this preset [as `X`]
### Test the bot
- Hey bot, wake up[./!]
 - Hey bot, are you awake[?]
 - Hey bot, ping

## Getting Started
_Confused? Check out [these instructions](#getting-started-for-people-who-have-no-clue-what-they-are-doing)_
1. Add BOT_ID to the environment variables
 * Include your BOT_ID from the [GroupMe API bots page](https://dev.groupme.com/bots)
... todo

## Getting Started for people who have no clue what they are doing
1. Fork this repo
 * Click fork
2. Go to the [GroupMe Bots page](https://dev.groupme.com/bots) (you may need to create an account) and click [Create Bot](https://dev.groupme.com/bots/new). name, cb?
3. Create a free Heroku account and navigate to the [dashboard](https://dashboard.heroku.com/apps)
 * Click new -> create new app and name it whatever you want (reminder-bot-6000)
 * Click create app
 * Scroll down to Connect to GitHub
 * Select the repository you just forked (RBot)
4. In your Heroku app dashboard, navigate to Settings and click Reveal Config Vars
 * Enter BOT_ID as KEY and your GroupMe Bot ID in the VALUE section. Then click "Add."
5. Add-on [Heroku Scheduler](https://devcenter.heroku.com/articles/scheduler)
 > Navigate to the “Resources” tab of the app’s Dashboard. Search for “Heroku Scheduler” in the Add-ons search box. Follow the prompts to provision the Add-on.
 * Click on the Heroku Scheduler in the list and it will open a new tab
 * Click Create job and select Every 10 minutes. This will wake up our bot to check if it is time to send a message every 10 minutes.
 * In Run Command, type `node cron-check.js` and then press Save Job
... todo

## How it works
- Each message sent in GroupMe is also sent to the bot
- The bot has code written to parse the message and tell if you are talking to him (his name is Bob)
- If you are talking to him, you can configure settings (which are stored in a text file instead of a database for simplicity) or enable the daily reminder
- Heroku will wake the bot up temporarily every 10 minutes to check