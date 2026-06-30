import telebot

TOKEN = "ضع_التوكن_هنا"

bot = telebot.TeleBot(TOKEN)

files = {
    "123": "++ wh.cpp"
}

@bot.message_handler(func=lambda message: True)
def send_file(message):

    code = message.text

    if code in files:

        with open(files[code], "rb") as f:
            bot.send_document(message.chat.id, f)

    else:
        bot.reply_to(message, "الرمز غير صحيح")

print("Bot Running")

bot.infinity_polling()
