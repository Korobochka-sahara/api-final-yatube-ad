# API для Yatube

## Описание проекта

API для социальной сети Yatube — платформы для публикации записей, комментирования постов и подписки на авторов.

Проект предоставляет REST API, позволяющий:
- получать список публикаций и просматривать отдельные записи;
- создавать, редактировать и удалять собственные публикации;
- получать информацию о сообществах;
- оставлять комментарии к публикациям;
- редактировать и удалять собственные комментарии;
- подписываться на других пользователей и просматривать свои подписки.

Для аутентификации используется JWT. Права доступа разграничиваются в зависимости от того, авторизован ли пользователь и является ли он автором публикации или комментария.

## Технологии

- Python 3.10
- Django
- Django REST Framework
- Djoser
- Simple JWT
- SQLite
- Pytest

## Установка и запуск

1. Клонируйте репозиторий:

   ```bash
   git clone https://github.com/Korobochka-sahara/api-final-yatube-ad.git
   ```

2. Перейдите в директорию проекта:

   ```bash
   cd api-final-yatube-ad
   ```

3. Создайте виртуальное окружение:

   ```bash
   python -m venv venv
   ```

4. Активируйте виртуальное окружение.

   Windows:

   ```bash
   source venv/Scripts/activate
   ```

   Linux/macOS:

   ```bash
   source venv/bin/activate
   ```

5. Установите зависимости:

   ```bash
   pip install -r requirements.txt
   ```

6. Выполните миграции:

   ```bash
   python manage.py migrate
   ```

7. Запустите сервер:

   ```bash
   python manage.py runserver
   ```

API будет доступно по адресу:

`http://127.0.0.1:8000/`

Документация API:

`http://127.0.0.1:8000/redoc/`

## Примеры запросов

### Получение списка публикаций

```http
GET /api/v1/posts/
```

### Создание публикации

```http
POST /api/v1/posts/
Authorization: Bearer <JWT-токен>
Content-Type: application/json
```

```json
{
    "text": "Моя первая публикация через API",
    "group": 1
}
```

### Получение комментариев к публикации

```http
GET /api/v1/posts/1/comments/
```

### Подписка на пользователя

```http
POST /api/v1/follow/
Authorization: Bearer <JWT-токен>
Content-Type: application/json
```

```json
{
    "following": "username"
}
```

## Аутентификация

Для получения JWT-токена необходимо отправить POST-запрос:

`/api/v1/jwt/create/`

После получения токена его следует передавать в заголовке запросов:

```http
Authorization: Bearer <JWT-токен>
```

## Автор

[Korobochka-sahara](https://github.com/Korobochka-sahara)