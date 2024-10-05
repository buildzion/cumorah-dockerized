# Python scripts

This directory is included in the container and added to the python path.
You can add a custom settings file here and override the DJANGO_SETTINGS_MODULE
value to point to it instead. 

If you create `local_settings.py` in this folder it will be imported at the end
of the default `cumorah.settings.production` settings module as a convenient
way for you to import customized settings.

