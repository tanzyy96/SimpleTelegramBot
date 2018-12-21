# SimpleTelegramBot
Make a simple Telegram Bot

The main component of a Telegram Bot is always 3 parts:
1) Managing Chat Messages
2) Managing Queries
    - callback queries
    - inline queries
3) Threading
4) Main Loop

## Part 0: Basic telepot API commands

Here are some useful telepot API commands needed for any basic Telegram bot.

#### 0.1 telepot.Bot(TOKEN)

This is the main telegram bot reference.
Methods include ```bot.sendMessage(chat_id,text,reply_markup=None)``` where reply_markup can be InlineKeyboardMarkup, ReplyKeyboardMarkup. etc

#### 0.2 telepot.glance(msg)

This is read the **Message** object when the Telegram bot receives messages from users. This method returns dictionary of ```{content_type, chat_type, chat_id}```

Just for understanding purposes, **Message** object is a 2D-dictionary:
```python
{'chat': {'first_name': 'Tanzy',
          'id': 123456789, 
          'type': 'private'},
 'date': 1545385866,
 'from': {'first_name': 'Tanzy',
          'id': 123456789,
          'is_bot': False,
          'language_code': 'en'},
 'message_id': 29,
 'text': 'hi'}
```

#### 0.3 MessageLoop(bot,handle=None).run_as_thread()

MessageLoop has inbuilt offset handling. This means the Telegram bot will only pick up new, "unread" messages.
- Parameters:
    - *bot* : The name of the bot
    - *handle* : The function handling the incoming messages. This can take up a <u>routing table</u>, which allows users to route the incoming messages according to their *flavor*, which is basically the type of response. This can vary from being a simple chat message to an inline button response. More on that later.

