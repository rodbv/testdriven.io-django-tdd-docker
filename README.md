# Sample Django API using Django-Rest-Framework and Postgres.

## Running the application

While you can run the application from your local environment, the application has a [Dockerfile](app/Dockerfile) is prepared to run inside Docker containers, to simplify development and testing.

To run it, simply execute from the `movies` directory

```bash
docker-compose up
```

Once the services are up and running you can execute the usual Django commands inside the containers as such:

```
> docker-compose exec movies python manage.py makemigrations
> docker-compose exec movies python manage.py migrate
> docker-compose exec movies python manage.py createsuperuser
```

## Heroku deployment

This application has been deployed on Heroku (via Gitlab CI) and is accessible at (https://morning-river-10989.herokuapp.com)[https://morning-river-10989.herokuapp.com]

## Running the tests

To run the tests, type

```bash
docker-compose exec movies pytest
```

Where "movies" is the main application service (check [docker-compose.yml](./docker-compose.yml)).

PyTest-watch is also supported with the `ptw` command.

Other useful pytest commands:

```
# normal run
docker-compose exec movies pytest

# disable warnings
docker-compose exec movies pytest -p no:warnings

# run only the last failed tests
docker-compose exec movies pytest --lf

# run only the tests with names that match the string expression
docker-compose exec movies pytest -k "movie and not all_movies"

# stop the test session after the first failure
docker-compose exec movies pytest -x

# enter PDB after first failure then end the test session
docker-compose exec movies pytest -x --pdb

# stop the test run after two failures
docker-compose exec movies pytest --maxfail=2

# show local variables in tracebacks
docker-compose exec movies pytest -l

# list the 2 slowest tests
docker-compose exec movies pytest --durations=2
```

## API

The API made available by the app is

| HTTP Method | CRUD Method | Result             |
| ----------- | ----------- | ------------------ |
| GET         | READ        | get all movies     |
| GET         | READ        | get a single movie |
| POST        | CREATE      | add a movie        |

## Seeding the database with file movies.json

```
docker-compose exec movies python manage.py flush
docker-compose exec movies python manage.py loaddata movies.json
```
