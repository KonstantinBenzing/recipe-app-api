# recipe-app-api
Recipe API Project


## Build docker environment
```
docker-compose build
```

## create a new app
```
docker-compose run --rm app sh -c "python manage.py startapp core"
```

## make migrations
```
docker-compose run --rm app sh -c "python manage.py makemigrations"
```

## Migrate
```
docker-compose run --rm app sh -c "python manage.py wait_for_db && python manage.py migrate"
```



## run tests
```
docker-compose run --rm app sh -c "python manage.py test"
```
## run tests including linting (flake8)
```
docker-compose run --rm app sh -c "python manage.py test  && flake8"
```