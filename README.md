<p align="center">
    <img src="https://github.com/mmdchnar/marzban-telebot/blob/main/screenshots/marzban-telebot2.PNG" alt="Charge screenshot" width="500" height="auto">
</p>

**<a href="https://github.com/mmdchnar/marzban-telebot/tree/main/screenshots">Screenshots</a>**

# Usage

First you need to clone [the repository](https://github.com/mmdchnar/marzban-telebot) to your sever. You can do it by this:

```bash
cd /opt/marzban
git clone https://github.com/mmdchnar/marzban-telebot
```

Then you have to map files to your docker container. Add this line to volume section of `docker-compose.yml`:

**(DO NOT REPLACE WHOLE FILE, Just the last two lines)**
```docker
services:
    marzban:
        ...
        volumes:
            ...
            - /opt/marzban/marzban-telebot/telegram:/code/app/telegram
            - /opt/marzban/marzban-telebot/config.py:/code/config.py
```
Then you have to edit your `.env` file.
edit like this:

**WARNING: `TELEGRAM_ADMIN_ID` renamed to `TELEGRAM_ADMINS_ID`**
```
TELEGRAM_API_TOKEN = 123456789:AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
TELEGRAM_ADMINS_ID = 987654321, 123456789
TELEGRAM_LOGGER_CHANNEL_ID = -1234567891234
TELEGRAM_VLESS_FLOW = "xtls-rprx-vision"
```

For logger channel you have to create a channel (its better to private), and send a message to the channel,
then forward the message to <a href="https://t.me/userinfobot">userinfobot</a> the bot send you the channel id


Now you can restart your marzban's docker:
```
marzban restart
```
---

# استفاده

اول باید  [رپوزیتوری](https://github.com/mmdchnar/marzban-telebot) رو تو سرورتون کلون کنید. برای اینکار این کامند هارو بزنید:

```bash
cd /opt/marzban
git clone https://github.com/mmdchnar/marzban-telebot
```

بعدش باید فایل هارو به داکر نشون بدید. برای این کار این دو خط رو به قسمت volume فایل `docker-compose.yml` اضافه کنید:

**(کل فایل رو جایگذین نکنید!! فقط دوخط اخر رو اضاف کنید)**
```docker
services:
    marzban:
        ...
        volumes:
            ...
            - /opt/marzban/marzban-telebot/telegram:/code/app/telegram
            - /opt/marzban/marzban-telebot/config.py:/code/config.py
```
بعذش باید فایل `.env` رو تغییر بدید.
این هارو تغییر بدید:

**توجه: اسم متغیر `TELEGRAM_ADMIN_ID` به `TELEGRAM_ADMINS_ID` تغییر کرده**
```
TELEGRAM_API_TOKEN = 123456789:AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
TELEGRAM_ADMINS_ID = 987654321, 123456789
TELEGRAM_LOGGER_CHANNEL_ID = -1234567891234
TELEGRAM_VLESS_FLOW = "xtls-rprx-vision"
```

برای کانال لاگر شما باید اول یک کانال (ترجیحا خصوصی) بسازید و داخلش یک پیام بفرستید.
حالا اون پیام رو برای ربات <a href="https://t.me/userinfobot">userinfobot</a> بفرستید تا ایدی عددی کانال رو بهتون بده و داخل فایل قرار بدید.


حالا مرزبان رو ریستارت میکنیم تا اعمال بشه:
```
marzban restart
```
