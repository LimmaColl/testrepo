import telebot 

bot = telebot.TeleBot("6255876930:AAGd3NzdNCdRCDI37GdolUzfsICoSt58PK4", parse_mode=None)

@bot.message_handler(commands=['start', 'help'])
def send_welcome(message):
    print(message)
    print(message.from_user.id)
    print(message.from_user.first_name)
    print(message.from_user.last_name)
    print(message.from_user.username)
    print(message.text)
    bot.send_message(message, "Привет, ")

bot.message_handler(commands=['sleep'])
def send_sleep(message):
    bot.send_message(message, f"Пока, ")



@bot.message_handler(func=lambda m: True)
def echo_all(message):
    if message.text == "Привет":
        bot.reply_to(message, f"{message.text}, {message.from_user.first_name}")
    else:
        bot.send_message(message, "Напишите 'Привет'")
bot.infinity_polling()    
