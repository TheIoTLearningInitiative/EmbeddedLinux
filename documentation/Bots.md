# Bots

> A new era of messaging. Telegram is a cloud-based mobile and desktop messaging app with a focus on security and speed. [Homepage](https://telegram.org/)
> Telegram Web Version 0.5.4 [Homepage](https://web.telegram.org/#/im)


![Telegram](https://telegram.org/img/t_logo.png)

[Everything you need is here](https://flowxo.com/features)

## Bot Revolution

> Bots are simply Telegram accounts operated by software – not people – and they'll often have AI features. They can do anything – teach, play, search, broadcast, remind, connect, integrate with other services, or even pass commands to the Internet of Things [Bot Revolution](https://telegram.org/blog/bot-revolution)

- [Sample Slack bot built with Botkit](https://github.com/howdyai/botkit-middleware-witai/blob/master/example_bot.js)
- [A customizable life embetterment robot](https://hubot.github.com/)
- [Cisco brings some (real) friends to the chat-bot party](http://www.computerworld.stfi.re/article/3094288/cloud-computing/cisco-brings-some-real-friends-to-the-chat-bot-party.html)

## Bots: An introduction for developers

Bots are third-party applications that run inside Telegram. Users can interact with bots by sending them messages, commands and inline requests. You control your bots using HTTPS requests to our bot API. [Bots: An introduction for developers](https://core.telegram.org/bots)

1. What can I do with bots?
2. How do bots work?
3. How do I create a bot?
4. How are bots different from humans?
5. Bot perks

## Bot Code Examples

> Many members of our community are building bots and publishing the source code. We collect these examples here. Ping us on BotSupport if you've built a bot and would like to share its code with others [Bot Code Examples](https://core.telegram.org/bots/samples)

## BotFather

- Go to [Web Telegram Org](https://web.telegram.org/#/im) and sign up
- Search for BotFather and add it, click on it

```sh
BotFather:
They call me the Botfather, I can help you create and set up Telegram bots. Please read this manual before we begin:
https://core.telegram.org/bots

You can control me by sending these commands:

/newbot - create a new bot
/token - generate authorization token
/revoke - revoke bot access token
/setname - change a bot's name
/setdescription - change bot description
/setabouttext - change bot about info
/setuserpic - change bot profile photo
/setinline - change inline settings
/setinlinegeo - toggle inline location requests
/setinlinefeedback - change inline feedback settings
/setcommands - change bot commands list
/setjoingroups - can your bot be added to groups?
/setprivacy - what messages does your bot see in groups?
/deletebot - delete a bot
/cancel - cancel the current operation
```

## Bot Creation

```sh
Abraham:
/newbot

[7:31:40 PM] BotFather:
Alright, a new bot. How are we going to call it? Please choose a name for your bot.

[7:31:57 PM] Abraham:
Xe1GyqExample

[7:31:58 PM] BotFather:
Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bot.

[7:32:06 PM] Abraham:
Xe1GyqExampleBot

[7:32:08 PM] BotFather:
Done! Congratulations on your new bot. You will find it at telegram.me/Xe1GyqExampleBot. You can now add a description, about section and profile picture for your bot, see /help for a list of commands. By the way, when you've finished creating your cool bot, ping our Bot Support if you want a better username for it. Just make sure the bot is fully operational before you do this.

Use this token to access the HTTP API:
231219005:BBFq9seF0LfVuUvjifc8cBYfCngGcbcGdYs

For a description of the Bot API, see this page: https://core.telegram.org/bots/api
CANCELFORWARD 1 DELETE 1 REPLY
```

- Search for the Bot already created and add it to your contacts

# Python Telegram Bot Library Installation


> Not just a Python Wrapper around the Telegram Bot API [Homepage](https://python-telegram-bot.org/) [Github](https://github.com/python-telegram-bot)

![Python Telegram Bot](https://raw.githubusercontent.com/python-telegram-bot/logos/master/logo/png/ptb-logo_240.png)


```sh
root@edison:~# opkg install python-pip python-dev
root@edison:~# pip install setuptools
root@edison:~# pip install requests --upgrade
root@edison:~# pip install future --upgrade
root@edison:~# pip install python-telegram-bot --upgrade
```

```sh
root@edison:~# cd
root@edison:~# git clone https://github.com/python-telegram-bot/python-telegram-bot.git
Cloning into 'python-telegram-bot'...
remote: Counting objects: 5289, done.
remote: Total 5289 (delta 0), reused 0 (delta 0), pack-reused 5289
Receiving objects: 100% (5289/5289), 1.52 MiB | 772.00 KiB/s, done.
Resolving deltas: 100% (3876/3876), done.
Checking connectivity... done.
root@edison:~# cd python-telegram-bot
root@edison:~/python-telegram-bot# python setup.py install
...
...
root@edison:~# cd
```

# Bot Example

```sh
root@edison:~# vi telegrambot.py
```

```python
#!/usr/bin/python

import time

import pyupm_grove as grove
import pyupm_i2clcd as lcd

from telegram.ext import Updater, CommandHandler, MessageHandler, Filters

light = grove.GroveLight(1)
temperature = grove.GroveTemp(0)
display = lcd.Jhd1313m1(0, 0x3E, 0x62)

def functionLight(bot, update):
    luxes = light.value()
    bot.sendMessage(update.message.chat_id, text='Light ' + str(luxes))

def functionTemperature(bot, update):
    degrees = temperature.value()
    bot.sendMessage(update.message.chat_id, text='Temperature ' + str(degrees))

def functionEcho(bot, update):
    bot.sendMessage(update.message.chat_id, text=update.message.text)

if __name__ == '__main__':

    updater = Updater("219701132:AAEBn3_9ZBN-Lk8l8kRnkLKegmjA-S5iPaQ")
    dp = updater.dispatcher

    dp.add_handler(CommandHandler("light", functionLight))
    dp.add_handler(CommandHandler("temperature", functionTemperature))
    dp.add_handler(MessageHandler([Filters.text], functionEcho))

    updater.start_polling()

    while True:

        degrees = temperature.value()
        luxes = light.value()

        display.setColor(255, 0, 0)

        display.setCursor(0,0)
        display.write('Light ' + str(luxes))

        display.setCursor(1,0)
        display.write('Temperature ' + str(degrees))

        time.sleep(1)

    updater.idle()
    del temperatura
```

```sh
root@edison:~# python telegrambot.py
```

- Interact with your Bot using the Web Telegram Org Application

# BeepBoop

> Beep Boop is a ridiculously simple hosting platform for your Slack and Messenger bots [Homepage](https://beepboophq.com/)

- [Coding a Weather Slackbot for Beep Boop with Wit.ai](https://www.youtube.com/watch?v=fus357b19io)