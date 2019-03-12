заливаем на pythonanywhere
1. создадим на github репозиторий.
Для начала создайте файл .gitignore для исключения файлов на индексацию при комитах, 
db.sqlite3
*.pyc
*.python
    git init
    git add .
    git commit -m "pythonanywhere"
    git remote add origin  https://github.com/name/repository.git
    git push -u origin master
2. регистрируемя на pythonanywhere выбираем бесплатный аккаунт
3. заходи в bash с помощью cd .. спускаумся в корневой каталог.
Текущий каталог можно проверить pwd.
git clone https://github.com/name/repository.git
mkvirtualenv myenv --python=/usr/bin/python3.7
pip install ваши библиотеки
4.  на pythonanywhere создаём новый web проект выбираем python3.7
далее custom.
5. В настройках проекта WSGI configuration file меняем на 
```python
import os
import sys
path = '/home/youaccount/dir_with_djangoproject'
if path not in sys.path:
    sys.path.append(path)
os.environ['DJANGO_SETTINGS_MODULE'] = 'app_name.settings'
from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()
```
6. Static files:
url: static
Directory/home/9kin/django-site-book/static
7. Virtualenv: myenv
8. В settings.py надо добавить 
```python
DEBUG = False
ALLOWED_HOSTS = ['*']
MEDIA_ROOT = u'/home/account/django_projec/media'
MEDIA_URL = '/media/'
STATIC_ROOT = u'/home/account/django_project/static'
STATIC_URL = '/static/'
```
9. заходим в bash
`python3 manage.py migrate`
`python3 manage.py collectstatic`
10. Нажимаем на Reload
11. Сайт готов.
