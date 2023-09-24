# kittygram_final

![CI workflow result](https://github.com/Ushanov-Ilya/kittygram_final/actions/workflows/main.yml/badge.svg)

## Описание
Сервис kittygram, представляющий из себя социальную сеть для того, чтобы делиться котиками и их достижениями с другими пользователями. Есть система регистрации.

## Инструкция по разворачиванию
1. Зайдите на сервер, где будете разворачивать проект
2. Склонируйте репозиторий 
```
git clone https://github.com/Ushanov-Ilya/kittygram_final.git
```
3. Настройте nginx на сервере в следующем формате:
```
server {
    ...
    server_name <ip> <домен>;

    location / {
        proxy_set_header Host $http_host;
        proxy_pass http://127.0.0.1:8000;
    }
    ...
}
```
4. Создайте папку kittygram
5. Создайте файл в ней .env со следующими ключами:
- SECRET_KEY - секретный ключ джанго
- DEBUG - режим разработки True/False
- ALLOWED_HOSTS - список разрешенных хостов через пробел
- POSTGRES_USER - пользователь бд
- POSTGRES_PASSWORD - пароль пользователя бд
- POSTGRES_DB - имя бд
- DB_HOST - название сервиса базы данных(db)
- DB_PORT - порт базы данных(5432)
6. Добавьте изменения в проект, создайте коммит и push, все остальное сделает github workflow

## Автор
Ушанов Илья
https://github.com/Ushanov-Ilya
