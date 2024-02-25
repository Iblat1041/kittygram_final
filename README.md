<h1 align='center'>
  Kittygram - социальная сеть для размещение фотографий домашних животных.
</h1>

<h2 align='center'>
  Описание проекта
</h2>
Проект, где пользователи могут регистрироваться, загружать фотографии кошек с описанием их достижений, а также любоваться на других котов.

<h2 align='center'>
  Технологии
</h2>

•	Python 3.9
•	Django==3.2.3
•	djangorestframework==3.12.4
•	nginx
•	gunicorn==20.1.0
• djoser==2.1.0


<h2 align='center'>
  Как запустить проект:
</h2>

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:Blathata/kittygram_final.git
```

Генерируем секретный ключ:

```
Запускаем интерпретатор Python
python manage.py shell
Генерируем ключ
from django.core.management.utils import get_random_secret_key
get_random_secret_key()
Создать папку .env в корне проекта
Добавить в переменую SECRET_KEY=... сгенерированый ключ
```

Перейти в корневую директорию
```
cd kittygram
```

Создать файл .evn для хранения ключей:

```
POSTGRES_USER=django_user
POSTGRES_PASSWORD=mysecretpassword
POSTGRES_DB=django
DB_HOST=db
DB_PORT=5432
```

Запустить docker-compose.production:

```
docker compose -f docker-compose.production.yml up
```

Выполнить миграции, сбор статики:

```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/

```

Создать суперпользователя, ввести почту, логин, пароль:

```
docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```

<h1 align='center'>
  Как работать с репозиторием финального задания
</h1>
<h2 align='center'>
  Что нужно сделать
</h2>

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

<h1 align='center'>
  Как проверить работу с помощью автотестов
</h1>

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.
<h1 align='center'>
  Чек-лист для проверки перед отправкой задания
</h1>

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.
