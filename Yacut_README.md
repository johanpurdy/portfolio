# Yacut — сервис укорачивания ссылок

**Yacut** — это веб-приложение на Flask, которое позволяет создавать короткие ссылки для длинных URL-адресов. Проект также поддерживает загрузку файлов на Яндекс.Диск с генерацией коротких ссылок для скачивания.

### Возможности

- Создание коротких ссылок для длинных URL
- Возможность указать свой вариант короткой ссылки
- Проверка уникальности коротких идентификаторов
- Загрузка файлов на Яндекс.Диск
- Получение коротких ссылок для загруженных файлов
- REST API для работы с ссылками
- Хранение данных в базе данных SQLite

### Технологии

- **Python 3.9+**
- **Flask** — веб-фреймворк
- **Flask-SQLAlchemy** — работа с базой данных
- **Flask-Migrate** — миграции базы данных
- **Flask-WTF / WTForms** — обработка форм
- **aiohttp** — асинхронные запросы к API Яндекс.Диска
- **Jinja2** — шаблонизатор
- **SQLite** — база данных (по умолчанию)

## Установка и запуск


Клонировать репозиторий и перейти в него в командной строке:

```
git clone 
```

```
cd yacut
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```

* Если у вас Linux/macOS

    ```
    source venv/bin/activate
    ```

* Если у вас windows

    ```
    source venv/scripts/activate
    ```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Создать в директории проекта файл .env с четыремя переменными окружения:

```
FLASK_APP=yacut
FLASK_ENV=development
SECRET_KEY=your-secret-key-here
DATABASE_URL=sqlite:///db.sqlite3

# Интеграция с Яндекс.Диском (опционально)
AUTH_HEADERS={"Authorization": "OAuth your-yandex-oauth-token"}
REQUEST_UPLOAD_URL=https://cloud-api.yandex.net
DOWNLOAD_LINK_URL=https://cloud-api.yandex.net
```

Создать базу данных и применить миграции:

```
flask db upgrade
```

Запустить проект:

```
flask run
```

*Приложение будет доступно по адресу: http://localhost:5000 (italic)*

## Использование

### Веб-интерфейс

#### Главная страница (укорачивание ссылок)

* Перейдите на ```http://localhost:5000```

* Введите длинную ссылку

* При желании укажите свой вариант короткой ссылки (до 16 символов, буквы и цифры)

* Нажмите "Создать"

#### Страница загрузки файлов

* Перейдите на ```http://localhost:5000/files```

* Выберите один или несколько файлов для загрузки

* Нажмите "Создать"

```Для каждого файла будет создана короткая ссылка вида http://localhost:5000/abc123```

## API

### Создание короткой ссылки

#### Запрос:

```**POST /api/id/**```

```python
{
    "url": "https://example.com/very-long-url-path",
    "custom_id": "example"  // опционально
}
```
#### Успешный ответ (201 Created):

```python
{
    "url": "https://example.com/very-long-url-path",
    "short_link": "http://localhost:5000/example"
}
```
### Получение оригинальной ссылки

#### Запрос:

```**GET /api/id/<string:example>/**```

#### Ответ:

```python
{
    "url": "https://example.com/very-long-url-path"
}
```

# Автор

## Марков Артем 

* GitHub: [@johanpurdy](https://github.com/johanpurdy)
* Telegram: @dacbhj
