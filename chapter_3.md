заливаем на pythonanywhere
1. создадим на github репозиторий.
Для начала создайте файл .gitignore для исключения файлов на индексацию при комитах, 
```bash
db.sqlite3
*.pyc
*.python
```
    ```bash
git init
    git add .
    git commit -m "pythonanywhere"
    git remote add origin  https://github.com/name/repository.git
    git push -u origin master
```
2. регистрируемя на pythonanywhere выбираем бесплатный аккаунт
3. заходи в bash с помощью cd .. спускаумся в корневой каталог.
Текущий каталог можно проверить pwd.
4. git clone https://github.com/name/repository.git
5. mkvirtualenv myenv --python=/usr/bin/python3.7
6. pip install -r requirements.txt
(зависмости вашего проекта requirements.txt pip freeze > requirements.txt)
В settings.py надо добавить 
```python
DEBUG = False
ALLOWED_HOSTS = ['*']
MEDIA_ROOT = u'/home/account/django_projec/media'
MEDIA_URL = '/media/'
STATIC_ROOT = u'/home/account/django_project/static'
STATIC_URL = '/static/'
```
`python3 manage.py migrate`
`python3 manage.py collectstatic`

7.  на pythonanywhere создаём новый web проект выбираем python3.7
далее custom.
8. В настройках проекта WSGI configuration file меняем на 
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
9. Static files:
url: static
Directory/home/account/django_project/static
10. Virtualenv: myenv
11. Нажимаем на Reload
12. Сайт готов.
