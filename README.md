# errbot-backend-hangoutschat

*This is a Google Hangouts Chat backend for [Errbot](http://errbot.io/).*

Setup
-----

1. [Install errbot](http://errbot.io/en/latest/user_guide/setup.html)
   and follow to instructions to setup a `config.py`.

2. Clone this repository somewhere convenient.

3. Install the requirements listed in `requirements.txt`.

   - If you meet some SSL issue, try it.

   ```bash
   pip install -U pyOpenSSL cryptography
   ```

4. In Google Chat, create a bot that will represent ErrBot. If you need help with this step,
   check out [this](https://developers.google.com/hangouts/chat/how-tos/pub-sub) guide on Hangouts Chat bots based on Google Cloud Pub/Sub.

   - Setup Google Chat API

   1) Enable API

   2) Manage > CONFIGURATION > Connection settings: Cloud Pub/Sub [Set the Topic Name]


5. Edit your ErrBot's `config.py`. Use the following template for a minimal configuration:

   ```python
   import logging

   BACKEND = 'Hangoutschat'

   BOT_EXTRA_BACKEND_DIR = r'<path/to/errbot-backend-hangoutschat>'
   BOT_DATA_DIR = r'<path/to/your/errbot/data/directory>'
   BOT_EXTRA_PLUGIN_DIR = r'<path/to/your/errbot/plugin/directory>'

   BOT_LOG_FILE = r'<path/to/your/errbot/logfile.log>'
   BOT_LOG_LEVEL = logging.INFO

   BOT_IDENTITY = {
      'project_id': '<projectid>',
      'subscription_name': '<Subscription ID>',
      'credentials_path': '<path/to/your/googleserviceaccount.json>'
   }

   BOT_ADMINS = ('<your@email.address>',)
   CHATROOM_PRESENCE = ()
   ```

   Sections you need to edit are marked with `<>`.

6. [Start ErrBot](http://errbot.io/en/latest/user_guide/setup.html#starting-the-daemon).

   - Run as Daemon

   ```bash
   errbot --daemon
   ```

7. Debug

   Edit your ErrBot's `config.py`.

   ```python
   BOT_LOG_LEVEL = logging.DEBUG
   ```

   Run it with DEBUG log.
   ```bash
   export GOOGLE_APPLICATION_CREDENTIALS='<path/to/your/googleserviceaccount.json>'; errbot
   ```

8. How to call bot

   - DM
  
   ```bash
   !tryme
   ```

   - ROOM
  
   ```bash
   @bot !tryme
   ```
