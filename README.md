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

**4. Make Project**
```
django-admin startproject <projectname>
```

**5. Make runtime.txt and add your versuin of python in it like this**
```
python-3.7.4
```

**6. Make requirements.txt**
```
pip freeze >  requirements.txt
```

**7. Make a procfile and add**
```
web: gunicorn <project name>.wsgi:application --log-file -
```

**8. Add some Code in start of settings.py **
```
import django_heroku
import os
```

**9. Add some Code in end of settings.py **
```
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
django_heroku.settings(locals())
```

**10. Don't forget to add * in allowed host**
```
ALLOWED_HOSTS = ["*"]
```
