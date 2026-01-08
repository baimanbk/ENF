🛍 ERD — Интернет-магазин одежды
Django + HTMX + Alpine.js
Современный интернет-магазин одежды с серверным рендерингом, динамическими интерфейсами и интеграцией платежей.
🚀 Технологии
Backend: Django
Frontend: HTMX, Alpine.js
База данных: PostgreSQL
Платежи: Stripe
Инфраструктура: Docker, Nginx, SSL (Certbot)
📦 Запуск проекта
1. Локальный запуск (без Docker)
1️⃣ Клонируйте репозиторий
git clone <repo_url>
cd erd
2️⃣ Создайте и активируйте виртуальное окружение
python -m venv venv
source venv/bin/activate   # Linux / Mac
venv\Scripts\activate      # Windows
3️⃣ Установите зависимости
python -m pip install -r requirements.txt
4️⃣ Настройте переменные окружения
Создайте файл .env в корне проекта и заполните его (пример ниже).
5️⃣ Выполните миграции
python manage.py migrate
6️⃣ Создайте суперпользователя
python manage.py createsuperuser
7️⃣ Запустите сервер
python manage.py runserver
Приложение будет доступно по адресу:
👉 http://127.0.0.1:8000
2. Запуск на сервере (Docker + SSL)
1️⃣ Подготовьте домен
Укажите DNS-запись domen.com и www.domen.com на IP вашего сервера
2️⃣ Настройте .env
SECRET_KEY=example

POSTGRES_DB=enfdb
POSTGRES_USER=enfdb
POSTGRES_PASSWORD=enfdb
POSTGRES_HOST=localhost
POSTGRES_PORT=5432

STRIPE_SECRET_KEY=example
STRIPE_WEBHOOK_SECRET=example

HELEKET_API_KEY=example
HELEKET_SECRET_KEY=example
3️⃣ Получите SSL-сертификаты (Certbot)
sudo certbot --nginx -d domen.com -d www.domen.com
4️⃣ Запустите контейнеры
docker-compose up --build -d
5️⃣ Соберите статику
docker-compose exec web python manage.py collectstatic --no-input

docker-compose up --build -d
Соберите статику:
docker-compose exec web python manage.py collectstatic --no-input
