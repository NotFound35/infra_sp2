# Запуск docker-compose. Проект YaMDb

Яндекс Практикум. Проект 15-го спринта: запуск docker-compose.

## Описание

Проект `YaMDb` собирает отзывы пользователей на произведения из категорий: «Книги», «Фильмы», «Музыка».

## Функционал

- Произведения делятся на категории. Список категорий может быть расширен администратором;
- Произведения, фильмы и музыка не хранятся в приложении;
- В каждой категории есть произведения: книги, фильмы или музыка;
- Произведению может быть присвоен жанр из списка предустановленных. Новые жанры может создавать только администратор;
- Пользователи могут оставлять отзывы и ставить оценку произведениям. Из пользовательских оценок формируется рейтинг. На одно произведение можно оставить только один отзыв.

## Установка

1. Проверить наличие Docker

   Прежде чем приступать к работе, убедиться что Docker установлен, для этого ввести команду:

   ```bash
   docker -v
   ```

   В случае отсутствия, скачать [Docker Desktop](https://www.docker.com/products/docker-desktop) для Mac или Windows. [Docker Compose](https://docs.docker.com/compose) будет установлен автоматически.


2. Клонировать репозиторий на локальный компьютер

   ```bash
   git clone https://github.com/NotFound35/infra_sp2.git
   ```

3. В корневой директории создать файл `.env`, согласно примеру:

   ```bash
   DB_ENGINE=django.db.backends.postgresql
   DB_NAME=postgres
   POSTGRES_USER=postgres
   POSTGRES_PASSWORD=postgres
   DB_HOST=db
   DB_PORT=5432
   ```

4. Запустить `docker-compose`

   Выполнить из корневой директории команду:

   ```bash
   docker-compose up -d
   ```

5. Заполнить БД

   Создать и выполнить миграции:

   ```bash
   docker-compose exec web python manage.py makemigrations --noinput
   docker-compose exec web python manage.py migrate --noinput
   ```

6. Подгрузить статику

   ```bash
   docker-compose exec web python manage.py collectstatic --no-input
   ```

7. Заполнить БД тестовыми данными

   Для заполнения базы использовать файл `fixtures.json`, в директории `infra_sp2`. Выполните команду:

   ```bash
   docker-compose exec web python manage.py loaddata fixtures.json
   ```

8. Создать суперпользователя

   ```bash
   docker-compose exec web python manage.py createsuperuser
   ```

9. Остановить работу всех контейнеров

   ```bash
   docker-compose down
   ```

10. Пересобрать и запустить контейнеры

    ```bash
    docker-compose up -d --build
    ```

11. Мониторинг запущенных контейнеров

    ```bash
    docker stats
    ```

12. Остановить и удалить контейнеры, тома и образы

    ```bash
    docker-compose down -v
    ```