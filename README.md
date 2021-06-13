# Telegram bots

Table of contents 
- <a href="#bots">My Bots</a>
- <a href="#upload">Upload methods</a>
  - <a href="#heroku">Heroku</a>
  - <a href="#google">Google Console</a>
  - <a href="#webhook">Web hook</a>
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
-  In your local directory create two files ( Procfile, runtime.txt) 
  - In runtime type `python-3.7.10`  or your python version. Note Heroku Supports specific versions of Python [See More](https://devcenter.heroku.com/articles/python-support).
  - In Procfile type `worker: python Your_script_name.py`
  - Create a new repository on github and upload your files
 -  Navigate to https://dashboard.heroku.com/apps/Your-App-Name/deploy/github,  click on github button, search and connect to bot's repository then click on deploy
 -  Navigate to https://dashboard.heroku.com/apps/Your-App-Name, click on Configure Dynos, click on pen icon, switch to active save it. Congratulations, your boot is now running smoothly 

## <div id="google">  Upload to Google Console</div>

  

   
