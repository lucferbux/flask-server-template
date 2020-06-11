# Flask Example

Flask example based in the one created by the folks of [Real Python](https://realpython.com/flask-by-example-part-1-project-setup/)


## Deployment

### Heroku
This app is deployed to a Heroku environment through a git remote bucket.
With the ```Procfile``` we detail the commands that are executed by the app on startup (in this case we call gunicorn to start the app)
With the ```runtime.txt``` we specify the Python Version that Heroku needs to use the right Python Runtime.

1. Create the heroku apps

```heroku create [YOUR_APP_NAME]```

2. To add a heroku environment, add the following command:

```git remote add [ENVIRONMENT] git@heroku.com:[YOUR_APP_NAME].git```

This will create a new remote in git in which we can push all the changes to heroki

3. To config heroku, run this command for every environment we want to create:

```heroku config:set APP_SETTINGS=config.[CONFIGURATION REQUIRED] --remote [ENVIRONMENT]```

4. To push all the changes run

```heroku push [ENVIRONMENT] master```

5. Now run the app

```heroku run python app.py --app [YOUR_APP_NAME]```

6. Add the external dependencies (postgresql...)

```heroku addons:create heroku-postgresql:hobby-dev --app [YOUR_APP_NAME]```

## Configuration

### Virtual Environment
Python venv is used for developing purposes. Virtual environment is used in order to wrap all the dependencies inside the project and avoid collisions with the global configuration of Python. 

### Config settings
We use a ```config.py``` file to set up multiple config environments for our app.
This config is based from the Djang's config file. We have a base config class that the other class inherit form.

### Autoenv
[Autoenv](https://github.com/inishchith/autoenv) is a great tool for auto-activating virtualenvs and setting project-specific environment variables.
We use autoenv for entering the env every time we cd into our directory and setting the Development configuration.
Please use the tutorial for further information about the installation.


### .env File
The ```.env``` file stores all the environment variables needed to config the project. As we use autoenv, it searches for this file in order to get all the configuration we need.

## DDBB

### PostgreSQL
We use PostgreSQL to store data in the application. The connection is made by the SQLAlchemy module.

### Psycopg2
Psycopg is a Python adapter for Postgres

### Flask-SQLAlchemy
SQLAlchemy is the Python SQL toolkit and Object Relational Mapper that gives application developers the full power and flexibility of SQL.

### Flask-Migrate
Extension that supports SQLAlchemy database migrations via Alembic, offers this functionality:

* Can emit ALTER statements to a database in order to change the structure of tables and other constructs

* Provides a system whereby “migration scripts” may be constructed; each script indicates a particular series of steps that can “upgrade” a target database to a new version, and optionally a series of steps that can “downgrade” similarly, doing the same steps in reverse.

* Allows the scripts to execute in some sequential manner.

In order tu run *Flask-Migrate* we use the old ```Flask-Script```template, there are few steps:

* To init the migration script just run ```python manage.py db init``` the first time 
* Then ```python manage.py db migrate``` for the first migration
* Now just run ```python manage.py db upgrade``` every time there's a change

