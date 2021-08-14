# Telegram bots

Table of contents 
- <a href="#bots">My Bots</a>
- <a href="#upload">Upload methods</a>
  - <a href="#heroku">Heroku</a>
  -  <a href="#webhook">Heroku Webhooks</a>
  - <a href="#google">Google Console</a>
  - <a href="#googlewebhook">AWS amazon cloud</a>
- <a href="#resource">Resources</a>



# <div id="bots"> My bots</div> 
- [Digital Cryptocurrency](https://github.com/AREEG94FAHAD/currencies_bot): With this bot, you can now monitor the prices of more than 12 digital Cryptocurrency 💰 💰
- [Text translator](https://github.com/AREEG94FAHAD/translate_text_bot): Translate your text  📜AR ➡️ 📜EN  and 📜EN ➡️ 📜AR
- [PDF merge](https://github.com/AREEG94FAHAD/pdfmerge_bot): With this bot, you can now simply merge your PDF files 📋
- [Remaining days](https://github.com/AREEG94FAHAD/remaining_days_bot): Calculate number of days between today and a date
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


Note: This  script will work base on polling mechanism  and it work 24/7.  That will lets you lose  550 free hours of Heroku quickly. So I prefer to deploy your code using webhook.[ For more details see ](https://blog.cloud-elements.com/webhooks-vs-polling-youre-better-than-this)




## <div id="webhook">  Upload to Heroku useing  Webhooks</div>
-  Create an account on [Heroku](https://id.heroku.com/login)
-  Create new app [new app](https://dashboard.heroku.com/apps)
-  I recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized . Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)
-  In your local directory, create two files ( Procfile, script.py) and install  [pyTelegramBotAPI](https://pypi.org/project/pyTelegramBotAPI/) by ``` pip install pyTelegramBotAPI ```

-  Install Flask framework ``` pip install Flask ```
  - In Procfile, type `web: python3 Your_script_name.py`
  - Go to Botfather in telegram and create new bot, add your APITOKEN in script.py
  - In script.py file, add this code 
  - Replace all https://your_heroku_project.com/ with your app link 
```
import os

from flask import Flask, request

import telebot

TOKEN = '<api_token>'
bot = telebot.TeleBot(TOKEN)
server = Flask(__name__)


@bot.message_handler(commands=['start'])
def start(message):
    bot.reply_to(message, 'Hello, ' + message.from_user.first_name)


@bot.message_handler(func=lambda message: True, content_types=['text'])
def echo_message(message):
    bot.reply_to(message, message.text)


@server.route('/' + TOKEN, methods=['POST'])
def getMessage():
    json_string = request.get_data().decode('utf-8')
    update = telebot.types.Update.de_json(json_string)
    bot.process_new_updates([update])
    return "!", 200


@server.route("/")
def webhook():
    bot.remove_webhook()
    bot.set_webhook(url='https://your_heroku_project.com/' + TOKEN)
    return "!", 200


if __name__ == "__main__":
    server.run(host="0.0.0.0", port=int(os.environ.get('PORT', 5000)))
```
- Save all the project dependencies into requirements file using ``` pip freeze > requirements.txt ```
- Create a new repository on github and upload your files
-  Navigate to https://dashboard.heroku.com/apps/Your-App-Name/deploy/github,  click on github button, search and connect to bot's repository then click on deploy


## <div id="google">  Upload to Google Console</div>
- Create an account on [Google console](https://console.cloud.google.com/)
- Link your Credit Card to get 300$ Valid for 90 days.
- From Sidebar navigate to Compute Engine  as shown in figure below 
![Capture](https://user-images.githubusercontent.com/30151596/121922925-12645400-cd43-11eb-8058-51eea8b328e2.PNG)
- Click on button called Create new instance . There are a lot of options I kept the default sitting then click create.
![c2](https://user-images.githubusercontent.com/30151596/121924262-6885c700-cd44-11eb-8b16-42b33cee5326.PNG)
- Click on SSH and check Python version ``` python3 -V  ```in usually, you will see the python is already installed. If no, install python by type ``` sudo apt-get install python version ```
- Install by pip by type, ``` sudo apt install python3-pip ```
- Install  [pyTelegramBotAPI](https://pypi.org/project/pyTelegramBotAPI/) by type  ``` pip3 install pyTelegramBotAPI ```
- Upload your script_name.py from local directory to google console by click on sitting icon in top correner and select upload file. ![up](https://user-images.githubusercontent.com/30151596/121935143-c9b39780-cd50-11eb-9288-c02a84261baa.PNG)

- Run the script by type, ``` python3 script_name.py ``` . If you close the ssh window, then bot will stop running. To avoid that, you need to use [tmux](https://github.com/tmux/tmux) : To allow your script running in background even if you close the SSH Windows.
- To use tmux type ``` Ctrl+ c``` then install tmux  by type, ``` sudo apt install tmux```
- type ``` tmux ```then run your script by type ``` python3 script_name.py ``` close the windows and go to start new thing. I guarantee that your bot won't close.
- To stop the bot type, ```ctrl + c ``` to back to main screen type, ``` ctrl + d ```  to start new tmux type ``` tmux ```, to terminate your bot type, you can run multi script by close the windows and open it again, type ``` tmux``` and run your another script. to terminate anyone just type ```tmuc ls``` this will display all your tmux sessions. Can  terminate anyone by type, ``` tmux a-t_number```


<!-- ## <div id="googlewebhook">  Upload to Google Console using Webhooks</div>
- Repate first seven points of Upload to Google Console
- Install flask by type, ```pip3 install flask ```
- Create new file in your directory called script.py,  past below code. Upload file to google cloud as mentioned above. 
``` 
import os

from flask import Flask, request

import telebot

TOKEN = '<api_token>'
bot = telebot.TeleBot(TOKEN)
server = Flask(__name__)


@bot.message_handler(commands=['start'])
def start(message):
    bot.reply_to(message, 'Hello, ' + message.from_user.first_name)


@bot.message_handler(func=lambda message: True, content_types=['text'])
def echo_message(message):
    bot.reply_to(message, message.text)


@server.route('/' + TOKEN, methods=['POST'])
def getMessage():
    json_string = request.get_data().decode('utf-8')
    update = telebot.types.Update.de_json(json_string)
    bot.process_new_updates([update])
    return "!", 200


@server.route("/")
def webhook():
    bot.remove_webhook()
    bot.set_webhook(url='https://your_heroku_project.com/' + TOKEN)
    return "!", 200


if __name__ == "__main__":
    server.run(host="0.0.0.0", port=int(os.environ.get('PORT', 5000)))
```
- Your app is finished and ready to be containerized and uploaded to Container Registry.
- create new file by type  ``` touch Dockerfile ```, type ``` nano Dockerfile ``` and past code below. Click ```ctrl+x then press, y, then enter.```
```
FROM python:3.7-slim
ENV PYTHONUNBUFFERED True
ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./
RUN pip install Flask gunicorn
CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 --timeout 0 script:app
```
- Add a .dockerignore file to exclude files from your container image. By type, ```touch touch .dockerignore``` then nano .dockerignore add code below then  Click ```ctrl+x then press, y, then enter.```
```
- Build your container image using Cloud Build, by runing this command 
```
 -->
