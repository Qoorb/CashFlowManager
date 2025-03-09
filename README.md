# Cash Flow Manager

Cash Flow Manager - это веб-приложение для учета движения денежных средств, разработанное на Django. Приложение позволяет отслеживать доходы и расходы, классифицировать их по категориям и подкатегориям, а также контролировать финансовые потоки.

## Возможности

- Учет доходов и расходов с детализацией по категориям и подкатегориям
- Фильтрация движений средств по датам, статусам, типам, категориям и подкатегориям
- Управление статусами, типами, категориями и подкатегориями
- REST API для интеграции с другими системами
- Система уведомлений пользователя о выполненных действиях

## Технологии

- Python 3.11+
- Django 5.0+
- Django REST Framework
- SQLite (может быть заменена на PostgreSQL, MySQL и др.)
- HTML/CSS/JavaScript (Bootstrap 5)

## Структура проекта

```tree
money_flow/
│
├── cash_flow/              # Основное приложение
│   ├── migrations/         # Миграции базы данных
│   ├── templates/          # HTML-шаблоны
│   ├── admin.py            # Настройка административной панели
│   ├── api.py              # ViewSet-классы для REST API
│   ├── api_urls.py         # URL-маршруты для API
│   ├── apps.py             # Конфигурация приложения
│   ├── forms.py            # Формы для работы с данными
│   ├── models.py           # Модели данных
│   ├── serializers.py      # Сериализаторы для REST API
│   ├── tests.py            # Тесты
│   ├── urls.py             # URL-маршруты для веб-интерфейса
│   └── views.py            # Представления для веб-интерфейса
│
├── money_flow/             # Настройки проекта
│   ├── settings.py         # Настройки Django
│   ├── urls.py             # Корневые URL-маршруты
│   ├── wsgi.py             # WSGI-конфигурация
│   └── asgi.py             # ASGI-конфигурация
│
├── static/                 # Статические файлы (CSS, JS, изображения)
├── templates/              # Общие шаблоны
├── .gitignore              # Игнорируемые файлы для Git
├── db.sqlite3              # База данных SQLite
├── manage.py               # Скрипт управления Django-проектом
└── requirements.txt        # Зависимости проекта
```

## Установка и запуск

### Шаг 1: Клонирование репозитория

```bash
git clone git@github.com:Qoorb/CashFlowManager.git
cd cash_flow_manager
```

### Шаг 2: Создание виртуального окружения и установка зависимостей

```bash
python -m venv .venv
source .venv/bin/activate  # На Linux/Mac
# или
.\.venv\Scripts\activate  # На Windows

pip install -r requirements.txt
```

### Шаг 3: Настройка базы данных

```bash
python manage.py migrate
```

### Шаг 4: Создание администратора (опционально)

```bash
python manage.py createsuperuser
```

### Шаг 5: Запуск сервера разработки

```bash
python manage.py runserver
```

После этого приложение будет доступно по адресу <http://127.0.0.1:8000/>.

## API-документация

### Доступные эндпоинты

- `/api/statuses/` - CRUD для статусов
- `/api/types/` - CRUD для типов
- `/api/categories/` - CRUD для категорий
- `/api/subcategories/` - CRUD для подкатегорий
- `/api/cashflows/` - CRUD для движений денежных средств

### Примеры использования API

#### Получение списка всех движений средств

```shell
GET /api/cashflows/
```

#### Фильтрация движений средств

```shell
GET /api/cashflows/?status=1&type=2&category=3&date_created=2023-01-01
```

#### Создание нового движения средств

```shell
POST /api/cashflows/
{
    "date_created": "2023-01-01",
    "status": 1,
    "type": 2,
    "category": 3,
    "subcategory": 4,
    "amount": 1000.00,
    "comment": "Зарплата"
}
```
