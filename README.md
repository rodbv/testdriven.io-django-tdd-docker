# Sample Django API using Django-Rest-Framework and Postgres.

## Running the application

While you can run the application from your local environment, the application has a [Dockerfile](app/Dockerfile) is prepared to run inside Docker containers, to simplify development and testing.

To run it, simply execute from the `movies` directory

```bash
docker-compose up
```

Once the services are up and running you can execute the usual Django commands as such:

```
> docker-compose exec movies python manage.py makemigrations
> docker-compose exec movies python manage.py migrate
> docker-compose exec movies python manage.py createsuperuser
```

To run the tests, type

```bash
docker-compose exec movies pytest
```

...where "movies" is the main application service (check [docker-compose.yml](./docker-compose.yml))

## API

The API made available by the app is

| HTTP Method | CRUD Method | Result             |
| ----------- | ----------- | ------------------ |
| GET         | READ        | get all movies     |
| GET         | READ        | get a single movie |
| POST        | CREATE      | add a movie        |
