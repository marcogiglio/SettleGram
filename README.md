# SettleGram: a Group Expenses Tracking Bot

This repository contains a telegram bot to track common expenses in a Telegram group. Expenses are added 
in natural language, and internally processed by NLP tools. The bot is integrated with Telegram user actions:
* If a user leaves a group or is banned, the bot will consider him inactive from now on and it won't add it to further common expenses
* If a user joins or is added to a group, the bot will consider him for new expenses

At this moment, the NLP processing is only working for Italian. The bot has access to the names and username of the members of a group and therefore will be able to understand when you refer to someone by either methods. The following are same examples of common expenses which are well-understood by the bot:

* Francesca ha speso 102 € per la spesa per tutti
* Edoardo ha speso 25.2 euro per il pranzo da dividere tra lui, Marco, Francesca e Giulia
* Ho speso 4 euro per i caffè di Edoardo e Chiara
* Chiara ha pagato 35,5 € per la cena da dividere tra lei, Marco e Giulia
* Ho pagato 15 euro per la pizza da dividere tra me e Francesca

If you want to see the balance just send the message (if you are using the public instance):
* @settlegrambot balance 

I will work on the english version soon, stay tuned! (or follow the repo!)
### Why I wrote this tool
I wrote this bot for my own needs. I am lucky enough to have a sizeable group of close friends,
and we travel together few times a year. Moreover, we all use Telegram for messaging. So far, in order
to track common expenses and settle them at a later date we relied on apps such as SettleUp and SplitWise.
But I have noticed that usually is one person that takes on the chore of inputing the expenses within the app.
Moreover, since they are sendomly used, most of the people in our groups do not have the app installed on their phones.
For these reasons, I have decided to take advantage of the Telegram API to build a bot to integrate an expense tracking
functionality directly within the Telegram group we usually create to organize our holidays. 

### Technologies used 
The bot leverages:
* [Telethon](https://github.com/LonamiWebs/Telethon): a Python-3 library to interact with Telegram Client API
* [Spacy](https://spacy.io): a Python-3 library with amazing tools to perform NLP processing. 
* MongoDB: to save the group state
* Docker: for easy deployment on a cloud instance


### Public instance:
I have deployed a free public instance. Just add @settlegrabot in your group to use it. 
At this time I cannot make any guarantee of uptime nor of data reliability. 

### How to launch your own private instance: 
After having ssh into your VPS, run the following commands:
```console
git clone git@github.com:marcogiglio/SettleGram
```
Get your [secrets from Telegram](https://core.telegram.org/api/obtaining_api_id) and create a file called secrets.env with this structure:
To access the bot token key, you need to create a new bot by contacting [the bot father](https://t.me/botfather)
```console
API_ID='your_api_id'
API_HASH='your_api_hash'
TOKEN_KEY='your_token_key'
```
Enter the repository folder and now you can run the following command launch the docker containers:
```console
 docker-compose up --build -d 
```

