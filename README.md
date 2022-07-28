# Задача

***

Необходимо разработать сервис управления рассылками API администрирования и получения статистики.

***

## Описание
- Необходимо реализовать методы создания новой рассылки, просмотра созданных и получения статистики по выполненным рассылкам;
- Реализовать сам сервис отправки уведомлений на внешнее API;
- добавления нового клиента в справочник со всеми его атрибутами;
- обновления данных атрибутов клиента;
- удаления клиента из справочника;
- добавления новой рассылки со всеми её атрибутами;
- получения общей статистики по созданным рассылкам и количеству отправленных сообщений по ним с группировкой по статусам;
- получения детальной статистики отправленных сообщений по конкретной рассылке;
- обновления атрибутов рассылки;
- удаления рассылки;
- обработки активных рассылок и отправки сообщений клиентам.

## Дополнительные задания

<p>Опциональные пункты, выполнение любого количества из приведённого списка повышают ваши шансы на положительное решение о приёме</p>
<ol>
<li>1.организовать тестирование написанного кода</li>
<li>3.подготовить docker-compose для запуска всех сервисов проекта одной командой</li>
<li>5.сделать так, чтобы по адресу /docs/ открывалась страница со drf_yasg UI и в нём отображалось описание разработанного API.</li>
<li>6.реализовать администраторский Web UI для управления рассылками и получения статистики по отправленным сообщениям</li>
</ol>

***

## Запуск проекта
Использовал Python 3.10 и Django 3.2.12
### Склонировать репозиторий:
```
git clone https://github.com/vadushkin/notification_api_service.git
```
### Перейти в директорию:
```
cd notification_api_service
```
### Создать виртуальную среду
```
python -m venv venv
```
### Перейти в виртуальную среду
```
venv\Scripts\activate
```
### Установить все зависимости
```
pip install -r requirements.txt
```
### Выполнить миграции:
```
python manage.py migrate
```
### Запуск сервера
```
python manage.py runserver
```

Документация будет доступа по ссылке 

```
http://127.0.0.1:8000/docs/ 
```

или 

```
http://127.0.0.1:8000/redoc/
```

Если вы хотите увидеть милого шарика, то вам сюда:

```
http://127.0.0.1:8000/
```
***
```http://localhost:8000/v1/``` - api проекта

```http://localhost:8000/v1/clients/``` - клиенты

```http://localhost:8000/v1/mailings/``` - рассылки

```http:/localhost:8000/v1/messages/``` - сообщения

```http://localhost:8000/v1/tags/``` - теги

```http://localhost:8000/docs/``` - docs проекта
***

## Запуск через Docker
### В файле .env и заполните переменные окружения:
```
SECRET_KEY=Ключ джанго
ALLOWED_HOSTS=127.0.0.1
DEBUG=Значение (True|False)

API_TOKEN=Ваш токен

DB_ENGINE=(django.db.backends.postgresql|api - для использования логов с sqlзапросами)
DB_NAME=<имя базы данных postgres>
POSTGRES_USER=<имя пользователя>
POSTGRES_PASSWORD=<пароль для базы данных>
DB_HOST=db
DB_PORT=5432
```
### Собрать docker-compose:
```
Для использования dockera, в файле settings, разкомментировать блок
# PostgreSQL
# ...

Для подключения БД PostgreSQL

и удалить блок
# SQLite3
# ...
```
Собрать образ и запустить
```
docker-compose up -d --build
```
### После успешной сборки на сервере выполните команды:
#### Выполните миграции:
```
docker-compose exec web python manage.py migrate --noinput
```
#### Создать суперпользователя Django:
```
docker-compose exec web python manage.py createsuperuser
```

Вдохновился идеей реализации и изменения кода у пользователя 'imersir'
