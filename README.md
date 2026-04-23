# Описание проекта

## Foodgram. 
## Yandex-Practicum. Python Backend.

**Foodgram** — это онлайн‑платформа для публикации и поиска рецептов. Реализует помощь пользователям в поиске рецептов.


### Контакт
* Марков Артем Романович
* TG: @dacbhj
* Email: artem.markovma@gmail.com

### Стек
Django + DRF (REST API), React, PostgreSQL, GitHub, 


### Запуск на удаленном сервере 
**добавить на GitHub Repository secrets**
Settings->Secrets and variables->Actions
- DOCKER_PASSWORD - пароль на DockerHub
- DOCKER_USERNAME - логин на DockerHub
- HOST - IP адрес вашего сервера
- SSH_KEY - закрытый ключдля подключения к вашему серверу
- SSH_USER - логин на вашем сервере
- SSH_PASSPHRASE - пароль от сервера
- TELEGRAM_TO - id вашего Telegram

### На сервере перед развертыванием CI/CD

cd ~/foodgram/

нужно создать файл
- .env
**Пример наполнения**
SECRET_KEY=SECRET_KEY
DEBUG=False
ALLOWED_HOSTS=127.0.0.1,localhost,89.169.190.216,finalproject.ddns.net

DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=django_user
POSTGRES_PASSWORD=mysecretpassword
DB_HOST=db
DB_PORT=5432

### Загрузка данных на сервер

```
Загрузка тегов:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py load_ingredients
```
Загрузка ингредиентов:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py load_tags

### Доступы:

1. **Главная страница:** [http://finalproject.ddns.net](http://localhost)
2. **API сервер:** [http://finalproject.ddns.net/api](http://localhost/api)  
3. **Админ-панель:** [http://finalproject.ddns.net/admin](http://localhost/admin)

### Запуск проекта локально

1. **Клонируйте репозиторий:**
git clone git@github.com:johanpurdy/foodgram.git
cd foodgram

2. **Создайте и активируйте виртуальное окружение:**
python -m venv venv

# Windows:
venv\Scripts\activate

# Linux/Mac:
source venv/bin/activate

3. **Установите зависимости:**
cd backend
pip install -r requirements.txt

4. **Настройте переменные окружения:**
Создайте файл .env в папке backend/

SECRET_KEY=ваш-secret-key
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost

DB_ENGINE=django.db.backends.postgresql
DB_NAME=foodgram
POSTGRES_USER=django_user
POSTGRES_PASSWORD=mysecretpassword
DB_HOST=localhost
DB_PORT=5432

6. **Выполните миграции:**
python manage.py migrate

7. **Создайте суперпользователя:**
python manage.py createsuperuser

8. **Загрузите тестовые данные:**
python manage.py load_ingredients --path "../data/ingredients.csv"
python manage.py load_tags --path "../data/tags.json"

9. **Запустите сервер разработки:**
python manage.py runserver

