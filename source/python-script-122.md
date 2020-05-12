---
title: python script 122 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '122'

Functions in program: 
* `def main():`
* `def timer(bot, update):`
* `def dice(bot, update):`
* `def start(bot, update):`
* `def choice(bot, update, job_queue, chat_data):`
* `def newKeyboard(bot, update, keyboard, oneTime, description = False):`
* `def task(bot, job):`
* `def set_timer(bot, update, args, job_queue, chat_data):`

## python 122

Python mysql example: 122

```python
from telegram.ext import Updater, MessageHandler, Filters, CommandHandler, JobQueue
from telegram import ReplyKeyboardMarkup, ReplyKeyboardRemove


SLOVAR = {}

def set_timer(bot, update, args, job_queue, chat_data):
    delay = int(args[0])
    job = job_queue.run_once(task, delay, context=update.message.chat_id)

    chat_data['job'] = job

    print('Вернусь через {} секунд!'.format(delay))

def task(bot, job):
    bot.send_message(job.context, text='Таймер истек')

def newKeyboard(bot, update, keyboard, oneTime, description = False):
    global markup
    markup = ReplyKeyboardMarkup(keyboard, one_time_keyboard = oneTime)
    update.message.reply_text("Выберите действие", reply_markup = markup)
    if description:
        update.message.reply_text(description)

def choice(bot, update, job_queue, chat_data):
    global SLOVAR
    slovar = SLOVAR
    try:
        exec(slovar[update.message.text]['task'])
    except KeyError:
        update.message.reply_text('Такое действие в данный момент недоступно, '+
                                  'либо вы ввели его неверно, попробуйте еще раз')
        print(SLOVAR)

def start(bot, update):
    print(update)
    global SLOVAR
    
    newKeyboard(bot, update, [['Кости', 'Таймер']], False, description = 'Нажмите на \"Кости\" для бросков кубиков\n'+
                                                                  'Нажмите на \"Таймер\" для засечения времени')
    
    SLOVAR = {"Кости": 
              {"task": "dice(bot, update)", "description": "Пользователю нужны кубики"},
              "Таймер": 
              {"task": "timer(bot, update)", "description": "Пользователю нужен таймер"}}

def dice(bot, update):
    global SLOVAR
    reply_keyboard = [['Кинуть один шестигранный кубик'], 
                      ['Кинуть 2 шестигранных кубика одновременно'], 
                      ['Кинуть 20-гранный кубик'], 
                      ['Вернуться назад']]
    
    newKeyboard(bot, update, reply_keyboard, False)
    
    SLOVAR = {"Кинуть один шестигранный кубик": 
                  {"task": "import random; update.message.reply_text(random.randint(1,6))", 
                   "description": "Кинуть один шестигранный кубик"},
              "Кинуть 2 шестигранных кубика одновременно": 
                  {"task": "import random; update.message.reply_text(random.randint(2,12))", 
                   "description": "Кинуть 2 шестигранных кубика одновременно"},
              "Кинуть 20-гранный кубик": 
                  {"task": "import random; update.message.reply_text(random.randint(1,20))", 
                   "description": "Кинуть 20-гранный кубик"},
              "Вернуться назад": 
                  {"task": "start(bot, update)", "description": 
                   "Вернуться на /start"}}

def timer(bot, update):
    global SLOVAR
    reply_keyboard = [['30 секунд'], 
                      ['1 минута'], 
                      ['5 минут'], 
                      ['Вернуться назад']]
    
    newKeyboard(bot, update, reply_keyboard, False)
    
    SLOVAR = {"30 секунд": 
                  {"task": "set_timer(bot, update, [30], job_queue, chat_data)", 
                   "description": "Таймер на 30 секунд"},
              "1 минута": 
                  {"task": "set_timer(bot, update, [60], job_queue, chat_data)", 
                   "description": "Таймер на 1 минуту"},
              "5 минут": 
                  {"task": "set_timer(bot, update, [300], job_queue, chat_data)", 
                   "description": "Таймер на 5 минут"},
              "Вернуться назад": 
                  {"task": "start(bot, update)", 
                   "description": "Вернуться на /start"}}

markup = 0

def main():
    updater = Updater("qqq")

    dp = updater.dispatcher

    dp.add_handler(CommandHandler("start", start))
    dp.add_handler(MessageHandler(Filters.text, choice, pass_job_queue=True, pass_chat_data=True))
    dp.add_handler(CommandHandler("dice", dice))
    dp.add_handler(CommandHandler("timer", timer))

    updater.start_polling()
    
    updater.idle()


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
