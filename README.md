# kittygram_final - Контейнеры и CI/CD для проектов Kittygram и Taski

[![CI](https://github.com/soloviev-andrey/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/soloviev-andrey/kittygram_final/actions/workflows/main.yml)


## Описание
Kittygram - это вдохновляющая платформа для котиколюбителей, где вы можете делиться фотографиями ваших пушистых друзей.

Taski - это инновационное приложение для управления задачами. Организуйте свою работу и повысьте эффективность вашей команды с Taski.

## Что было сделано?
В рамках этого проекта было выполнено следующее:
- Разработана веб-платформа Kittygram для обмена фотографиями котиков.
- Создан Docker-контейнер для бэкенд-части проекта Kittygram.
- Настроен Nginx-сервер для проксирования запросов к разным частям проекта Kittygram.
- Разработан Docker-контейнер для фронтенд-части Kittygram.
- Произведена интеграция с базой данных PostgreSQL.
- Развернут проект Taski на сервере.
- Создан Docker-контейнер для бэкенд-части проекта Taski.
- Разработан Docker-контейнер для фронтенд-части Taski.
- Произведена интеграция с базой данных PostgreSQL.
- Оба проекта были настроены с использованием Docker и автоматизированы с помощью GitHub Actions.

## Использованные технологии
Проект был реализован с использованием следующих технологий:
- Django и Django REST framework для бэкенд-части Kittygram и Taski.
- React.js для фронтенд-части Kittygram и Taski.
- Docker для контейнеризации приложений.
- PostgreSQL для хранения данных.
- Nginx для обеспечения балансировки и проксирования запросов.
- GitHub Actions для настройки непрерывной интеграции и доставки.

## Проверка работоспособности
Вы можете проверить работу Kittygram и Taski, перейдя по следующим ссылкам:
- Kittygram: [https://kittygramsolo.ddns.net/](https://kittygramsolo.ddns.net/)
- Taski: [https://yphost.sytes.net/](https://yphost.sytes.net/)

## Автор
Андрей Соловьев

## Как запустить проект:
1. Клонировать репозиторий и перейти в него в командной строке:
```bash
git clone git@github.com:soloviev-andrey/kittygram_final.git
cd kittygram_final
```
2. Создать файл .env для хранения ключей:
```bash
SECRET_KEY='указать секретный ключ'
ALLOWED_HOSTS='указать имя или IP хоста'
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432
DEBUG=False
```
3. Запустить docker-compose.production:
```bash
docker compose \-f docker\-compose\.production\.yml up
```
4. Выполнить миграции, сбор статики:
```bash
docker compose \-f docker\-compose\.production\.yml exec backend python manage\.py migrate
docker compose \-f docker\-compose\.production\.yml exec backend python manage\.py collectstatic
docker compose \-f docker\-compose\.production\.yml exec backend cp \-r /app/collected\_static/\. /static/static/
```
5. Создать суперпользователя, ввести почту, логин, пароль:
```bash
docker compose \-f docker\-compose\.production\.yml exec backend python manage\.py createsuperuser
```