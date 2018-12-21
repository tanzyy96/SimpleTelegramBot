# SimpleTelegramBot
Make a simple Telegram Bot

The main component of a Telegram Bot is always 3 parts:
1) Chat Messages
2) Queries
    - callback queries
    - inline queries
3) Threading
4) Main Loop

telepot API commands

BASIC:
  telepot.Bot(TOKEN)
    # main telegram bot reference
        ## bot.sendMessage(chat_id,text,reply_markup=None)
        ## reply_markup can be InlineKeyboardMarkup, ReplyKeyboardMarkup .etc

  telepot.glance(msg)
    # analyse type of msg; returns dictionary {content_type, chat_type, chat_id}
    # msg in form:
      ```python
      {'chat': {'first_name': 'Tanzy', 'id': 366058116, 'type': 'private'},
 'date': 1545385866,
 'from': {'first_name': 'Tanzy',
          'id': 366058116,
          'is_bot': False,
          'language_code': 'en'},
 'message_id': 29,
 'text': 'hi'}
      ```
    MessageLoop(bot,handle).run_as_thread()
      # bot is name of bot
      # handle refers to handle_message function
      # run_as_thread breaks on error
