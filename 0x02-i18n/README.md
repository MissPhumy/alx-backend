# 0x02. i18n
## Flask i18n Project

This project demonstrates the implementation of internationalization (i18n) in a Flask application. The main objective is to localize the app by displaying different languages and timezones based on user settings, URL parameters, and request headers.

## Learning Objectives

- Parametrize Flask templates to display different languages
- Infer the correct locale based on URL parameters, user settings, or request headers
- Localize timestamps

## Requirements

- Python 3
- Flask
- Flask-Babel
- pytz

## Setup

1. Clone the repository:

   ```sh
   git clone https://github.com/yourusername/flask-i18n.git
   cd flask-i18n
Install the required packages:

sh
Copy code
pip install -r requirements.txt
Tasks
0. Basic Flask App
Create a basic Flask app in 0-app.py with a single / route and an index.html template that outputs "Welcome to Holberton" as the page title and "Hello world" as the header.

1. Basic Babel Setup
Install the Babel Flask extension:

sh
Copy code
pip install flask_babel==2.0.0
Instantiate the Babel object in your app and store it in a module-level variable named babel.

Create a Config class to set available languages ["en", "fr"], default locale "en", and timezone "UTC".

Use this class as the config for your Flask app.

2. Get Locale from Request
Create a get_locale function using the babel.localeselector decorator.
Use request.accept_languages to determine the best match with supported languages.
3. Parametrize Templates
Use the _ or gettext function to parametrize your templates.

Create a babel.cfg file and initialize translations:

sh
Copy code
pybabel extract -F babel.cfg -o messages.pot .
pybabel init -i messages.pot -d translations -l en
pybabel init -i messages.pot -d translations -l fr
Edit the translation files and compile the dictionaries:

sh
Copy code
pybabel compile -d translations
4. Force Locale with URL Parameter
Update get_locale to detect locale in URL parameters and return it if supported, otherwise, fall back to default behavior.
5. Mock Logging In
Create a mock user table in 5-app.py.
Define a get_user function to return a user dictionary based on login_as URL parameter.
Use before_request decorator to set the user as a global on flask.g.user.
6. Use User Locale
Update get_locale to prioritize locale settings from URL parameters, user settings, request headers, and default locale.
7. Infer Appropriate Time Zone
Define a get_timezone function using the babel.timezoneselector decorator.
Prioritize timezone settings from URL parameters, user settings, and default to UTC.
Validate the time zone using pytz.timezone.
8. Display the Current Time
Display the current time on the home page based on the inferred time zone.
Use translations for the time format.
Running the Application
Run the Flask application:

sh
Copy code
flask run
Access the application in your browser at http://127.0.0.1:5000.


