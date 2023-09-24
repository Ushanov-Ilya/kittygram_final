# kittygram_final

![CI workflow result](https://github.com/Ushanov-Ilya/kittygram_final/actions/workflows/main.yml/badge.svg)
Файл стоит оформить следующим образом:
1. приложить бейдж со статусом пайплайна
3. инструкция по разворачиванию

## Описание
Сервис kittygram, представляющий из себя социальную сеть для того, чтобы делиться котиками и их достижениями с другими пользователями. Есть система регистрации.

## Инструкция по разворачиванию
1. Склонируйте репозиторий с помощью git clone https://github.com/Ushanov-Ilya/infra_sprint1.git
2. Измените файл конфигурации nginx /etc/nginx/sites-enabled/default на пример из /infra/default
3. Создайте файл конфигурации gunicorn /etc/systemd/system/gunicorn.service по примеру из /infra/gunicorn_kittygram.service, исправив доменное имя на свое
4. Создайте и заполните виртуальное оуружение:
- `python3 -m venv venv`
- `source venv/bin/activate`
- `pip install -r requirements.txt`
- `pip install gunicorn==20.1.0`
5. Создайте файл .env со следующими ключами:
- SECRET_KEY - секретный ключ джанго
- DEBUG - режим разработки True/False
- ALLOWED_HOSTS - список разрешенных хостов через пробел
- POSTGRES_USER - пользователь бд
- POSTGRES_PASSWORD - пароль пользователя бд
- POSTGRES_DB - имя бд
- DB_HOST - название сервиса базы данных(db)
- DB_PORT - порт базы данных(5432)
6. Запустите gunicorn service:
- `sudo systemctl restart gunicorn`
7. Соберите статику фронтенда:
- `npm run build`
И перенесите статику в папку /var/www/kittygram/
8. Соберите статику бекэнда:
- `python manage.py collectstatic`
И перенесите статику в папку /var/www/kittygram/
9. Перезапустите nginx:
- `sudo nginx -t`
- `sudo systemctl reload nginx`

## Автор
Ушанов Илья
https://github.com/Ushanov-Ilya
