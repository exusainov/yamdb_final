# yamdb_final
![example branch parameter](https://github.com/exusainov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master)

Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).

# Техническая документация проекта yamdb_final
Документация API YaMDb доступна по адресу: http://127.0.0.1:8000/redoc/

​
### Как запустить проект:
​
Клонировать репозиторий и перейти в него в командной строке:
​
```
git clone git@github.com:exusainov/yamdb_final.git
​
cd yamdb_final
```
​
Cоздать и активировать виртуальное окружение:
​
```
python -m venv venv
​
source venv/Scripts/activate (source venv/bin/activate - для Mac)
```
​
Установить зависимости из файла requirements.txt:
​
```
python -m pip install --upgrade pip
​
pip install -r requirements.txt
```
​
Выполнить миграции:
​
```
python manage.py migrate
```
​
Создать суперпользователя:
​
```
python manage.py createsuperuser
```

Запустить проект:
​
```
python manage.py runserver
```
# Шаблон наполнение .env

Создать файл .env в папке infra/:

```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД 
```

# Запуск docker-compose. Взлетаем!

Пересоберите контейнеры и запустите их:


* docker-compose up -d --build

Выполните по очереди команды:

```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

Теперь проект доступен по адресу: http://localhost/


# Заполнить базу

Экспорт данных:


* python manage.py dumpdata > dump.json

Загрузка данных:


* python manage.py loaddata dump.json


# Технологии
​
Python3, Django, HTTP, Django Rest Framework, PostgreSQL, Docker, YandexCloud
​

​
# Авторы
​
- Хусаинов Евгений Маратович (Exusainov@yandex.com)
