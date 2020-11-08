# Flask BluePrint

- With tests in place, let's refactor the app, adding in Blueprints...

- Create a new directory in "project" called "api", and add an __init__.py file along with users.py and models.py. Then within users.py add the following:

- Here, we created a new instance of the Blueprint class and bound the ping_pong() function to it.

- ake note of the shell_context_processor . This is used to register the app and db to the shell. Now we can work with the application context and the database without having to import them directly into the shell.