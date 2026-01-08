ERD - Интернет-магазин одежды (Django + HTMX + Alpine.js)

Запуск проекта
1. Локальный запуск (без Docker)
Установите зависимости:
python -m pip install -r requirements.txt
Создайте и активируйте виртуальное окружение:
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate    # Windows
Настройте переменные окружения:
# Заполните .env своими значениями(пример .env ниже)
Запустите миграции:
python manage.py migrate
Создайте суперпользователя:
python manage.py createsuperuser
Запустите сервер:
python manage.py runserver
2. Запуск на сервере (с SSL)
Подготовьте домен:

Укажите DNS запись для domen.com на ваш IP
Настройте .env:

SECRET_KEY='example'

POSTGRES_DB=enfdb
POSTGRES_USER=enfdb
POSTGRES_PASSWORD=enfdb
POSTGRES_HOST=localhost # db если запускаете на vps
POSTGRES_PORT=5432

STRIPE_SECRET_KEY='example'
STRIPE_WEBHOOK_SECRET='example'

HELEKET_API_KEY='example'
HELEKET_SECRET_KEY='example'
Получите сертификаты (certbot):
sudo certbot --nginx -d domen.com -d www.domen.com
Соберите контейнер:
docker-compose up --build -d
Соберите статику:
docker-compose exec web python manage.py collectstatic --no-input
