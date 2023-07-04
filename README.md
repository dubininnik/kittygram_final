# Kittygram - похвастайся своим котейкой

## Использованные технологии

![Docker](https://img.shields.io/badge/Docker-2496ed?style=for-the-badge&logo=docker&logoColor=white)![Postgres](https://img.shields.io/badge/Postgres-336791?style=for-the-badge&logo=Postgresql&logoColor=white)![Python](https://img.shields.io/badge/Python-30363d?style=for-the-badge&logo=Python&logoColor=yellow)![Django](https://img.shields.io/badge/Django-103e2e?style=for-the-badge&logo=Django&logoColor=white)![NodeJS](https://img.shields.io/badge/NodeJS-404137?style=for-the-badge&logo=Node.JS&logoColor=83cd29)

## Функционал сервиса

После регистрации у вас есть возможность:

- Редактировать, добавлять, удалять, просматривать профили котов;
- Добавлять новые / присваивать существующие достижения;
- Просматривать профили чужих котов и их достижения;

## Подготовка к запуску

На сервере создайте папку проекта - kittygram и скопируйте в нее файлы docker-compose.production.yml и .env.example:

В папке с проектом переименуйте файл `.env.example` в `.env` и заполните его своими данными:

`POSTGRES_USER` - имя пользователя для базы данных

`POSTGRES_PASSWORD` - пароль для базы данных

`POSTGRES_DB` - имя базы данных

`SECRET_KEY` - секретный ключ для Django

`DEBUG` - режим отладки Django

`ALLOWED_HOSTS` - список разрешенных хостов

`DB_HOST` - имя хоста базы данных

`DB_PORT` - порт базы данных

`DOCKER_LOGIN` - логин от Docker Hub

## Запуск проекта

Находясь в папке с проектом скачайте образы и запустите проект командами:
```
sudo docker compose -f docker-compose.production.yml up -d
```

Выполните миграции, соберите статические файлы бэкенда:

```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```
```
sudo docker compose -f docker-compose.production.yml exec backend mkdir -p backend_static/static/
```
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```

Создайте суперпользователя:

```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```