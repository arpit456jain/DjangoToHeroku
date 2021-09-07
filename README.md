# DjangoToHeroku
Step by step process of hosting django website to heroku

**1. Create a Virtual Environment**

- *On macOS and Linux:*
  ```bash
    python3 -m venv env
  ```
- *Windows*
  ```bash
    py -m venv env
  ````

**2. Activate the Virtual Environment**
  - *On Windows*
    ```bash
    .\env\Scripts\activate
    ```
  - *On macOS and Linux:*
    ```bash
    source env/bin/activate
    ```
    
**3. Install required modules**
```
pip install django gunicorn django-heroku
```

**4. Make Project and App**
```
django-admin startproject <projectname>
python manage.py startapp <app name>
```

**5. Make runtime.txt and add your versuin of python in it like this**
```
python-3.7.12
```

**6. Make requirements.txt**
```
pip freeze >  requirements.txt
```

**7. Make a Procfile and add this but make sure it has capital P**
```
web: gunicorn <project name>.wsgi:application --log-file -
```

**8. Add some Code in start of settings.py**
```
import django_heroku
import os
```

**9. Add some Code in end of settings.py**
```
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
django_heroku.settings(locals())
```

**10. Don't forget to add * in allowed host**
```
ALLOWED_HOSTS = ["*"]
```

**11. Now all done either you can push all this to GitHub and connect your heroku to Github and deploy master branch or you can use heroku CLI**

## For Heroku CLI follow these steps

**1. Login to heroku,make sure you had installed the heroku CLI**
```
heroku login
```

**2. Create heroku app**
```
heroku create <app-name>
```
**3. Push the code to heroku**
```
git add -A
git commit -a -m "first commit"
git push heroku master
```

**4. run migrate command**
```
heroku run python manage.py migrate
```

**5. For creating Superuser**
```
heroku run python manage.py createsuperuser
```
