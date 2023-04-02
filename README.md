# YaMDb
Бэкенд API проекта YaMDb (ресурс для публикации отзывов к произведениям 
искусства и формирования их рейтинга)

##### Технологии
- Python 3
- Django 3.2
- Django REST Framework 3.12
##### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:grmzk/api_yamdb.git
```

```
cd api_yamdb/
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```

```
source venv/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```

##### Эндпоинты

Получить список всех произведений искусства:
```
GET /api/v1/titles/
```

Получить конкретную произведение по id:
```
GET /api/v1/titles/{id}/
```

Добавление отзыва к произведению:
```
JSON в теле запроса
{
    "text": "string",
    "score": "integer"
}

POST /api/v1/titles/{title_id}/reviews/
```

Полный список эндпоинтов:
```
http://127.0.0.1:8000/redoc/
```

##### Авторы
- Игорь Музыка [mailto:igor@mail.fake]
- Денис Попченко [mailto:denis@mail.fake]
- Александр Романов [mailto:alex@mail.fake]
- Yandex LLC
