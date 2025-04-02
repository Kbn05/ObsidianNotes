Let's start with the setup config for Django project. First, we must create a venv using the following command:
powershell/cmd: python -m venv <name>
					(module) virtual enviroment
bash: python3 -m venv <name>

Once it's installed, we must select the python interpreter, in this case v-env. Next step, is to activate the v-env. 
Powershell: start \route-to-script-file-activate.bat
Same way with bash.

Then we can install Django:
pip install django==version

To see the installed dependencies, use:
pip freeze

To start a Django project type:

django-admin startproject <name>

It creates a folder with the name speficied, which includes:
<name>/manage.py: command line that we will use to create apps and interact with webserver
<name>/<name>/settings.py: all the server configs
<name>/<name>/urls.py: paths the users can request or access

With Django you can perform db migrations, or ORM, transforming all the python classes into SQL statements with the command(you must be in the same path level as manage.py):

python manage.py migrate

It migrates all the preconfig modules or apps like admin module for website administration, authentication, session, etc that are into settings.py, you can also delete or configure them as needed.

After this, it creates a new file called db.sqlite because into the preconfig parameters include the sqlite3 as default db

In settings.py a functionality is enabled that aids in debug or during development phases, it must be disabled if you send to prod because it displays errors or if a library or dependency is deprecated, making it a vulnerability. 

AllowedHost allows you to block the access to the site according to IP, or country, etc.

Python also includes a web server for testing purposes only, not for production deployment. It runs with:

python manage.py runserver

In Django, each module works as an app

static_url refers to the path of static components like img, music, etc.

A Django project could have multiple applications, in this example we're going to create a blog app that includes authors, comments, etc.
To create it, type:

python manage.py startapp <name>

Work/modify as many folders as needed, define the structure for your app inside models.py, each class you create will be converted into a SQL table. To activate your app in Django, specify the path to appsConfig, which is located in apps.py, write it into the "installed apps" field located in setting.py like this:

'blog.apps.BlogConfig',

To migrate the classes you created in models.py, execute:
python manage.py makemigrations <nameApp>

It should return a new file in the migrations directory named after the migration number, ex:

0001_initial.py

This file contains all the SQL code that will be executed and sent to the db manager, and if you want to see the SQL statements type:

python manage.py sqlmigrate <nameApp> <migrationNumber>

Finally, to execute the migration type:

python manage.py migrate

For administration purposes, it's necessary create a superuser, which can administrate the app. To create a new superuser, type:

python manage.py createsuperuser

<superUser cred>
username: kbn
email: djangoadmin@kbn.com
password: zot10175
</superUser cred>

To access the adminTools, request the path: {{URL}}/admin

The first time you open this, you'll realize that you can't see the project you added later. In this step it's necessary define the route through admin.py file.

Import the class and then register the class into the admin site like this:

from .models import <class>

admin.site.register('class')

Inside the administration console, you can see now the new app. If you click on it, will redirect you into a panel administration where you can see all the data asociated with the app. Also you can add more data inside de panel.

You can also interact with web server through command line typing:

python manage.py shell


Ley 23 del 82 -> Ley de protección de derechos de autor
El software no se inventa
Decreto 1360 del 89 -> Reglamenta inscripción del software y la protección que brindan
