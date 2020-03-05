# Ergonode development docker

This is only a development solution! Do not use it on production environments!

## How the hell should I install it all ?!

At first you must install Docker and Docker Compose (https://docs.docker.com/compose).

Next, you must clone frontend and backend and docs repositories to ergonode directory:

```bash
mkdir ergonode
cd ergonode
git clone git@github.com:ergonode/docker.git
git clone git@github.com:ergonode/frontend.git
git clone git@github.com:ergonode/backend.git
git clone git@github.com:ergonode/docs.git
```

Next, you will need to enter docker directory and copy ``.env.dist``

```bash
cd docker
cp .env.dist .env
```

If you want to test ergonode in multiple directories you need to change in the  `.env` file
COMPOSE_PROJECT_NAME env var to some unique value

Now you can start start docker by simple command

```bash
docker-compose up
```

Now you can fill  app database with basic data by using command
```
docker-compose exec php bin/phing database:fixture
```

Or fill database with development data with command
```
docker-compose exec php bin/phing database:fixture:dev
```

Enjoy :)

## Ok, but what now?


If you want to view frontend panel just type address from below into your browser

```
http://localhost
```

And to test app you can login as `test@ergonode.com` with password `abcd1234`

If you want to view backend API doc just type address from below into your browser

```
http://localhost:8000/api/doc
```

## What can i do with this creature?

To run all tests execute 
```
docker-compose exec php bin/phing test
```

To run symfony console 
``` 
docker-compose exec php bin/console
```

To add new users you can use command 
```
docker-compose exec php bin/console ergonode:user:create  <email> <first_name> <last_name> <password> <language> [<role>]
```

If you want to enter some container

```bash
docker-compose exec php bash
docker-compose exec postgres bash
docker-compose exec node bash
```

