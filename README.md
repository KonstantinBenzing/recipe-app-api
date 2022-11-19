# recipe-app-api
Recipe API Project

## Commands
### Starting environment
```
docker compose up
```

### Build docker environment
use it especially after making adjustments in the Dockerfile and/or requirements files
```
docker-compose build
```

### create a new app
```
docker-compose run --rm app sh -c "python manage.py startapp core"
```

### make migrations
```
docker-compose run --rm app sh -c "python manage.py makemigrations"
```

### Migrate
```
docker-compose run --rm app sh -c "python manage.py wait_for_db && python manage.py migrate"
```

### Create superuser
```
docker-compose run --rm app sh -c "python manage.py createsuperuser"
```


### run tests
```
docker-compose run --rm app sh -c "python manage.py test"
```
### run tests including linting (flake8)
```
docker-compose run --rm app sh -c "python manage.py test  && flake8"
```

### run linting only: flake8
```
docker-compose run --rm app sh -c "flake8"
```

### gather static files
```
docker-compose run --rm app sh -c "python manage.py collectstatic"
```


## Gathered info

### API Docs
Type: Swagger
url: http://127.0.0.1:8000/api/docs/
url: http://localhost:8000/api/docs/

Testing with user:
user: user2@example.com
pw: Awesome123