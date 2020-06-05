# Flask Example

Flask example based in the one created by the folks of [Real Python](https://realpython.com/flask-by-example-part-1-project-setup/)

## Virtual Environment
Python venv is used for developing purposes. Virtual environment is used in order to wrap all the dependencies inside the project and avoid collisions with the global configuration of Python. 


## Heroku
This app is deployed to a Heroku environment through a git remote bucket.
With the ```Procfile``` we detail the commands that are executed by the app on startup (in this case we call gunicorn to start the app)
With the ```runtime.txt``` we specify the Python Version that Heroku needs to use the right Python Runtime.


## Config settings
We use a ```config.py``` file to set up multiple config environments for our app.
This config is based from the Djang's config file. We have a base config class that the other class inherit form.

## Autoenv
[Autoenv](https://github.com/inishchith/autoenv) is a great tool for auto-activating virtualenvs and setting project-specific environment variables.
We use autoenv for entering the env every time we cd into our directory and setting the Development configuration.
Please use the tutorial for further information about the installation.