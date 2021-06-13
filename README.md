# Telegram bots

Table of contents 
- <a href="#bots">My Bots</a>
- <a href="#upload">Upload methods</a>
  - <a href="#heroku">Heroku</a>
  -  <a href="#webhook">Web hook</a>
  - <a href="#google">Google Console</a>
- <a href="#resource">Resources</a>



# <div id="bots"> My bots</div> 
- [Digital Cryptocurrency](https://github.com/AREEG94FAHAD/currencies_bot): With this bot, you can now monitor the prices of more than 12 digital Cryptocurrency 💰 💰
- [Text translator](https://github.com/AREEG94FAHAD/translate_text_bot): Translate your text  📜AR ➡️ 📜EN  and 📜EN ➡️ 📜AR
- [PDF merge](https://github.com/AREEG94FAHAD/pdfmerge_bot): With this bot, you can now simply merge your PDF files 📋
- [Jokes](https://github.com/AREEG94FAHAD/tell_me_a_joke): Use this bot to change your unhappiness by joke 😂
- [Convert voice to text](https://github.com/AREEG94FAHAD/co-voice-txt-and-tran): A telegram bot to convert a voice to text and translating it 🎤 ➡️ 📜
- [Lorem ipsum](https://github.com/AREEG94FAHAD/lorem_ip_bot): A Lorem ipsum bot, supports three languages 📝
- [Photo compressor](https://github.com/AREEG94FAHAD/compression_img_bot): With this bot, you can now compress your photo 🖼️🖼️
- [Resize your image](https://github.com/AREEG94FAHAD/resizeimage_bot): A telegram bot for changing the size of an image to any size. It can be used to resize the images to be suitable for posting on social media, or any other platform ✂️🖼️
- [The Quran Karim](https://github.com/AREEG94FAHAD/quran_bot): A special bot for reading the Quran karim ☪️️☪️️
- [Video to mp3](https://github.com/AREEG94FAHAD/conv_vid_to_mp3): With this bot, you can now convert your video to mp3 📸 -> 🎤

# <div id="upload"> Upload methods </div>

## Upload to Heroku
-  Create an account on [Heroku](https://id.heroku.com/login)
-  Create new app [new app](https://dashboard.heroku.com/apps)
-  I recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized . Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)
-  In your local directory, create three files ( Procfile, runtime.txt, script.py) and install  [pyTelegramBotAPI](https://pypi.org/project/pyTelegramBotAPI/) by ``` pip install pyTelegramBotAPI ```
  - In runtime file,  type `python-3.7.10`  or your python version. Note Heroku Supports specific versions of Python [See More](https://devcenter.heroku.com/articles/python-support).
  - In Procfile, type `worker: python Your_script_name.py`
  - Go to Botfather in telegram and create new bot, add your APITOKEN in script.py
  - In script.py file, add this code 
  

```import telebot

API_TOKEN = '<api_token>'

bot = telebot.TeleBot(API_TOKEN)


# Handle '/start' and '/help'
@bot.message_handler(commands=['help', 'start'])
def send_welcome(message):
    bot.reply_to(message, """\
Hi there, I am EchoBot.
I am here to echo your kind words back to you. Just say anything nice and I'll say the exact same thing to you!\
""")


# Handle all other messages with content_type 'text' (content_types defaults to ['text'])
@bot.message_handler(func=lambda message: True)
def echo_message(message):
    bot.reply_to(message, message.text)


bot.polling()
```
  - Save all the project dependencies into requirements file using ``` pip freeze > requirements.txt ```
  - Create a new repository on github and upload your files
 -  Navigate to https://dashboard.heroku.com/apps/Your-App-Name/deploy/github,  click on github button, search and connect to bot's repository then click on deploy
 -  Navigate to https://dashboard.heroku.com/apps/Your-App-Name, click on Configure Dynos, click on pen icon, switch to active save it. Congratulations, your boot is now running smoothly 


Note: This  script  work base on polling mechanism  and it work 24/7.  This lets you lose  550 free hours of Heroku quickly. So I prefer to deploy your code using webhook.[ For more details see ](https://blog.cloud-elements.com/webhooks-vs-polling-youre-better-than-this)




## <div id="webhook">  Upload to Heroku useing  Web hook</div>


## <div id="google">  Upload to Google Console</div>

  

   
