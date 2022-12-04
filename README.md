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

## DEPLOYMENT

### start server
```
docker-compose -f docker-compose-deploy.yml down --volumes
docker-compose -f docker-compose-deploy.yml up
```

### keys example for AWS
```
ssh-keygen -t rsa -b 4096
/Users/.../.ssh/aws_id_rsa
<passphrase>
cat ~/.ssh/aws_id_rsa.pub
```
copy the content and add as key to server

### connect with key to running server instance
```
ssh-add ~/.ssh/aws_id_rsa
<passphrase>
ssh <user>@<ip>
[yes]
```
-> connected! cli shows [...]$

### create key on server
```
ssh-keygen -t ed25519 -b 4096
```
accept location and skip passphrase (if not needed)
```
cat ~/.ssh/id_ed25519.pub
```
copy the key
go to
- Github
- project
- Deploy keys

-> add deploy key from server


## Local deployment
remove all existing instances from local development environment
```
docker-compose -f docker-compose-deploy.yml down --volumes
```
start fresh instance
```
docker-compose -f docker-compose-deploy.yml build
docker-compose -f docker-compose-deploy.yml up
```


## Run commands on server
```
docker-compose -f docker-compose-deploy.yml run --rm app sh -c "python manage.py <command>"
```