## How start project?

1. clone repo

        git clone https://gitlab.informatics.ru/2019-2020/online/s101/meta-social.git
        cd meta-social
        python3 -m venv venv
        source venv/bin/activate
        pip install -r requirements.txt

2. db migrations

        cd meta_social
        python manage.py makemigrations
        python manage.py migrate
        python manage.py loaddata allauth.json

3. Start project

    #### with docker:

        docker-compose up --build
    
    #### without docker:

        python manage.py runserver
        celery -A meta_social worker -l info


# For chat

## start with Docker
    docker-compose up --build

## Starl local
    CHANNEL_LAYERS = {
    'default': {
        'BACKEND': 'channels_redis.core.RedisChannelLayer',
        'CONFIG': {
            "hosts": [('redis', 6379)], Change for "hosts": [('127.0.0.1', 6379)],
            },
        },
    }

## Install redis
    Arch: sudo pacman -S redis
    Fedora: sudo dnf install redis
    Debian: sudo apt install redis

## Start redis
    Linux: redis-server
    Docker: docker run -p 6379:6379 -d redis:5

## Check redis
    redis-cli ping
