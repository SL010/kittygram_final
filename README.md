### Проект Kittygram
Kittygram - это социальная сеть, специально созданная для размещения фотографий своих питомцев.

# Как развернуть проект в docker контейнерах:
-Скачайте docker-compose.yml из репозитория https://github.com/SL010/kittygram_final/docker-compose.yml
-Создайте файл .env 
-Наполните созданный файл переменными окружения
  POSTGRES_DB=<БазаДанных>
  POSTGRES_USER=<имя пользователя>
  POSTGRES_PASSWORD=<пароль>
  DB_NAME=<имя БазыДанных>
  DB_HOST=db
  DB_PORT=5432
  SECRET_KEY=<ключ Django>
  DEBUG=<DEBUG True/False>
  ALLOWED_HOSTS=<разрешенные хосты>
-Запустите Docker-compose (в директории с файлом docker-compose):
$sudo docker compose -f docker-compose.yml pull
$sudo docker compose -f docker-compose.yml down
$sudo docker compose -f docker-compose.yml up -d
-Сделайте миграции и соберите статику
$sudo docker compose -f docker-compose.yml exec backend python manage.py migrate
$sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
$sudo docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/ 

### Настройка CI/CD с помощью GitHub Actions (конфигурационный файл main.yml в директории .github/workflows)
Добавьте перменные в Secrets в github:
  DOCKER_PASSWORD - пароль от Docker Hub
  DOCKER_USERNAME - имя пользователя Docker Hub
  HOST - ip сервера
  SSH_KEY - ключ ssh для доступа к удаленному серверу
  SSH_PASSPHRASE - пароль ssh
  TELEGRAM_TO - id пользователя TELEGRAM
  TELEGRAM_TOKEN - TELEGRAM токен
  USER - имя пользователя сервера

### Стэк:
Backend: Django, DRF, Gunicorn, Pillow, Подробней в requirements.txt

Сервер: nginx

Деплой Docker Docker compose

Автор: Борисов Вячеслав 
https://github.com/SL010

